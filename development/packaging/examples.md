---
title: Examples
description: Explaining examples of spec files created and maintained
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---
Place holder
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
```
Good example for cargo toml
https://github.com/OpenMandrivaAssociation/typst
