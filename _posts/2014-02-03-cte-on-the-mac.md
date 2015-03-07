---
layout: post
title: "Installing Classical Text Editor in Mac OS X using Wine"
description: "Directions for installing Classical Text Editor using WineBottler."
date: 2014-02-03
category: posts
---

[Classical Text Editor](http://cte.oeaw.ac.at) can be used on Mac or Linux systems using [Wine](http://www.winehq.org), an open-source software package that attempts to duplicate the parts of Windows necessary to running its programs, as an alternative to running a full copy of the operating system. The [result is not perfect](https://appdb.winehq.org/objectManager.php?sClass=application&iId=15806), but allows for most day-to-day use.

![Classical Text Editor running under Wine](/images/cte-mac-main-window.png)

The program is most easily installed on OS X using WineBottler:

1. Download and install the [development version of WineBottler](http://winebottler.kronenberg.org); the development rather than the stable version tends to work better.

2. Download the current [demo version of Classical Text Editor](http://cte.oeaw.ac.at/?id0=download).

3. Open WineBottler, and go the Advanced section. Change the following options:
    - Select the `cte32_9.exe` file downloaded (`cte32demo12.exe` if you are using version 8) as the program to install.
	- In the Wineticks section, type `uniscribe` into the search field, and check the box beside `Uniscribe 1.325`.
	- Change the bundle identifier to `at.ac.oeaw.cte` (deleting the existing `yourcompany` identifier).

	![WineBottler advanced settings](/images/winebottler-settings.png)

4. Clicking the Install button will launch the CTE installer and walk you through the standard Windows installer; you can use the default settings. You will find it installed in your Applications folder.

5. Download a [newer copy of Uniscribe](http://homepage.univie.ac.at/stefan.hagel/cte/usp10.dll), which is necessary for OpenType support. Copy this file into CTE by choosing the 'Go to Folder' option in the Finder's Go menu, and typing `~/Library/Application Support/`. In the resulting window, look for a folder beginning with 'at.ac.oeaw.cte'; inside this folder, open `drive_c`, `Program Files`, and finally `Classical Text Editor`. Copy the `usp10.dll` file that you downloaded into this folder.

6. (*No longer necessary under version 9.*) To register a licence for version 8, select the 'Upgrade to Full Version' option in the Help menu, which will download a file called `cte32upd12.exe`. Right-click (or control-click) on the file, go to the 'Open With' menu, and choose Wine. In the resulting dialogue box, choose to run the file directly (choosing the `at.ac.oeaw.cte` option if it is not already selected). The updater will run, following which you can follow the instructions provided by Stefan Hagel to register the program. You may be prompted to enter a user and company name, which needs to match the name provided for the licence (both can also be left blank); if you find that you have made a mistake with either of these, you can change the registered name by opening the Wine application, selecting the wine glass icon that appears in your menu bar, and selecting the Configuration option. The owner and organization are changed in the 'About' tab.

7. (*optional*) If you wish to be able to create PDFs from the program, within the limitations listed above, this is possible by installing [PDFwriter](http://pdfwriterformac.sourceforge.net). Note that the operation of this program is slightly unusual; be sure to read its documentation.

(*Updated 6 March 2015 to reflect changes in CTE version 9.*)
