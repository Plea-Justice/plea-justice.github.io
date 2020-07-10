---
layout: page
title: Release Schedule
permalink: /simulation/docs/release-schedule
parent: Simulation
---
# Release Schedule #

***

**0.2.0 – August 30th, Testing: August 19th 2019**
* This release will support at least one experiment (randomized scenario order).
* All features available for all avatar figures throughout scenarios.
    * For example, does Figure1 show custom eyes in Scenario 2?
* The live server Qualtrics survey that begins and ends the experiment will have a unique version name & number
    * this unique version name & number will also be added to this wiki to associate it with release v0.2.0
    * All future releases must not break support for this experiment(s)
* Defense attorney on for plea offers (instead of prosecutor)
* All visual asset files will be under version control.
    * Gitlab w/Large File Storage (LFS) free account
* Reduce number of JavaScript animation files by a factor of 9.

***

**0.1.1 – July 29th 2019**
* Refactored application doesn't use separate feature variation files. All animations exist as single js files with eye and hair features that can be made visible or invisible via code (using a conditional if statements to turn features on and off).

***

**0.1.0 – July 1st 2019**
* This release fixes some bugs
* It brings in the female avatar for Scenario 2 shoplifting
* Scenario 2 can only show customized hair in animation (eye adjustments are ignored because current software architecture plus browser gets overloaded when loading complete feature combination files)
* Allows for the running of experiment 3 (both scenarios in one)
* Features automatic publishing of custom avatar feature variation files
* Features automatic palettization
* Features automatic translation of new Adobe Animate format javascript to become compatible with plea justice.

The completed milestone code is tagged in git with [v0.1.0](https://github.com/Plea-Justice/pleabargain-simulation/commits/tag/v0.1.0)
