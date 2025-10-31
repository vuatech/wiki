---
title: License
description: Notice about licensing requirement
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---
# What is a license?
A software license is a legal instrument that governs the use or redistribution of software, establishing the rights and restrictions for users, developers, and providers.
## Approved license
Generally OSI approved license are allowed without any issues. License can be found at this link. https://opensource.org/licenses In some cases a license name may not be exactly the same as BSD-3-Clause and BSD-3-Clause-Open-MPI. If the text of the license matches the OSI entry then it is safe to say the license was written in a shorthand fashion. Other examples are the GLP-2.0+ that have a variety of shorthand ways to describe the same license.
## License that are open but not OSI approved
While OSI is the golden rule there are some license that are not listed but are in its intent opensource. A good example is WTFPL license below.
```
Everyone is permitted to copy and distribute verbatim or modified copies of this license document, and changing it is allowed as long as the name is changed.
```
If a license falls into this category ask the developers for their opinion before packaging.
## List of license: entries for Spec files
The rpmlint package contains a list of license in the file of /etc/xdg/rpmlint/license.toml. These entries are valid ```license:``` entries for RPM spec files to abide by RPMlint check. For best practice please check and use the appropriate license listed. Failure to do so will result in an RPMlint error, if RPMLint has an error threshold it will fail on the ABF. As of 10/31/2025 there is not a error limit.
