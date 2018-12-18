---
layout: post
title: "Installing Classical Text Editor on a Mac"
description: "Directions for installing Classical Text Editor (CTE) on macOS using Wine."
date: 2014-02-03 14:06
last_modified_at: 2018-12-18 14:00
categories: digital editing
---

[Classical Text Editor](http://cte.oeaw.ac.at) (CTE) is the most successful program, at this writing, for typesetting a critical edition of a text. There is [other software](/critical-edition-software) available for creating such works, but CTE is the only one that comes with a visual interface.

[Stefan Hagel](https://homepage.univie.ac.at/Stefan.Hagel/) wrote Classical Text Editor for Windows, but if you are using a Mac or Linux system, you have two options:

1. Run a full copy of Windows on your computer using a program such as [Parallels Desktop](https://www.parallels.com/) or [VirtualBox](https://www.virtualbox.org). This is the only way to produce PDFs including OpenType fonts from Classical Text Editor, but requires buying an extra copy of Windows as well as the virtual machine software.
2. Use [Wine](http://www.winehq.org), an open-source package that duplicates the parts of Windows necessary to running its programs, as an alternative to running a full copy of the operating system. The [result is not perfect](https://appdb.winehq.org/objectManager.php?sClass=application&iId=15806), but allows for everyday modifications of Classical Text Editor documents, and is faster than running a full copy of Windows.

![Classical Text Editor running under Wine](/images/cte-mac-main-window.png)

Wine programs need to be installed using the Terminal, simplified on the Mac using the [Homebrew](https://brew.sh) package manager. (Linux users can use a similar technique by installing Wine and starting with step 3.) This provides the most up-to-date software and does not involve additional licensing fees. You won't need the Terminal after installing CTE.

The Terminal allow you to run Unix commands directly on your Mac. Follow these steps by opening the Terminal program in your Utilities folder, pasting the full line into the window, and pressing return to run the command:

1. Install [Homebrew](https://brew.sh) using the directions on the official website.

2. Install Wine using Homebrew by pasting this line into a Terminal window:

    ```shell
    brew install wine winetricks
    ```

3. Configure the Wine environment for CTE and install Uniscribe:

    ```shell
    WINEARCH=win32 winetricks usp10 fontsmooth=rgb
    ```

4. To install CTE itself, download [Classical Text Editor](http://cte.oeaw.ac.at). To run the installer, type `wine` in the Terminal followed by a space, drag the installer file into the Terminal window, press Return, and follow the steps. You can then close the Terminal.

5. To open CTE, [download my launcher script](/assets/cte-shortcut.zip) and place it in the Applications folder: it will work on any Mac using the default settings. This is a simple AppleScript program: open it using the Script Editor, in your Utilities folder, if you want to see what it does. (I updated the script on 18 December 2018 to correct a problem causing CTE not to recognize any printers. Redownload the script if you are experiencing this problem.)

To update the program in the future, follow the same technique as in step 4, but drag the update installer into the Terminal window rather than the original program installer.

To update to a newer version of Wine:

```shell
brew update && brew upgrade
```

If you later wish to uninstall everything, run:

```shell
rm -rf ~/.wine && brew uninstall wine winetricks
```

For a slightly more user-friendly installation method, [CrossOver](https://www.codeweavers.com) is a commercial package that guides you through the process (but does not improve the functionality of CTE itself). A previous version of this guide recommended [WineBottler](http://winebottler.kronenberg.org), a free alternative, but it no longer runs on newer systems.

# Caveats

Classical Text Editor's built-in PDF creation mechanism will not work with Wine. It is possible to produce basic PDFs by installing [VipRiser](https://onflapp.wordpress.com/vipriser/), a virtual PDF printer ([detailed instructions](http://macvalley.blogspot.ca/2017/01/installiing-vipriser-pdf-printer-that.html)), but there are issues with missing characters if you are using OpenType fonts.

CTE will not operate under a 64-bit Wine environment (the help system will not work, you will receive various error messages when running the installer, it cannot connect to the Internet, and so forth). If you find yourself in this situation, run `rm -rf ~/.wine` (deleting CTE and any other Wine files) and start again with step 3.
