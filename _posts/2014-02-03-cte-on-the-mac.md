---
layout: post
title: "Approaches to producing a critical edition: TEI, LaTeX, and Classical Text Editor"
description: "Overview of different approaches to producing a critical edition, with directions for installing Classical Text Editor on macOS."
date: 2014-02-03 14:06
categories: digital editing
---

(*Updated 28 March 2018.*)

Creating a critical edition is a complex process, and the software supporting it is not for the faint of heart. There are several different approaches, not mutually compatible, and you need to think carefully about the final product and its audience before deciding on a working method.

If you wish to produce an edition that may have a life both online and in print, as for the [Digital Latin Library](https://digitallatin.org), your work will be most useful over the long term by using a version of the [Text Encoding Initiative](http://www.tei-c.org/) (TEI) guidelines. Using TEI has meant producing everything from the ground up in the past, but resources such as the [TEI Critical Apparatus Toolbox](http://ciham-digital.huma-num.fr/teitoolbox/) are gradually making it into a viable solution. This is still a shifting area as of early 2018 – it must be said that no publisher other than the Digital Latin Library accepts TEI files, and they have very specific [guidelines](https://digitallatin.github.io/guidelines/) – but there is much that looks promising.

If you are producing an edition that you only intend to appear in print, you should consult with your prospective publisher on the best approach as soon as possible. The author guidelines for [Oxford Medieval Texts](http://global.oup.com/fdscontent/academic/pdf/academic/history/omt_style.pdf), the [Dumbarton Oaks Medieval Library](http://domedieval.org), [Dallas Medieval Texts](http://dallasmedievaltexts.org), and [Corpus Christianorum](http://www.corpuschristianorum.org/authors.html) series all prefer Microsoft Word files. This process is laborious and error-prone: essentially unchanged from that described in M.L. West's *Textual Criticism and Editorial Technique* (Stuttgart, 1973).

If you need to typeset an apparatus on your own, [critical edition typesetting with LaTeX](http://www.webdesign-bu.de/uwe_lueck/critedltx.html) produces the absolute best results possible. The [Reledmac](https://ctan.org/pkg/reledmac) package is in active development. If you are taking this approach, you might wish to encode your work using TEI, to allow for wider possibilities in publication; the conversion mechanisms from TEI to print use LaTeX. Many publishers use LaTeX behind the scenes after taking your Microsoft Word file, and are often willing to take submissions in this format on request.

Finally, [Classical Text Editor](http://cte.oeaw.ac.at) (CTE) offers a graphical interface that many scholars find easier to learn. The [CSEL](http://csel.sbg.ac.at) series supports it, and Corpus Christianorum will accept CTE files with advance permission. Although it theoretically has a TEI export function, it remains underdeveloped – [due to lack of demand](http://www.infotext.unisi.it/upload/DIGIMED06/book/hagel.pdf), according to its author. Its true strength is in typesetting a traditional critical edition for print, and in this it nearly matches the levels of quality possible with LaTeX, which narrowly edges it out through its implementation of the [Knuth–Plass line breaking algorithm](https://doi.org/10.1002/spe.4380111102) (combined with the [Microtype](https://ctan.org/pkg/microtype) package, this produces the best automatic paragraph composition available anywhere). That said, CTE is much easier to deal with in many respects, and if you are not already experienced with LaTeX, it is possible to achieve good results more quickly using CTE.

# Installing Classical Text Editor on the Mac

CTE is a Windows-only program, but there are two approaches to installing it on Mac or Linux systems:

1. Run a full copy of Windows on your computer using a program such as [Parallels Desktop](https://www.parallels.com/) or [VirtualBox](https://www.virtualbox.org). This is the only way to produce PDFs including OpenType fonts from Classical Text Editor.
2. Use [Wine](http://www.winehq.org), an open-source package that duplicates the parts of Windows necessary to running its programs, as an alternative to running a full copy of the operating system. The [result is not perfect](https://appdb.winehq.org/objectManager.php?sClass=application&iId=15806), but allows for everyday modifications of Classical Text Editor documents, and is faster than running a full copy of Windows.

![Classical Text Editor running under Wine](/images/cte-mac-main-window.png)

Wine programs need to be installed using the Terminal. The best method for using it on the Mac is to install Wine via Homebrew. This provides the most up-to-date software and does not involve additional licensing fees:

1. Install [Homebrew](https://brew.sh).

2. Install Wine using Homebrew by running the following in the Terminal:

    ```shell
    brew tap caskroom/cask && brew cask install xquartz && brew install wine winetricks
    ```

3. To ensure CTE is installed with the software it needs, run this in the Terminal:

    ```shell
    WINEARCH=win32 winecfg && winetricks usp10 fontsmooth=rgb
    ```

4. To install CTE itself, download [Classical Text Editor](http://cte.oeaw.ac.at). To run the installer, type `wine` in the Terminal followed by a space, drag the installer file into the Terminal window, press Return, and follow the steps.

5. To open CTE, [download my shortcut script](/files/cte-shortcut.zip) and place it in the Applications folder: it will work on any Mac using the default settings. You can also create your own version of this script using the [instructions from the official Wine website](https://wiki.winehq.org/MacOS_FAQ#How_to_create_shortcut.2C_launcher.2C_or_.app_to_start_a_given_.exe.3F).

Classical Text Editor's built-in PDF creation mechanism will not work with Wine. It is possible to produce basic PDFs by installing [VipRiser](https://onflapp.wordpress.com/vipriser/), a virtual PDF printer ([detailed instructions](http://macvalley.blogspot.ca/2017/01/installiing-vipriser-pdf-printer-that.html)), but there are often issues with missing characters if you are using OpenType fonts.

Note that Classical Text Editor will not work in a 64-bit Wine environment (the help system will not work, you will receive various error messages when running the installer, it cannot connect to the Internet, and so forth). If you find yourself in this situation, run `rm -rf ~/.wine` (deleting your Wine files) and start again with step 3.

If you later wish to uninstall everything, run:

```shell
rm -rf ~/.wine && brew uninstall wine winetricks && brew uninstall $(join <(brew leaves) <(brew deps wine)) && brew cask uninstall xquartz
```

For a slightly more user-friendly installation method, [CrossOver](https://www.codeweavers.com) is a commercial package that guides you through the process (but does not improve the functionality of CTE itself). A previous version of this guide recommended [WineBottler](http://winebottler.kronenberg.org), a free alternative, but it is no longer actively developed.
