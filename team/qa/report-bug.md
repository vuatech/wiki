---
title: How to report a bug
description: 
published: true
date: 2022-03-24T10:53:52.452Z
tags: documentation, qa
editor: markdown
dateCreated: 2020-03-01T21:44:55.485Z
---

# How to report a bug

Description of how to file a bug-report with the maximum precision. In this way developers know exactly what needs to be done to apply fixes to our beloved products. 

## What are bugs?
A software bug is an error, flaw, failure, or fault in a computer software or system that causes it to produce an incorrect or unexpected result, or to behave in unintended ways.

OM Lx users are encouraged to file bug reports if you believe there is a problem needing developer attention. If you have an issue that you think other users can help you with then that is for our [OpenMandriva Forum](https://forum.openmandriva.org/).
If you are in doubt, please post in our forum and someone from QA will advise. 

We are a small all volunteer group so please be patient and give us some time to do things. And thanks in advance for reporting issues with OM Lx.

## Where to report them?

If you want to report a bug please use our [Issue Tracker](https://github.com/OpenMandrivaAssociation/distribution/issues), even if you already reported it on IRC or OpenMandriva Forum.

- A GitHub account is required to use the Issue Tracker
- Click the 'New issue' link (to file a new bug)
- Selecting [Bug report > Get started](https://github.com/OpenMandrivaAssociation/distribution/issues/new/choose) is usually the proper link for common bug reports

## Good practices with bug reporting with OpenMandriva
- Check if a similar issue has already been reported.
If you find the same or very similar issue and it is not confirmed, please do it. This can be done using a short notice like "Confirming in latest OM Lx 4.3 as of 11 March 2022 fully updated". 
- **One bug, one report**
Some people put all of the issues they are facing into one report. Please file a separate bug report for each issue.
- GitHub Issues is not the place to ask for help and general discussion.
Use the public [forum](https://forum.openmandriva.org/) we provide to discuss issues you are facing, discuss them there and if you agree that it should be reported as a bug, do it!
- The official language in bug tracking system is English.
But we do not insist on a specific regional English (like UK-English or American English). We are aware that English is not everyone's native language but we hope you do your best to write reports in English. It is the lingua-franca of the business world after all. Developers, package maintainers, QA-Team, and other contributors do work in English language.
- Make sure the bug is not happening with the upstream project.
At OpenMandriva we are doing a Linux-based distribution, a collection of software we receive from other Free and Open Source software projects. Most OpenMandriva packages are compiled from upstream source code. OpenMandriva does collaborate with upstream projects. We strongly believe that we are a part of the Linux ecosystem as a whole and we want other distributions to benefit from our work.
- User are encouraged to report any issue they believe may be a software error, flaw, failure, or fault in a computer software or system no matter how small.
Even things like typographical errors should be reported and fixed.
- Use a good title which reflects what you are experiencing.
Please include what the problem is. Always write the version or flavour of your OpenMandriva distribution in use. Be precise in order to not waste too much time for developers to identify the particular problem.  
- Provide console output if possible.
If you have problems starting an application for example, please try launching it from the command-line in a terminal emulator. If there is a resulting output with further information please send this output to us in a text-file using a plain text editor such as Kwrite or LeafPad. Just do not use full fledged office suite document formats (.odt-format in LibreOffice etc.) Developers prefer to receive console output rather than screenshots or photographs that have been taken with a smartphone camera on your mobile device. 
- Attach program output from console with 'LC_ALL=C' prefix.
Example: `LC_ALL=C dnf install <some_package>` to force console output in English to make output easier for developers to understand. If your computer uses a language other than English this should be done for **all** commands.
- Logs are the best tool we have for developers to try to understand problems they are unable to reproduce.
The system logs for modern Linux are called the journal and can be accessed with the `journalctl` command. Other common logs are found in the directory `/var/log`. These include dnf.log and Xorg.0.log. If you need help gathering logs for your issue please ask and someone will help.
Note: [om-bug-report tool](/team/qa/bugreport-tool) does include enough log information for many bugs, if developers need more they will ask.
- Try to make sure that you have the latest updates applied.
The reason for this is that we do not want you to waste time when a bugfix has already been applied in updated software.
- Regarding suggestions from users:
Getting new ideas and inspiration from other people is always nice but bug reporting should be on software quality. 
- Please include the omv-bug-report.log file to provide further information about your computer system.

## I have a new package, package upgrade, or new feature request

Please do the following:
- File an issue at [Bug Tracker](https://github.com/OpenMandrivaAssociation/distribution/issues/new/choose) 
- Select one among:
-- *Enhancement request*
-- *Package request*
-- *Package update*
according to your request.

- Write 'Package Request' in the title as well as the name of the package you would like to have built, updated, rolled out etc. Also let us know which version number you would like to have
- Put the URL to the package source, source rpm-URL in the URL field of the form
- Make a few notes in the description field. I would like to request package XYZ
- We will take a look at the project site and will try to fulfill your request
- Keep checking the status of your issue. When we accept the request and when building is underway to 'IN PROGRESS'. Once the package is done, we mark it as 'RESOLVED/FIXED'.

## Common cases
Below you can find some instructions of how to properly file a bug when you fall in these common scenarios.

### My OpenMandriva Lx does not want to start program

OpenMandriva Lx is a collection of software programs that we try to make work as well as possible. It is important to distinguish between console and graphical X-Window applications who provide a graphical user interface.

Here is what you can do to check if a graphical application does not start:
- Open up a terminal when you are logged into your graphical desktop.
  You will find this usually in sections like *Tools* or *System tools*. In KDE Plasma desktop use Konsole, in LXQt use LXQt Terminal.
- Try to launch that application from the command line. If you do not know what to type try to find out the name of the binary you want to start. You can use the package manager to find this. Most of the time it is simply the package name for instance to launch Dolphin file manager in Konsole you simply type 'dolphin' and press <kbd>Enter</kbd>. 
- You might also want to try just typing the beginning letters of the application ('libre' for LibreOffice as an example) and then press the <kbd>Tab</kbd> key to use the auto-completion feature in the bash shell which is running inside that Terminal you just opened. If that does not produce any effect try pressing the <kbd>Tab</kbd> key on your keyboard twice shortly afterwards. You should then be presented with a list of possible matches. 
- After executing the command if you get things like core dumped etc. or unexpected errors, do submit these outputs. Ideally you put these in a text file and attach this file to your bug report using the "Add an Attachment" link in Bugzilla. Please include all output including the command you used.
- Please also let us know which desktop you were using. 
- Remember: **one bug, one report**. This makes it easier for us to tackle the issues one by one.

### My OpenMandriva Lx does not start graphical desktop

With OpenMandriva we use Xorg as a server to serve graphical output to your computer monitor. In case the screen stays black, try switching to login into a virtual terminal that should be set up by default. You can access the virtual terminals by pressing <kbd>Ctrl + Alt + F2</kbd> (or `F3` up to `F6` whatever you preference is).
Try logging in from there and let us know in a bug report which graphics hardware you are using. The following command should supply this information
`lspci -nnk | grep -EiA3 'vga|3d|display'`

Please include the omv-bug-report.log file to provide further information about your computer system.

Also in your bug report please let us know which graphical desktop environment you actually want to start. We use KDE Plasma desktop by default but in case you would like to try some other desktop please do include this in your report.


