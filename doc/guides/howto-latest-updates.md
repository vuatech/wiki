---
title: How to get a list of the latest updates
description: 
published: true
date: 2020-03-13T07:55:04.233Z
tags: 
---

# How to get a list of the latest updates
Sometimes updates may cause some sort of malfunctioning and in such a case it may be useful to have at hand a list of the latest updates while looking for the source of the problem.

Let's start with a complete list, from which we can get some useful informations.

The main command is

```
rpm -qa --last
```

which prints this kind of list:
.

    korganizer-17.12.2-1-omv2015.0.x86_64         Thu 15 Mar 2018 05:27:48 PM CET
    incidenceeditor-17.12.2-1-omv2015.0.x86_64    Thu 15 Mar 2018 05:27:48 PM CET
    lib64vdpau-drivers-17.3.6-1-omv2015.0.x86_64  Thu 15 Mar 2018 05:27:47 PM CET
    lib64korganizer_core5-17.12.2-1-omv2015.0.x86_64 Thu 15 Mar 2018 05:27:47 PM CET
    spectacle-17.12.2-1-omv2015.0.x86_64          Thu 15 Mar 2018 05:27:45 PM CET
    locales-en-2.27-9-omv2015.0.x86_64            Thu 15 Mar 2018 05:27:45 PM CET
    kdf-17.12.2-1-omv2015.0.x86_64                Thu 15 Mar 2018 05:27:44 PM CET
    task-plasma-5.10.5-4-omv2015.0.x86_64         Thu 15 Mar 2018 05:27:43 PM CET
    okular-tiff-17.12.2-1-omv2015.0.x86_64        Thu 15 Mar 2018 05:27:43 PM CET


Note: The list may be very long and some rows might not be included.
To be sure to see them all, to read it more easily or to provide it as attachment, it is useful to convert the console output in a text document.

_Example_:
```
rpm -qa --last > rpmlast.txt
```
A document `rpmlast.txt` will be created in your /home directory.

You may want to specify a different filename every time you run the above command in order to obtain a new file and not to overwrite the previous one.

_Example_:
```
rpm -qa --last > rpmlast_20180315.txt
```

The document can also be saved in ".csv" format (Comma Separated Value), to be easily imported into a spreadsheet
_for example Calc_:

```
rpm -qa --last> rpmlast_20180315.csv
```

The list may contain many rows, but you can narrow down the list by indicating the date.

_Example_:
```
rpm -qa --last | grep Mar
``` 
provides updates made in March. To know how to shorten the month just look in the document created with the main command shown above.

You can also restrict your search to a specific day:

_Example_:
```
rpm -qa --last | grep Thu\ 15\ Mar
```

.