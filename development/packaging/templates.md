---
title: Templates
description: Templates of spec files
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---
# Generating templates
When creating a new project there are several ways to generate a spec file pre filled. Check the man vs page for more information on the utility

## VS
```
Name:           foo
Version:
Release:        1
Source0:        https://github.com/foo/foo/archive/%{version}/%{name}-%{version}.tar.gz
Summary:
URL:            https://github.com/foo/foo
License:        GPL
Group:
BuildRequires:  cmake
BuildSystem:    cmake

%description

%prep
%autosetup -p1

%files
```
## VL
```
%define major 0
%define libname %mklibname foo
%define devname %mklibname foo -d

Name:           foo
Version:
Release:        1
Source0:        https://github.com/foo/foo/archive/%{version}/%{name}-%{version}.tar.gz
Summary:
URL:            https://github.com/foo/foo
License:        GPL
Group:          System/Libraries
BuildRequires:  cmake
BuildSystem:    cmake

%description

%package -n %{libname}
Summary:
Group:          System/Libraries

%description -n %{libname}

%package -n %{devname}
Summary:        Development files for %{name}
Group:          Development/C
Requires:       %{libname} = %{EVRD}

%description -n %{devname}
Development files (Headers etc.) for %{name}.

%prep
%autosetup -p1

%files
%{_bindir}/*

%files -n %{libname}
%{_libdir}/*.so.%{major}*

%files -n %{devname}
%{_includedir}/*
%{_libdir}/*.so
%{_libdir}/pkgconfig/*
%{_libdir}/cmake/*
```
## VP
```
Name:           python-foo
Version:        .1
Release:        1
Source0:        https://files.pythonhosted.org/packages/source/f/foo/foo-%{version}.tar.gz
Summary:        UNKNOWN
URL:            https://pypi.org/project/foo/
License:        UNKNOWN
Group:          Development/Python
BuildRequires:  python
BuildSystem:    python
BuildArch:      noarch

%description
UNKNOWN

%files
%{py_sitedir}/foo
%{py_sitedir}/foo-*.*-info
```
## VPL
```
%define module foo
%undefine _debugsource_packages

Name:           perl-%{module}
Version:
Release:        1
Summary:
URL:            https://metacpan.org/pod/foo
Source:         https://cpan.org/modules/by-module/foo/%{module}-%{version}.tar.gz
License:        Perl (Artistic or GPL)
Group:          Development/Perl
BuildRequires:  perl
BuildArch:      noarch

%description

%prep
%autosetup -p1 -n %{module}-%{version}
perl Makefile.PL INSTALLDIRS=vendor

%build
%make_build

%check
make test

%install
%make_install INSTALLDIRS=vendor

%files
%doc Changes MANIFEST README
%{perl_vendorlib}/*/*
%{_mandir}/man3/*.3pm*
```
## VJ
```
Name: foo
Version:
Release: 1
Summary:
URL: http://foo.sf.net/
Source: %{name}-%{version}.tar.bz2
License: ASF 2.0
Group: Libraries/Java
BuildRequires: jdk-current
BuildArch: noarch

%description

%package        javadoc
Summary:        Javadoc for %{name}
Group:          Libraries/Java
Requires: %{name} = %{version}-%{release}

%description    javadoc
Javadoc for %{name}.

%prep
%autosetup -p1

%build
. %{_sysconfdir}/profile.d/90java.sh
ant dist

%install
mkdir -p %{buildroot}%{_javadir}
install -c -m 644 *.jar %{buildroot}%{_javadir}
install -d -m 755 %{buildroot}%{_javadocdir}/%{name}-%{version}
cp -pr docs/api/* %{buildroot}%{_javadocdir}/%{name}-%{version}

%files
%{_javadir}/*

%files javadoc
%{_javadocdir}/%{name}-%{version}
```
## VO
```
%global octpkg foo

Summary:
Name:           octave-foo
Version:
Release:        1
License:        GPL
Group:          Sciences/Mathematics
#Url:           https://packages.octave.org/foo/
Url:
Source0:


Requires:       octave(api) = %{octave_api}

Requires(post): octave
Requires(postun): octave

BuildArch:      noarch

%description


%files
%license COPYING
%doc NEWS
%dir %{octpkgdir}
%{octpkgdir}/*

#---------------------------------------------------------------------------

%prep
%autosetup -p1 -n %{octpkg}-%{version}

%build
%octave_pkg_build

%install
%octave_pkg_install

%check
%octave_pkg_check

%post
%octave_cmd pkg rebuild

%preun
%octave_pkg_preun

%postun
%octave_cmd pkg rebuild
```
## Using git commits as source
This spec file below can be used for software that is sometimes known to have to be packaged off commits such as Zig. In Zig example, it relies on LLVM and if LLVM is updated then Zig will need to updated it a breaking change occurs. To drop the ```%{commit_date}``` from version you can replace ```%define commit_date %{nil}``` with ```#define commit_date %{nil}``` The the software is version 0.15.1 but a commit is needed the new version in this example should be 0.15.1.20251031
```
# set to nil when packaging a release, 
# or the long commit tag for the specific git branch
%define commit_tag %{nil}

# when using a commit_tag (i.e. not nil) add a commit date
# decoration ~0.yyyyMMdd to Version number
%define commit_date %{nil}


Name:
Version:        %{?commit_date:~0.%{commit_date}}
Release:        1
Summary:
Group:
License:
URL:

# change the source URL depending on if the package is a release version or a git version
%if "%{commit_tag}" != "%{nil}"
Source0:        https://github.com/<org_name>/<project_name>/archive/%{commit_tag}.tar.gz#/%{name}-%{version}.tar.gz
%else
Source0:        https://github.com/<org_name>/<project_name>/archive/%{version}.tar.gz#/%{name}-%{version}.tar.gz
%endif

BuildSystem:
BuildRequires:
Requires:

%description

%files
%license
%doc
