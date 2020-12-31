---
layout: page
title: Testing And Debugging
permalink: /internal/dev/testing-and-debugging
parent: Developers
grand_parent: Internal Documentation
---
# Testing & Debugging

This is the testing/debugging page: a page that will continuously get updated as each programmer, developer, and contributor of the likes give their own input on how the software can be tested. Anything useful pertaining to testing and debugging should be found on this page, and if something is missing here then it should be noted.

***

## The *pleabargains/tests* folder

This folder contains bits and pieces of the simulation final product. The folder is essentially treated as a sandbox to show some of the development process of how some elements are created. There are .html, .js, and .fla files in the directory.

If one were to tinker around with these files, you can simply just click a particular file, click the three dots on the right side of the screen (...), right-click "Open Raw", and save the link as an html. Once the interested files are saved, the html file can be opened in a browser. Some content in the folder involves the testing text parsing, text animations, and mouth animations.

***

## Testing Guidelines

The links of specific variations of the simulation is found at the bottom of the page. When testing, there are a few things to look out for. Common issues with the simulation involve spelling errors, text formatting, or palettization color errors.

The experiment's flow is broken up into 4 phrases (this is different from how the software is described). These 4 phases each can have their own bugs and require analysis to verify each of their functionalities:

- The participant consent form
- The avatar customization
- The animated simulation
- The post-simulation survey

### 1. The avatar customization

The avatar customization is comprised of buttons and color palettes used to configure the features of the participant's avatar. When making contributions to and debugging this feature, some things to consider are:

- Do the buttons function? Are there any types of unexpected behavior?
- Is this phase functional across different platforms? Note the browser, operating system, and device type (laptop, mobile)
- Are you able to navigate freely throughout the menu? re-selecting any feature you would like to make changes to? Can you reach the animation simulation phase of the experiment from here?

### 2. The animated simulation

The animated simulation is the bread-and-butter of the experiment. This can be broken up further: the avatar, the link, the scenarios, the text and the script.

### 3. The participant consent form and post-simulation survey

The participant consent form and post-simulation survey are forms hosted by Qualtrics that can carry embedded data across the simulation through passing it in the URL.

***

## Running the code locally

There are a few ways to run the simulation locally:

1. You can clone it with git and switching to a particular branch you wish to test on.
2. You can use http-server (command-line http server) or any web server to run the code.
3. Use [this short video tutorial](https://youtu.be/qMUS1JJcR-A) to run the code without using git or the command line.

***

## Adobe Animate Publishing to JS
Due to changes made by Adobe to the syntax of this output in the middle of development, the modules/assets/publishing-scripts/add-lib.sh is needed to translate the new published js to the more legacy compatible format. In case that ever fails, here is a snippet from the old readme about more manual things to try:

> There are changes which must be made to the tail end of any such assets in order to match expectations of the **engine**. These changes are minimal, and consist of altering the syntax of boilerplate class properties and methods found at the end of the file to conform to the syntax of existing assets. See existing Movie Clips such as *prologue.js* for a practical example of expected syntax.

***

## Qualtrics Links

### Demo server for testing latest changes

1. [Hit & Run](https://umasslowell.co1.qualtrics.com/jfe/form/SV_eCzRrXXeDTl3tKB)
2. Shoplifting
3. [Both scenarios](https://umasslowell.co1.qualtrics.com/jfe/form/SV_25DlciTSNf0F5nn)
  - Username: test
  - Email: test@student.uml.edu

### Live.pleajustice.org server for actual experiments

1. [Hit & Run](https://umasslowell.co1.qualtrics.com/jfe/form/SV_3vKHaUSDeJcxxKl)
2. n/a Shoplifting only (don't need this on live as no experiment with shoplifting only was/is being done)
3. [Both scenarios](https://umasslowell.co1.qualtrics.com/jfe/form/SV_3XfsZqMTudTGZql)
  - Username: test
  - Email: test@student.uml.edu

### DEPRECATED justice.misharabinovich.com server for actual experiments
1. [Hit & Run](https://umasslowell.co1.qualtrics.com/jfe/form/SV_eE880no2AvUoRQV)
2. Shoplifting
3. [Both scenarios](https://umasslowell.co1.qualtrics.com/jfe/form/SV_1ZgWdnbRrtFLPdr)
  - Username: test
  - Email: test@student.uml.edu

[Bypass Qualtrics, go direct to Avatar Customization on Demo](http://demo.pleajustice.org/src/avatar_creation.html?ID=95327970&Name=m&module=0&Locale=en_US&S=bip&email=m@student.uml.edu&modcounter=1&SURL=https://umasslowell.co1.qualtrics.com/jfe/form/SV_25DlciTSNf0F5nn&skinA=&skinB=&hairA=&hairB=&eyeA=&eyeB=&outfitA=&outfitB=&avatarSex=&avatarNum=)

(**NOTE**: This is an outdated parameter convention, but in the URL: `bop` means guilty, `bip` means not guilty. Swap them in the URL and reload to test guilt variation of scenarios.)
