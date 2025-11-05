---
title: Information on Vendoring
description: Describing the importance of vendoring and how to do it for common builds
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---
# What is vendoring
Vendoring is a practice of generating/installing dependencies required for a package to be compiled and installed. This can be done by packaging the software and calling on it through the BuildRequires: tag or by archiving the vendors and extracting them during the build process.
## The purpose of vendoring
As described in the ABF entry, the ABF works in an airgapped environment. When a project is vendored, it allows the project to be built without any external internet connection. Cargo and Go are the most common default online compilers with mostly easy to use built in vendoring capability.
### Vendoring standard project
Vendoring these projects requires packaging the needed dependencies and uploading them to the build environment. In cases like om-welcome the spec file has the line below. 
```
BuildRequires:	make
BuildRequires:	gettext
```
In order to build the om-welcome package, both make and gettext must be packaged/vendored. Without the gettext package the build will fail as show below.
```
+ /usr/bin/make install DESTDIR=/home/omv/abf/om-welcome/BUILD/om-welcome-2.9.19-build/BUILDROOT 'INSTALL=/usr/bin/install -p'
xgettext -d om-welcome -o usr/share/om-welcome/om-welcome.pot -L Shell --from-code utf-8 usr/share/om-welcome/translation
make: xgettext: No such file or directory
make: *** [Makefile:12: messages] Error 127
error: Bad exit status from /var/tmp/rpm-tmp.k0oBH7 (%install)
```
These errors in the build and install phases are not always straight forward but usually there will be an error of no such file or directory. 
### Vendoring cargo projects
Cargo has a built in vendoring utility. Running ```cargo vendor``` in the root of a rust project will start the download process to the vendor folder and return the following below.   
```
To use vendored sources, add this to your .cargo/config.toml for this project:

[source.crates-io]
replace-with = "vendored-sources"

[source.vendored-sources]
directory = "vendor"
```
Once the command is finished the vendor folder will need to be archived and added as a source to the spec file. Once the source is added the .cargo/config.toml file will need to be modified with the above output. Below is an spec file for swww that shows the source being added as Source1 and the modification of the .toml file. In some cases cargo will return a different output for the config.toml. It is important to modify the config.toml as the cargo package manager says.
```
%global debug_package %{nil}

Name:		swww
Version:	0.11.2
Release:	1
URL:		https://github.com/LGFae/swww
Source0:	%{url}/archive/v%{version}/%{name}-%{version}.tar.gz
Source1:    	swww-%{version}-vendor.tar.gz
Summary:	A Solution to your Wayland Wallpaper Woes
License:	GPL-3.0
Group:		Wayland/Utils

BuildRequires:	cargo
BuildRequires: scdoc
BuildRequires: pkgconfig(liblz4)
BuildRequires: pkgconfig(wayland-protocols)
BuildRequires: pkgconfig(wayland-client)
BuildRequires: pkgconfig(dav1d)

%description
%summary

%prep
%autosetup -n %{name}-%{version} -a1
tar -zxf %{SOURCE1}
mkdir -p .cargo
cat >> .cargo/config.toml << EOF
[source.crates-io]
replace-with = "vendored-sources"

[source.vendored-sources]
directory = "vendor"
EOF

%build
cargo build --release --offline --frozen --all-features
./doc/gen.sh

%install
install -Dpm755 target/release/swww %{buildroot}%{_bindir}/swww
install -Dpm755 target/release/swww-daemon %{buildroot}%{_bindir}/swww-daemon
install -Dpm644 ./doc/generated/*.1 -t %{buildroot}%{_mandir}/man1
install -Dpm644 completions/_swww %{buildroot}/%{_datadir}/zsh-completions/completions/%{name}
install -Dpm644 completions/swww.bash %{buildroot}/%{_datadir}/bash-completions/completions/%{name}
install -Dpm644 completions/swww.fish %{buildroot}/%{_datadir}/fish-completions/completions/%{name}.fish

%files
%license LICENSE
%doc README.md
%{_bindir}/swww
%{_bindir}/swww-daemon
%{_mandir}/man1/swww*.1.*
%{_datadir}/zsh-completions/completions/%{name}
%{_datadir}/fish-completions/completions/%{name}.fish
%{_datadir}/bash-completions/completions/%{name}
```
### Vendoring go
Go has a builtin vendoring utility. Running ```go mod vendor``` will start the download of dependencies to the vendor folder in the root of the go project folder. Once the download is complete the vendor folder will need to be archived and added as a source to be extracted in a similar way to cargo. Unlike cargo, go does not need any files to be modified to be used. In some cases the repositories containing the depedencies may be private or archived in a way that is not accessible. Using ```export GOPROXY=https://proxy.golang.org,direct``` before running ```go mod vendor``` should allow those dependencies to be downloaded. When this is required please include the export command as a comment in the spec file for other users.
### Vendoring nodejs using pnpm
Nodejs vendoring is strange and very not straight forward. Below is a script used to package hyprpanel and aylurs-gtk-shell. Changing the (folder) to the folder of the software extracted from the source tarball. Once this script is ran from the directory above the source folder the output will be named pnpm-offline-cache.tar.gz. This archive will need to be extracted during the %prep phase. In rare cases nodejs will use symlinks which will need to be manually copied like the situation in [hyprpanel](https://github.com/OpenMandrivaAssociation/hyprpanel/blob/master/hyprpanel.spec).
```
#!/usr/bin/env bash
set -euo pipefail

# Change folder to correct name
cd (folder)

cat > .npmrc <<'EOF'
node-linker=hoisted
store-dir=.pnpm-store
cache-dir=.pnpm-cache
virtual-store-dir=.pnpm
EOF

pnpm install --lockfile-only
pnpm fetch
pnpm install --offline --frozen-lockfile

ARCHIVE_NAME="pnpm-offline-cache.tar.gz"
tar --mtime='2025-01-01' \
    --owner=0 --group=0 --numeric-owner \
    -czf "../$ARCHIVE_NAME" \
    package.json \
    pnpm-lock.yaml \
    .npmrc \
    .pnpm-store \
    .pnpm-cache \
    .pnpm \
    node_modules

echo "Archive created: ../$ARCHIVE_NAME"
echo "Size: $(du -h ../$ARCHIVE_NAME | cut -f1)"
```
