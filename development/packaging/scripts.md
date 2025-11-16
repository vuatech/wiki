---
title: Scripts for common processes
description: List of scripts for common processes
published: false
date: 2025-11-16T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-16T23:43:56Z
---
#Cargo
This script should vendor and archive the dependencies. Source will need to be added to spec file along with the correct ```%prep``` needs to point cargo to the vendor folder.
```
#!/bin/sh
################################################################################
# Source of this script: https://gitlab.com/-/snippets/4827226
################################################################################
# Shell script to create vendored crate archives for rust packages from the RPM-
# spec file based packaging system used by OpenMandrivaLx.
#
# The archive produced by this script can then be uploaded to the abf-
# infrastructure and linked to in the packages spec file & the .abf.yml file's-
# contents can be updated accordingly.
################################################################################
# NOTE	If upgrading a package update the spec file's "Version:" parameter-
# NOTE	BEFORE running this script, in order for it to download the new sources.
################################################################################
# NOTE	This script assumes you have ensured the package source name-versioned
# NOTE	tarball archive resides next to both this script and the spec file.
# NOTE	In the event that you forgot to do that, this script will attempt to
# NOTE	download the archive from the Source0: parameter value listed in
# NOTE	the spec file.
################################################################################
# NOTE	Package sources must be following the naming convention format of:
# NOTE	name-version.tar.gz for this script to function.
################################################################################
# NOTE	If an oname exists in the spec file due to upstream repo/package-
# NOTE	naming quirks then this script will prioritise the spec file oname-
# NOTE	parameter value over the package's Name: parameter value.
################################################################################
# NOTE	Generated vendor archives will be in the format of:
# NOTE	name-version-vendor.tar.xz
################################################################################
# NOTE	Usual caveats apply:
# NOTE	Only modify this script if you know what you are doing.
# NOTE	Using this script is entirely at your own risk.
################################################################################
# NOTE	You can edit the parameter below IF upstream sources are using a
# NOTE	different tarball archive compression type.
#
# Upstream source archive filetypes are usually gzipped tarballs, occsionally
# they are not, alternatives are "tar.xz", this parameter is exposed here to
# change the source tarball archive filetype should you need to.
#
PACKAGE_ARCHIVE_KIND="tar.gz"
#
SUBPKG_DIR="src/"
SUBPKG_NAME="_bcrypt"
#
################################################################################
# Science happens below this line.
################################################################################
#
DownloadSource () {
	local FILENAME=$( basename $1 )
	if  [ ! -f "./${FILENAME}"  ]; then
		printf "${FILENAME} does not exist in package directory. \nAttempting to download..\n"
		if curl -o /dev/null -sfL -r 0-0 "${1}"; then
			printf "File exists on remote, downloading..\n"
			curl -o "${FILENAME}" -L $1
		else
			printf "URI/Archive: $FILENAME does not exist on remote server. \nCheck package Name or oname define in spec file.\n\n"
			exit 0
		fi
else
	printf "${FILENAME} exists in package directory, skipping download attempt.\n"
fi
}

printf  "Constructing archive name using parameters from package spec file...\n"
# Construct our packages archive name using spec file parameters
# Get package name from spec file
PACKAGE_NAME=$(awk -F ":" '/Name/ {print $2}' *.spec)
# Remove leading and trailing whitespace from PACKAGE
PACKAGE_NAME="${PACKAGE_NAME#"${PACKAGE_NAME%%[![:space:]]*}"}"
PACKAGE_NAME="${PACKAGE_NAME%"${PACKAGE_NAME##*[![:space:]]}"}"
PKG_NAME=$PACKAGE_NAME
# Get version from spec file
VERSION=$(awk -F ":" '/Version/ {print $2}' *.spec)
# Remove leading and trailing whitespace from VERSION
VERSION="${VERSION#"${VERSION%%[![:space:]]*}"}"
VERSION="${VERSION%"${VERSION##*[![:space:]]}"}"
VSN=$VERSION
#Get the package source URL from the spec file
PACKAGE_SRC=$(awk -F " " '/^Source:|^Source0:/ {print $2}' *.spec)
if [ ! $PACKAGE_SRC ]; then
	printf "No 'Source:' or 'Source0:' parameter provided in spec file. \nCheck your spec file's 'Source:' lines, this script only accepts the values from the 'Source:' OR 'Source0:' parameters\n"
	exit 0
fi

# Replace spec macros with variable strings
PACKAGE_SRC=$(echo ${PACKAGE_SRC} | sed -e 's,\%{version},'${VERSION}',g')
################################################################################
# if spec has '%define oname NAME' declared prioritise that repo name-
# to download the source from
ONAME=$(awk -F " " '/%define oname/ {print $3}' *.spec)
if [ ${ONAME} ]; then
	PACKAGE_SRC=$(echo ${PACKAGE_SRC} | sed -e 's,\%{oname},'${ONAME}',g')
	PKG_NAME=${ONAME}
else
	PACKAGE_SRC=$(echo ${PACKAGE_SRC} | sed -e 's,\%{name},'${PACKAGE_NAME}',g')
fi


printf "Constructed package archive name: $PACKAGE_SRC \n"
################################################################################
DownloadSource ${PACKAGE_SRC}
################################################################################
# More science
# Leverage find to case-insensitively locate the actual archive filename
echo -e "pwd: $(pwd)"
 ARCHIVE_NAME=$(find ./ -iname "$PKG_NAME-$VSN" -type f)
if [ -f $ARCHIVE_NAME ]; then
	ARCHIVE_NAME="$PKG_NAME-$VSN.$PACKAGE_ARCHIVE_KIND"
	printf "arch-name: $ARCHIVE_NAME\n"
else
	printf "Cannot construct archive name from input values\n"
	printf "arch-name2: $ARCHIVE_NAME\n"
	exit 0
fi
printf "Finding and using real archive name: $ARCHIVE_NAME\n"

################################################################################
printf "Extracting package source archive...\n"
# Extract the source tarball archive
tar -xf "$ARCHIVE_NAME"
################################################################################
# Move into extracted archive directory
if [ $SUBPKG_NAME ]; then
	cd ./${ARCHIVE_NAME%%.$PACKAGE_ARCHIVE_KIND}/$SUBPKG_DIR$SUBPKG_NAME
else
	cd ./${ARCHIVE_NAME%%.$PACKAGE_ARCHIVE_KIND}
fi
printf "Moved into archive directory: $(pwd)\n"
################################################################################
# cargo vendor all the crates
printf "Running cargo vendor...\n"
cargo vendor
################################################################################
printf "\nArchiving vendor directory...\n"
# Archive the vendor directory
tar -cJf vendor.tar.xz ./vendor
################################################################################
# Move & rename vendor archive out to package root dir
if [ $SUBPKG_NAME ]; then
	if [ $SUBPKG_DIR ]; then
		mv -f ./vendor.tar.xz "../../../$SUBPKG_NAME-$VERSION-vendor.tar.xz"
		cd ../..
		printf "Moving vendor archive out to package directory at: $(pwd)/$SUBPKG_NAME-$VERSION-vendor.tar.xz\n"
	else
		mv -f ./vendor.tar.xz "../../$SUBPKG_NAME-$VERSION-vendor.tar.xz"
		cd ../..
		printf "Moving vendor archive out to package directory at: $(pwd)/$SUBPKG_NAME-$VERSION-vendor.tar.xz\n"
	fi
else
	mv -f ./vendor.tar.xz "../$PKG_NAME-$VERSION-vendor.tar.xz"
	cd ..
	printf "Moving vendor archive out to package directory at: $(pwd)/$PKG_NAME-$VERSION-vendor.tar.xz\n"
fi
################################################################################
printf "Cleaning up files used to create vendored archive.\n"
# Cleanup directories and files used to create vendoring archive, leave package-
# directory as it was found plus the additon of archive this script created.
rm -rf ./${ARCHIVE_NAME%%.$PACKAGE_ARCHIVE_KIND}
printf "Package crate vendoring archive creation completed.\n"
################################################################################
################################################################################

```
