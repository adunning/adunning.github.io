---
layout: post
title: "Approaches to producing a critical edition: Classical Text Editor, LaTeX, and TEI"
description: "Overview of different approaches to producing a critical edition, with directions for installing Classical Text Editor on macOS."
date: 2014-02-03 14:06
categories: digital editing
---

(*Updated 24 April 2018.*)

Creating a critical edition is a complex process, and the software supporting it is not for the faint of heart. There are several different approaches, not mutually compatible, and you need to think carefully about the final product and its audience before deciding on a working method.

If you are interested in producing a digital or print–digital hybrid edition, a peer-reviewed environment for publishing your work finally emerged in early 2018, if your source is in Latin. The [Society for Classical Studies](https://classicalstudies.org/publications-and-research/ldlt-scs-guidelines), [Mediaeval Academy of America](http://www.medievalacademy.org/page/LDLTSubmissions), and Renaissance Society of America are launching the [Digital Latin Library](https://digitallatin.org). They are taking texts of any length, and both working and full critical editions, optionally with translations. The Mediaeval Academy will also consider book-length texts for co-publication with the University of Toronto Press. All this is exactly what scholars have been asking for, and has the potential to go beyond what a print edition can normally do. The underlying mechanism is the [Text Encoding Initiative](http://www.tei-c.org/) (TEI), a set of guidelines developed since the 1980s, but this seems to be the first serious publication project using it. (For shorter texts, the [Scholarly Editing](http://scholarlyediting.org) journal remains an option, taking texts in any language.) There are also scripts available for typesetting TEI using LaTeX and Reledmac, as demonstrated in the [TEI Critical Apparatus Toolbox](http://ciham-digital.huma-num.fr/teitoolbox/). This is still a shifting area, but there is much that looks promising. I have written a [post on setting up software to work with TEI for the Digital Latin Library](https://digitallatin.org/blog/setting-atom-editing-texts-digital-latin-library).

If you're producing a printed edition, [Classical Text Editor](http://cte.oeaw.ac.at) (CTE) offers the only software for creating a critical edition with a graphical interface, imitating older versions of Microsoft Word. Its primary strength is in typesetting a traditional critical edition, and the results are very good, allowing for attention to various typographical niceties that many publishers have ignored for the last few decades. Its author, Stefan Hagel, is extremely responsive. It is possible to achieve good results using it, relatively quickly. There is some support for creating digital editions, but this aspect remains underdeveloped – entirely [due to lack of demand](http://www.infotext.unisi.it/upload/DIGIMED06/book/hagel.pdf), according to Dr Hagel.

Before using CTE for a new edition, make sure that you have a statement from your publisher, in writing, that they will accept your submission in CTE format. The [CSEL](http://csel.sbg.ac.at) series supports it, and [Corpus Christianorum](http://www.corpuschristianorum.org/authors.html) will accept CTE files with advance permission. The author guidelines for prominent series such as [Oxford Medieval Texts](http://global.oup.com/fdscontent/academic/pdf/academic/history/omt_style.pdf), the [Dumbarton Oaks Medieval Library](http://domedieval.org), and [Dallas Medieval Texts](http://dallasmedievaltexts.org) all ask specifically for Microsoft Word files. The production process in converting a Word text into a critical edition is laborious and error-prone: essentially unchanged from that described in M.L. West's *Textual Criticism and Editorial Technique* (Stuttgart, 1973).

If you need to produce a critical apparatus on your own (either for a publisher that requires camera-ready submission or for a thesis) and either want the absolute best typography possible or cannot afford CTE's licensing fee, the next most usable option is [critical edition typesetting with LaTeX](http://www.webdesign-bu.de/uwe_lueck/critedltx.html). LaTeX edges out CTE in its typesetting quality through its implementation of the [Knuth–Plass line breaking algorithm](https://doi.org/10.1002/spe.4380111102); combined with the [Microtype](https://ctan.org/pkg/microtype) package, this produces the best automatic paragraph composition available anywhere. The [Reledmac](https://ctan.org/pkg/reledmac) package for typesetting a critical apparatus and parallel text is in active development. Many publishers use LaTeX behind the scenes after taking your Microsoft Word file, and are often willing to take direct submissions in this format on request. LaTeX was designed in the 1980s, however, and it can be daunting to learn if you are not familiar with it.

# Installing Classical Text Editor on the Mac

Classical Text Editor is a Windows-only program, but there are two approaches to installing it on Mac or Linux systems:

1. Run a full copy of Windows on your computer using a program such as [Parallels Desktop](https://www.parallels.com/) or [VirtualBox](https://www.virtualbox.org). This is the only way to produce PDFs including OpenType fonts from Classical Text Editor, but requires buying an extra copy of Windows as well as the virtual machine software.
2. Use [Wine](http://www.winehq.org), an open-source package that duplicates the parts of Windows necessary to running its programs, as an alternative to running a full copy of the operating system. The [result is not perfect](https://appdb.winehq.org/objectManager.php?sClass=application&iId=15806), but allows for everyday modifications of Classical Text Editor documents, and is faster than running a full copy of Windows.

![Classical Text Editor running under Wine](/images/cte-mac-main-window.png)

Wine programs need to be installed using the Terminal. The best method for using it on the Mac is to install Wine via the [Homebrew](https://brew.sh) package manager. (Linux users can use a similar technique by installing Wine and starting with step 3.) This provides the most up-to-date software and does not involve additional licensing fees:

1. Install [Homebrew](https://brew.sh).

2. Install Wine using Homebrew by running the following in the Terminal:

    ```shell
    brew install wine winetricks
    ```

3. To ensure CTE is installed with the software it needs, run this in the Terminal:

    ```shell
    WINEARCH=win32 winetricks usp10 fontsmooth=rgb
    ```

4. To install CTE itself, download [Classical Text Editor](http://cte.oeaw.ac.at). To run the installer, type `wine` in the Terminal followed by a space, drag the installer file into the Terminal window, press Return, and follow the steps. You can then close the Terminal.

5. To open CTE, [download my shortcut script](/files/cte-shortcut.zip) and place it in the Applications folder: it will work on any Mac using the default settings. You can also create your own version of this script using the [instructions from the official Wine website](https://wiki.winehq.org/MacOS_FAQ#How_to_create_shortcut.2C_launcher.2C_or_.app_to_start_a_given_.exe.3F).

To update the program in the future, follow the same technique as in step 4, but running the update installer rather than the original program's installer.

Classical Text Editor's built-in PDF creation mechanism will not work with Wine. It is possible to produce basic PDFs by installing [VipRiser](https://onflapp.wordpress.com/vipriser/), a virtual PDF printer ([detailed instructions](http://macvalley.blogspot.ca/2017/01/installiing-vipriser-pdf-printer-that.html)), but there are often issues with missing characters if you are using OpenType fonts.

Note that Classical Text Editor will not work in a 64-bit Wine environment (the help system will not work, you will receive various error messages when running the installer, it cannot connect to the Internet, and so forth). If you find yourself in this situation, run `rm -rf ~/.wine` (deleting your Wine files) and start again with step 3.

If you later wish to uninstall everything, run:

```shell
rm -rf ~/.wine && brew uninstall wine winetricks
```

For a slightly more user-friendly installation method, [CrossOver](https://www.codeweavers.com) is a commercial package that guides you through the process (but does not improve the functionality of CTE itself). A previous version of this guide recommended [WineBottler](http://winebottler.kronenberg.org), a free alternative, but it is no longer actively developed.
