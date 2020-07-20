---
layout: page
title: Art Documentation
permalink: /simulation/docs/art-documentation
parent: Simulation
---
# Adobe Animate File Naming Conventions

All animation assets are stored in the [simulation-assets](https://github.com/Plea-Justice/simulation-assets) repository on GitHub. Backup copies are stored on Google Drive. Always make sure you're working with the latest version of an asset `.fla` and always back up files to Drive.

**Layer Names**, however are these agreed upon Condensed files, which have the agreed upon layer naming convention.

## Figures and features are numbered beginning at 0. (i.e. 0, 1, 2...)

**figure0** is the new name for our **stereotypically male-looking figure**

**figure1** is the new name for our **stereotypically female-looking figure**

Going forward, the next figure we add should be named figure2 (later, figure3 and so on).

Feature layers must be named similarly. For example:

**figure0hair0** is the first hair style on figure0 and **figure1eyes3** is the third eye option on figure1.


## **"Condensed" Files (NOTE: Underscores in file names)**
### Convention: [Scenario Name]_[Type of Scene]**_**Figure[Number]
### Needed files:


### Scenario 1 File Names

* Scenario1**_**Intro**_**Figure0.fla
* Scenario1**_**Intro**_**Figure1.fla
* Scenario1**_**FlashbackGuilty**_**Figure0.fla
* Scenario1**_**FlashbackGuilty**_**Figure1.fla
* Scenario1**_**FlashbackInnocent**_**Figure0.fla
* Scenario1**_**FlashbackInnocent**_**Figure1.fla
* Scenario1**_**SecurityFootage**_**AllFigures.fla

**Developer Publishing NOTE:** Scenario1_SecurityFootage_AllFigures.fla doesn't need to be palettized, or have feature versions generated. It just needs to have the var lib definition updated manually using [add-lib.sh](https://github.com/Plea-Justice/pleabargain-simulation/wiki/Palettization%20Guide#add-lib)

### Scenario 2 File Names

* Scenario2**_**Intro**_**Figure0.fla
* Scenario2**_**Intro**_**Figure1.fla
* Scenario2**_**FlashbackGuilty**_**Figure0.fla
* Scenario2**_**FlashbackGuilty**_**Figure1.fla
* Scenario2**_**FlashbackInnocent**_**Figure0.fla
* Scenario2**_**FlashbackInnocent**_**Figure1.fla
* Scenario2**_**SecurityCam**_**Figure0.fla
* Scenario2**_**SecurityCam**_**Figure1.fla

### For all Scenarios

* AllScenarios**_**Jail_Figure0.fla
* AllScenarios**_**Jail_Figure1.fla


### Layer Names (use whatever folder organization you want, layers have to be named these:)
## Note: figure[Number] is the layer name for the avatar figure itself

* figure0avatar
* figure0hair0
* figure0hair1
* figure0hair2
* figure0hair3 (NOTE: This is religious headwear)
* figure0eyes0
* figure0eyes1
* figure0eyes2

### In your other fla file

* figure1avatar
* figure1hair0
* figure1hair1
* figure1hair2
* figure0hair3 (NOTE: This is religious headwear)
* figure1eyes0
* figure1eyes1
* figure1eyes2

### In the screenshot below, the Animator chose a nice layer folder organization as she saw fit. The only important thing is the layer names (order of layers doesn't matter), not anything to do with what folders they are in or whatever

<img src="/img/file_names.png">

## Other Guidelines

Every file created is created as a **Full HD** **1920 x 1080** file. This is every asset, including actors.

Every file must be created as an **HTML5 Canvas file** in **Adobe Animate**. Make sure to set Basic and Advanced Publishing Settings like so: Basic (nothing checked), HTML/JS: Overwrite, Hosted Libraries, Compact Shapes. **Under these settings, hidden layers WILL NOT be published, just fyi.**

<img src="/img/file_settings1.png">

<img src="/img/file_settings2.png">

Don't rely on stage color to produce a background. Stage color is omitted in publishing by Animate. If a background color is needed, such as a solid yellow background for Scenario2_Intro_Figure0 (or 1).fla, create an explicit background layer with the rectangle shape taking up full stage and color it.

Use Classic Tweens in Adobe Animate where possible. Any animated figure should be a Graphic symbol with a minimal walk cycle. Moving the animated figure across the stage should be done with time-saving Classic Tween whenever possible (vs. frame-by-frame animation).

Take care to backup your working fla files on your own backup drive as well as on the shared drive. When uploading files, please do it under your own unique user and not as a shared user so contributions can be properly attributed. In other words, don't log into drive as the admin@pleajustice.org user to upload. Upload your 'condensed' files as described in Deliverables above to their appropriate folders and **overwrite** the old files with the same name. Google Drive will ask if you want to overwrite or keep version separate, you **do not** want to keep them separate. We can always go back to an old version with 'Manage Versions'.

## Workflow

In general, the art assets that an animator would work on for this project are as follows:
* Custom avatars and their features (hair styles, eyes, etc.)
* Animated clips that show some action like a crime or flashback
* Backgrounds: sometimes we need to export the setting from Adobe Animate as a raster background image like in the Courtroom scenes. In the future these need to be vector js as well to maintain a responsive user experience.
* Drawn text for narration scenes: text that is rasterized aka "broken" and baked into an image or clip.

Keeping in mind when and how to report to supervisors is important. This is also a general summary of the entire process from start to finish:

* Create Concept Art
  * Think of what you are creating and why. Are you creating a defense attorney? Do you want them to seem incredibly competent, overworked? These things will be factors, potentially, in the research results. Come up with several variations before moving on.
* Respond to feedback, change designs according to Supervisor feedback.
* Once designs are approved, **storyboarding must be done** to get into full swing. Reference the script a lot during this portion of the process. During this process there should be at least 2 reviews of the storyboards so that the full intent of the script can be properly conveyed *before* animating begins.
* Once the storyboards are finalized, as well as the concept art, you begin by creating a rough draft animation. This can be several layers, but keeping them rough and minimal is preferred. Once again, this process should have at least 2 revisions in order to assure quality of work, optimal script cohesion, and style matching.
* The rough approval ends the beginning work for the animation, but it doesn’t end the need for style matching guidance. Refer to style guides (do we have these?) and have supervisors provide regular feedback on the assets.
* As you move on to the final version, regularly uploading and publishing videos to Google Drive / Documentation / Animation Review for regular online review by supervisors is a must. The final animation needs to be matching in style, have believable motion, and follow the script in a way that promotes the quality of research your supervisor needs.

## Actors

Each Actor (such as the customizable avatar) when created should be centered in the middle of the screen. The current issue with actors is we’re unsure if programmers can move them around. This is something we should try to fix in future versions. As of now the Judge is to the left, the prosecutor is to the right, and the user avatars stray towards the middle. The figures should ideally never be on the screen at the same time or this issue might come to a head. In order to avoid complications, just place new actors in the center.

Each actor should have style matching to the currently existing assets, or they will potentially disrupt the immersion of the experience, which is important to the research. This is up to the discretion of individual supervisors.

Each actor has a list of mouth flaps, here is the list as a set:

* ai = { a, A, i, I, h, H }
* e = { e, E }
* o = { o, O }
* mb = { m, M, b, B }
* l = { l, L }
* u = { u, U, w, W, y, Y }

Each mouth flap needs to be set according to this.

## Scenes

Most assets created in Animate will be manually published out of Adobe Animate as a .js javascript file. The published animations are in a vector format (asset scales in a lossless state according to the dimensions it is being viewed or rendered at). Some assets will be raster images (mainly used for backgrounds).

## Performance

Layer Organization is important. Organize layers in layer folders in Adobe Animate to make the project straightforward to understand by another team member.

Help keep the published js files smaller in size by using walk cycle loops, tweening animations whenever possible, simplifying shapes, merging background layers (anything thats not in the key layers discussed above such as figure0hair0, etc.) into one layer **while making sure everything is still editable** (use grouping or converting things into symbols (or movie clips, but I think symbols are slightly lighter weight) so they can be edited later). Use this [Adobe guide](https://helpx.adobe.com/animate/using/best-practices-optimizing-fla-files.html) on optimizing the animations.


## Final Notes:
Refer to [palettization guide](https://github.com/Plea-Justice/pleabargain-simulation/wiki/Palettization%20Guide) for skin tones, eye colors, and hair colors.
Follow a naming guide.
Layer your assets in every file with proper layer names, and properly label files (as described at the start of this page).
Make regular commits, upload and export regular video updates.
BACKUP your work on Google Drive regularly.
