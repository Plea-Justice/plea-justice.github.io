---
layout: page
title: Palettization Guide
permalink: /simulation/docs/palattization-guide
parent: Simulation
---
# Palettization Guide

## Avatar Palette

These colors are **RESERVED** to allow the avatar customization to work.
**Do not use these colors for anything else.**

<img src="/img/palettization.png">

| Feature   | Reserved color |
| --------|---------|
| hairA  | #663300   |
| eyeA | #666600 |
| skinA | #FFCC99 |
| skinB | #F49E50 |
| outfitA | #E5CCFF |
| outfitB | #70618D |

The palettization script searches for these reserved colors within the exported `.js` file. It then replaces these reserved colors with variables. When a participant selects a color for hair, eyes, skin or outfit, the corresponding variable adapts to the color that was selected.

* These colors should be used to color the avatar.
* These specific colors should not be used anywhere else.

## Publishing Script

As of May 22, 2020, the publishing script works with Adobe Animate 20.0.4. Video Tutorial: [https://youtu.be/Kt7Pdozg-H8](https://youtu.be/Kt7Pdozg-H8) *Not up to date.*

The publishing script is a small computer program written in Python which modifies the `.js` files exported by Adobe Animate such that they may be added to the simulation. Before running the script, make sure Animate layers follow the required [naming convention][/simulation/docs/art-documentation] as well as the above color palette rules.

To run the publishing script you will need [Python 3](https://www.python.org/) installed. The script may be found at `src/modules/assets/publishing-scripts/publish.py`. Run the publishing script in a terminal (command-line) with the following commands.
```
cd src/modules/assets/publishing-scripts/

python publish.py [filename]
```
Example:

```
python publish.py AllScenarios_Jail.js
```

In this case, `AllScenarios_Jail.fla` has been exported from Adobe Animate as `AllScenarios_Jail.js` this file has then been moved to the same directory as the publishing script. The publishing script has now been run, and we may now use `AllScenarios_Jail.js` as a scene in the simulation.

### Technical Details

Adobe Animate exports `.fla` animations as JavaScript objects that may be rendered in a browser with the [CreateJs](https://createjs.com/) library. The `.js` output of Animate requires modifications before it can be used with the simulation.

The publishing script does several things:

* Replaces the reserved palette colors to JavaScript variable names so they can be set dynamically based on the participants' avatar customizations.
* Prepends `if` statements to avatar feature layers (eyes, hair), allowing them to be similarly toggled on and off with variables.
* Prepends `if` statements to all avatar layers associated with a figure to allow toggling between body shapes.
* Replaces the `lib` object in which the animation object is stored by Animate with a global `lib`. (An issue introduced by [Animate 17.5](https://community.adobe.com/t5/get-started/download-animate-cc-2017-17-1-or-17-2/td-p/10021673?page=1)).
* Prepends `// Published.` to the beginning of the file and checks for this line before running to ensure the script is never accidentally run more than once.
