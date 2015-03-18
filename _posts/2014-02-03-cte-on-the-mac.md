---
layout: post
title: "Installing Classical Text Editor in Mac OS X using Wine"
description: "Directions for installing Classical Text Editor using WineBottler."
date: 2014-02-03 14:06
category: posts
---

[Classical Text Editor](http://cte.oeaw.ac.at) can be used on Mac or Linux systems using [Wine](http://www.winehq.org), an open-source package that duplicates the parts of Windows necessary to running its programs, as an alternative to running a full copy of the operating system. The [result is not perfect](https://appdb.winehq.org/objectManager.php?sClass=application&iId=15806), but allows for most day-to-day use.

![Classical Text Editor running under Wine](/images/cte-mac-main-window.png)

The program is most easily installed on OS X using WineBottler:

1. Download and install the [development version of WineBottler](http://winebottler.kronenberg.org).

2. Download the [demo version of Classical Text Editor](http://cte.oeaw.ac.at/?id0=download).

3. Open WineBottler, and go the Advanced section. Change the these settings:
    - Select the `cte32_9.exe` file downloaded (`cte32demo12.exe` if you are using version 8) as the program to install.
	- In the Wineticks section, type `uniscribe` into the search field, and check the box beside `usp10` to include Uniscribe 1.325.
	- Change the identifier to `at.ac.oeaw.cte`.

    ![WineBottler advanced settings](/images/cte-winebottler-settings.png)

4. Clicking the Install button will prompt you to save the program. Naming it 'Classical Text Editor' and saving it in the Applications folder is likely most desirable. It will then launch the CTE installer and walk you through the standard Windows installer; you can use the default settings. Choose `CTE.exe` as the 'startfile' when prompted.

    ![WineBottler 'Startfile'](/images/cte-winebottler-startfile.png)

5. Launch Classical Text Editor and close it again. This installs its configuration files.

6. Download a [newer copy of Uniscribe](http://homepage.univie.ac.at/stefan.hagel/cte/usp10.dll), which is necessary for OpenType support. Copy this file into CTE by choosing the 'Go to Folder' option in the Finder's Go menu, and typing `~/Library/Application Support/`. In the resulting window, look for a folder beginning with `at.ac.oeaw.cte`; inside this folder, open `drive_c`, `Program Files`, and finally `Classical Text Editor`. Move the `usp10.dll` file that you downloaded into this folder.

7. If you wish to update the program in the future, you may have to first open the Wine application, open the wine glass menu, choose the 'Change Prefix' item, and double-click the `at.ac.owae.cte` line (this is only necessary after the program is first installed). After this, right-click (or control-click) on the downloaded updater, go to 'Open With' in the contextual menu, and choose Wine. In the resulting dialogue box, choose to run the file directly under the `at.ac.oeaw.cte` prefix.

8. (*optional*) If you wish to be able to create PDFs from the program, within the limitations listed above, this is possible by installing [PDFwriter](http://pdfwriterformac.sourceforge.net). The operation of this program is slightly unusual; be sure to read its instructions.

(*Updated 18 March 2015 to reflect changes in CTE version 9.*)
