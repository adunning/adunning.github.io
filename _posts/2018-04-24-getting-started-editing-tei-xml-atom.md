---
layout: post
title: "Getting started with editing TEI XML using Atom"
description: "Instructions for setting up Atom as an XML editor for use with the Text Encoding Initiative."
date: 2018-04-24 14:17
last_modified_at: 2018-12-20 22:00
categories: digital editing
---

This post was originally published on the [Digital Latin Library](https://digitallatin.org/blog/setting-atom-editing-texts-digital-latin-library) website, but is applicable to any project using the [Text Encoding Initiative](http://www.tei-c.org/).

---

You will quickly hear about the [Text Encoding Initiative](http://www.tei-c.org/) (TEI) if you spend any amount of time looking into producing a digital edition. The [Digital Latin Library](https://digitallatin.org/) is about to launch, which will be the first serious publisher using TEI, with series run by the [Society for Classical Studies](https://classicalstudies.org/publications-and-research/ldlt-scs-guidelines), [Mediaeval Academy of America](http://www.medievalacademy.org/page/LDLTSubmissions/MAA-Procedures-for-Evaluation-of-Proposals--Submissions-to-the-Library.htm), and Renaissance Society of America. For the first time, scholars will be able to publish peer-reviewed editions of primary sources that are universally accessible to both researchers and the general public, including readers with print disabilities. So where does one start in understanding the basic concepts behind TEI and setting up software for working with XML files?

## Technology-independent editions

The Text Encoding Initiative is based on XML, which works exactly like the HTML tags that underlie every website. The Digital Latin Library has [guidelines for its variant of TEI](https://digitallatin.github.io/guidelines/), allowing you to create files ready for publication. If you've already started on an edition, the DLL team are at work on software to help convert files in other formats, but the final submission will be a TEI XML. It's not a perfect format, but it's the best thing we have for representing the phenoma that we see in premodern texts. As someone who has published editions using [nearly every program available](/critical-edition-software) (including Classical Text Editor, LaTeX, and plain Microsoft Word), allow me to ensure you that this is by far the most efficient and sustainable way of going about it so far.

Editing a file with TEI is much more precise than using a word processor. When you're writing a file in a program such as Microsoft Word or LibreOffice, it forces to you look at your work in visual terms, whereas in editing we need to think about the text's semantic meaning. For instance, when you put text in italics, that doesn't tell us whether it's a foreign word, a title, or a biblical quotation. TEI lets us note these things precisely, which makes it easier to work as a team across different fields, and allows us to create editions that are technology-independent – that work equally well online, in print, or using accessibility devices.

## Software for working with TEI

Because TEI doesn't work in the same way as people tend to write on computers, we can't use an everyday work processor to write using it. When you use Microsoft Word or LibreOffice, this program turns your words into a coded XML file. What you on the screen is a visual representation of markup for computers. There isn't yet software that allows you work visually with TEI XML files, for the simple reason that we don't yet have a critical mass of people who want this. Instead, we working directly with the XML tags. If you haven't worked this way before, it might feel like stepping back into the 1980s: you're working with the same software as programmers use.

You can edit XML in any *plain-text editor.* This is a program that allows you to work with the exact characters being sent to a computer, instead of a visual abstraction. Life will be easier, however, if you use an editor that includes tools for working with XML. Many people in the TEI community use the [Oxygen XML Editor](https://www.oxygenxml.com), which has far more features for working with XML than you'll probably need. If you prefer an editor that is simpler and can be used for other writing and programming tasks, there are other options.

There are many different text editors available; the best for working with TEI at the moment is [Atom](https://atom.io), a highly customizable and open-source program that works on Mac, Windows, and Linux systems. The key feature that you need for basic TEI editing is a [package that validates your XML files](https://atom.io/packages/linter-autocomplete-jing), ensuring that you files conform to the Digital Latin Library guidelines as you work, defined in computer terms by a 'schema'. (There are other editors that include a basic XML validator, but validating TEI requires a more complex schema language called 'Relax NG' that most of them do not support.)

Installing the editor itself is fairly simple, but for XML validation to work, you'll also need Java, which can be fussy to install. These steps should give you a functional setup.

### Installing Atom on a Mac with Homebrew

The quickest method of installing the software you'll need on a Mac is to use the Terminal, a program that gives you direct access to the Unix system at the heart of your computer. It might look daunting if you didn't use a computer before the 1990s, but it simply lets you run commands by typing words instead of clicking buttons. To open the Terminal, look for it in the 'Utilities' folder inside Applications. It functions by writing text-based commands into a prompt.

1. Install [Homebrew](https://brew.sh) by going to its website and pasting the command it gives you into the Terminal. This is a program for adding Unix-based programs to your Mac, many of which are handy for academic purposes.

2. Paste the following lines into the Terminal (you can run each one individually, pressing Return after each line, or copy in the whole thing at once). You will be prompted for your password:

    ```shell
    brew install homebrew/cask/java homebrew/cask/atom
    apm install linter-autocomplete-jing atom-wrap-in-tag atom-beautify tag
    ```

After the installers have run, you will find Atom in your Applications folder. When you open the editor, you will receive messages about needing to install extra dependencies, which you should do. You now have Atom together with the '[linter-autocomplete-jing](https://atom.io/packages/linter-autocomplete-jing)',  '[atom-wrap-in-tag](https://atom.io/packages/atom-wrap-in-tag)', and '[atom-beautify](https://atom.io/packages/atom-beautify)' packages, which make writing XML much easier.

### Installing Atom on Windows

To install Atom and the XML validation package on Windows:

1. Download [Atom](https://atom.io) and run the installer. For more detailed instructions, see [Installing Atom](https://flight-manual.atom.io/getting-started/sections/installing-atom/).
2. Download [Java](https://java.com/download/) and run the installer. If you see any offers to install extra, unrelated software, be sure to decline these.
3.  To install XML validation support:
    1.  Open Atom.
    2.  Type Control + Shift + P to open the Command Palette (which lets
        you run any Atom command: you will use it frequently).
    3.  Search for 'Install Packages and Themes' and select it.
    4.  In the 'Install Packages' window, search for '[linter-autocomplete-jing](https://atom.io/packages/linter-autocomplete-jing)' and click the Install button. If it asks to install extra dependencies, allow it to do so. You'll also likely want the '[atom-wrap-in-tag](https://atom.io/packages/atom-wrap-in-tag)', '[tag](https://atom.io/packages/tag)', and '[atom-beautify](https://atom.io/packages/atom-beautify)' packages.

## Get started with Atom

Because Atom is useful for working not just with XML but any plain-text file, it is used by millions of developers and writers. There is a large community around it, and many introductions to using it. You might be interested in a [recent review of text editors](https://thesweetsetup.com/apps/best-text-editor-macos/) that introduces these programs and highlights some of Atom's key features. These allow you to work far more efficiently than in a standard word processor, even if the initial learning curve is steeper. There is an official [Atom Basics](https://flight-manual.atom.io/getting-started/sections/atom-basics/) guide. [*Learn Enough Text Editor to Be Dangerous*](https://www.learnenough.com/text-editor-tutorial) is a slightly more advanced overview of how text editors work that focuses on Atom.

The Atom community has also produced a vast array of packages that give the editor extra functionality. Many of them are directed towards programming, but some are also useful for using it for everyday writing. For example, [Teletype for Atom](https://teletype.atom.io) allows multiple people to collaborate on a file over the Internet. When working with XML, there are two particularly useful packages: '[atom-wrap-in-tag](https://atom.io/packages/atom-wrap-in-tag)' allows you to select text and wrap it in an XML tag; '[tag](https://atom.io/packages/tag)' gives you a handy keyboard shortcut for closing an XML tag; and '[atom-beautify](https://atom.io/packages/atom-beautify)' can reformat an XML file.

If you find that there are long strongs of TEI tags that you keep writing out (such as a critical apparatus), you can set up [snippets](https://flight-manual.atom.io/using-atom/sections/snippets/) in Atom to save you the typing. For a more user-friendly solution that works anywhere on your computer, try [TextExpander](https://textexpander.com/), which allows you to write small forms that are wonderful for a particular project (for example, I often set up TextExpander snippets that allow me to fill in variants from standard manuscripts in an edition).

Once you're ready to start writing TEI, you might begin with the template on the [Digital Latin Library Guidelines](https://digitallatin.github.io/guidelines/) website. [*What is the Text Encoding Initiative?*](http://books.openedition.org/oep/426) is a more general overview of TEI. The DLL guidelines are based on [EpiDoc](http://epidoc.sourceforge.net): you can also see more examples of how to transcribe Latin manuscripts and inscriptions on its website, and there are also other introductions to it available online.
