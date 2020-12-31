---
layout: page
title: Introduction
permalink: /internal/introduction
nav_order: 1
parent: Developers
---

# Introduction to the Plea Bargain Simulation

## Clips

Clip scenes are composed of fully pre-made movie animations. These scenes do not include custom scripts. Clips may be exported from Adobe Animate, uploaded, and played as-is.

### Avatar Clips

Clip scenes may include the participant's avatar. The avatar is composed of multiple layers, all of which must be enabled on export from Animate.
These layers will later be toggled on or off automatically depending on the participant's selection.

The avatar uses certain colors exclusively. These special colors will be replaced automatically depending on the participant's selection.
These colors are reserved and must not be used elsewhere.


The base layer of the avatar is the figure. Figures are the body shape options available to the participant.
There are currently two figure layer options, a stereotypical male and stereotypical female figure.

Several feature layers are overlayed on the figure layers. These include options for hair style and eye shape.

## Dialogues

Dialogue scenes are composed of an actor and script with the option of foreground or background images. Actors are assets representing a single, stationary character. Actors read the lines of script defined in the dialogue.

Scripts are limited to 120 characters. If the intended script is too long for one scene, the script can be split into multiple dialogue scenes with the same actor continuing the script.

Actor assets include a mouth layer with a timeline composed of nine frames. This enables the actor's mouth to move as he or she speaks. The first of these frames must be a closed mouth.

| Timeline Frame | Viseme |
| - | --- |
| 1 | Closed |
| 2 | A/I |
| 3 | Consonant |
| 4 | E |
| 5 | M/B |
| 6 | O |
| 7 | L |
| 8 | Slight Open |
| 9 | U |
