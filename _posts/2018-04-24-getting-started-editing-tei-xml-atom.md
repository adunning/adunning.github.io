---
layout: post
title: "Getting started with editing TEI XML using Atom"
description: "Instructions for setting up Atom as an XML editor for use with the Text Encoding Initiative."
date: 2018-04-24 14:17
last_modified_at: 2019-01-11 22:00
categories: digital editing
---

You will quickly hear about the [Text Encoding Initiative](http://www.tei-c.org/) (TEI) if you spend any amount of time looking into producing a digital edition. But it's not a piece of software that you can install on your computer. So how do you create TEI files?

## What is TEI?

The Text Encoding Initiative is a 'markup language', a set of standard tags that tell a computer how to interpret a file. TEI is based on XML, which works exactly like the HTML tags that underlie every website.

Editing a file with TEI is much more precise than using a word processor. When you're writing a file in a program such as Microsoft Word or LibreOffice, it forces to you look at your work in visual terms. But we need to think about the text's semantic meaning. For instance, when you put text in italics, that doesn't tell us whether it's a foreign word, a title, or a biblical quotation. TEI lets us note these things precisely, which makes it easier to work as a team across different fields, and allows us to create editions that are 'technology-independent' – that work equally well online, in print, or using accessibility devices.

## Software for TEI

You can edit XML in any 'plain-text editor', a program that allows you to work with the exact characters being sent to a computer. You already have TextEdit (Mac) or Notepad (Windows), and you can edit a TEI file with these programs, but your life will easier with tools designed for working with XML.

The best introductory text editor for TEI is [Atom](https://atom.io), a highly customizable and open-source program that works on Mac, Windows, and Linux systems. The key feature that you need for basic TEI editing is XML 'validation', which checks your files against a TEI 'schema' as you work.

Many people in the TEI community use the [Oxygen XML Editor](https://www.oxygenxml.com). It's devoted specifically to XML, but it has far more features than you need if you're simply creating a transcription or edition.

To use Atom together with its packages for XML, you'll both Atom itself and Java. You can install this using the Terminal on the Mac, or using a Web browser on either a Mac or Windows.

## Installing Atom with the Terminal (Mac)

This is the most reliable way to install Atom if you'll be doing more digital humanities work in the future, or if you have a technical friend lending a hand. If you're not planning to go any further than writing TEI files and find the Terminal too intimidating, you can follow the steps in the next section instead.

This approach uses Homebrew, a program for adding Unix-based programs to your Mac. Homebrew is a lifesaver for supporting work in programming, text or image processing, and typesetting. Many online tutorials refer to it, so it's worth learning.

This will install Atom and its packages for XML using Homebrew:

1. Open the Terminal, inside your 'Utilities' folder inside Applications. Terminal gives you direct access to the Unix system at the heart of your computer. It might look daunting if you didn't use a computer before the 1990s, but it simply lets you run commands by typing words instead of clicking buttons.

2. Install [Homebrew](https://brew.sh) by going to its website and pasting the command it gives you into the Terminal.

3. Install Atom and Java using Homebrew by copying this line into the Terminal:

    ```shell
    brew install homebrew/cask/java homebrew/cask/atom
    ```
    
    You will be prompted for your password, which won't appear on your screen as you type; just press return after entering it. If you already had an old version Atom installed and it gives you an error, just delete it from your Applications folder and run the command again.

4. Install a set of add-ons for Atom that make writing XML much easier:

    ```shell
    apm install linter-autocomplete-jing atom-wrap-in-tag double-tag tag atom-beautify linter linter-ui-default intentions busy-signal
    ```

You will find Atom in your Applications folder.

## Installing Atom with a Web browser (Mac/Windows)

To install Atom together with its packages for writing XML using a Web browser:

1. Download [Atom](https://atom.io) and install it. For more detailed instructions, see [Installing Atom](https://flight-manual.atom.io/getting-started/sections/installing-atom/).

2. Download [Java](https://java.com/download/) and run the installer. If you see any offers to install extra, unrelated software, be sure to decline these.

3. Open Atom, either from your Applications folder (Mac) or Start menu (Windows).

4. When you open Atom for the first time, you'll see a Welcome Guide. Click on the 'Install a Package' button. If it didn't appear when you opened Atom, go to the Packages > Settings View > Install Packages/Themes menu option.

5. In the Install Packages window, search for each of the following packages and install them:
    
    - [`linter-autocomplete-jing`](https://atom.io/packages/linter-autocomplete-jing): Validates a XML file as you work and notifies you of any errors.
    - [`atom-beautify`](https://atom.io/packages/atom-beautify): Provides an option to reformat an XML file.
    - [`atom-wrap-in-tag`](https://atom.io/packages/atom-wrap-in-tag): Lets you select a word and use the Alt + Shift + W shortcut to add an XML tag.
    - [`double-tag`](https://atom.io/packages/double-tag): Renames matching tags when you edit one.
    - [`tag`](https://atom.io/packages/tag): Shortcuts for closing an XML tag.

## Get started with Atom

Atom is useful for working not just with XML but any plain-text file, meaning that there is a large community around it, and many introductions to using it:

- The official [Atom Basics](https://flight-manual.atom.io/getting-started/sections/atom-basics/) guide;
- [*Learn Enough Text Editor to Be Dangerous*](https://www.learnenough.com/text-editor-tutorial), a slightly more advanced overview of how text editors work;
- [*The Sweet Setup* review of Atom](https://thesweetsetup.com/apps/best-text-editor-macos/) and other text editors.

The Atom community has produced many packages that give the editor extra functionality. For example, [Teletype for Atom](https://teletype.atom.io) allows multiple people to collaborate on a file over the Internet.

If you find that there are long TEI tags that you keep writing out (such as a critical apparatus), you can set up [snippets](https://flight-manual.atom.io/using-atom/sections/snippets/) in Atom to save you the typing. For a more user-friendly solution that works anywhere on your computer, [TextExpander](https://textexpander.com/) allows you to write small forms for a particular project (for example, I often set up snippets that allow me to fill in textual variants from standard manuscripts).

Once you're ready to start writing TEI, [*What is the Text Encoding Initiative?*](http://books.openedition.org/oep/426) is a good place to start. If you're working with premodern sources, you might begin with [EpiDoc](http://epidoc.sourceforge.net), which is provides examples of how to transcribe manuscripts and inscriptions on its website. The [Digital Latin Library Guidelines](https://digitallatin.github.io/guidelines/) gives an overview of using TEI for critical editions.
