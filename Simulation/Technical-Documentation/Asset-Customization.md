---
layout: page
title: Asset Customization
permalink: /simulation/docs/asset-customization
parent: Technical Documentation
grand_parent: Simulation
---
# Asset Customization

The simulation enables assets to be configured at runtime to allow the participant to customize the avatar and for researchers to manipulate the actors.

Internally, this is accomplished with modifications to the JavaScript exported by Adobe Animate to control the visibility of different layers and to dynamically change a specific set of reserved colors. These modifications are performed automatically when an asset is uploaded to the [researcher console](/console).

## Reserved Color Palettes

These colors are **reserved** to allow the color customization of the avatar and actors. They will be replaced automatically by the simulation at the participant or researcher's selection.

**Do not use these colors anywhere other than in the assets they are associated with.**

<img src="/img/palettization.png">

Copy and paste the color codes exactly as they are below. The eyedropper tool does not accurately find the exact color code.

#### Slot 1 - Avatar Reserved Colors

Use these colors only on the avatar figure, hair, and eye layers. These colors are __always__ reserved for the avatar only.

| Feature | Color Code |
| --- | --- |
| Eye | #666600 |
| Hair | #663300 |
| Skin | #FFCC99 |
| Skin Shadow | #F49E50 |
| Outfit | #E5CCFF |
| Outfit Shadow | #70618D |

#### Slot 2 - Judge Reserved Colors

Use these colors only on the layers of the judge actor. If you are not using the judge, you may use this color slot for a new customizable character.

| Feature | Color Code |
| --- | --- |
| Hair | #999999 |
| Skin | #FFF9CE |
| Skin Shadow | #FFC889 |

#### Slot 3 - Defense Attorney Reserved Colors

Use these colors only on the layers of the defense attorney actor. If you are not using the defense attorney, you may use this color slot for a new customizable character.

| Feature | Color Code |
| --- | --- |
| Hair | #5B3607 |
| Skin | #F3D0A5 |
| Skin Shadow | #F3C18D |

#### Slot 4 - Prosecutor Reserved Colors

Use these colors only on the layers of the prosecutor actor. If you are not using the prosecutor, you may use this color slot for a new customizable character.

| Feature | Color Code |
| --- | --- |
| Hair | #666666 |
| Skin | #FFC9A5 |
| Skin Shadow | #FFBB91 |

 Animate supports [find and replace for colors](https://helpx.adobe.com/au/animate/using/find-replace.html#find_and_replace_colors) if you ever need to quickly modify many colors at a time.

## Asset Feature Layers

The avatar and actors are composed of multiple layers, __all of which must be enabled when exporting from Animate__. They will later be automatically toggled on or off depending on the participant and/or researcher's selection. These layers must also follow a strict naming convention.

The base layer of each avatar or actor is the `figure`. This is the body shape of the character. The simulation currently supports two figures, a stereotypical male and a stereotypical female shape. Figure layers must be named with the figure number and the actor they are applicable to. For example: `figure0base` or `figure1base`.

Several feature layers are overlayed on each of the figure layers. These include options for hair style and eye shape. These layers must be named with the figure they are applicable to. For example `figure0hair0` or `figure1eyes2`.

The following is a list of the currently existing avatar layers.

* `figure0base`
* `figure0hair0`
* `figure0hair1`
* `figure0hair2`
* `figure0hair3` (Religious headwear)
* `figure0eyes0`
* `figure0eyes1`
* `figure0eyes2`
* `figure0accessory0` (Larceny FlashbackGuilty Glasses)

* `figure1base`
* `figure1hair0`
* `figure1hair1`
* `figure1hair2`
* `figure0hair3` (Religious headwear)
* `figure1eyes0`
* `figure1eyes1`
* `figure1eyes2`
* `figure1accessory0` (Larceny FlashbackGuilty Glasses)

The other actors only implement figure customization and so currently only contain the figure base layers.

* `figure0base`
* `figure1base`

These layers may be organized into any desired folder organization as long as the layers themselves have these names _exactly_, without spaces or capitalization.

## Publishing Script

As of July 20, 2020, the publishing script works with Adobe Animate 20.0.5.

The publishing script is a small computer program written in JavaScript which modifies the `.js` files exported by Adobe Animate such that they may be added to the simulation. Before running the script, make sure Animate layers follow the required [naming convention](/simulation/docs/art-documentation) as well as the above color palette rules.

To run the publishing script you will need [Node.js](https://nodejs.org/en/) installed. The script may be found at [`src/modules/assets/publishing-scripts/publish.py`](https://github.com/Plea-Justice/simulation-assets/blob/master/publish.js). Run the publishing script in a terminal (command-line) with the following.

```
node publish.js [options] [filename]
```

Example:

```
node publish.js AllScenarios_Jail.js
```

In this case, `AllScenarios_Jail.fla` has been exported from Adobe Animate as `AllScenarios_Jail.js` this file has then been moved to the same directory as the publishing script. The publishing script has now been run, and we may now use `AllScenarios_Jail.js` as a scene in the simulation.

### Technical Details

Adobe Animate exports `.fla` animations as JavaScript objects that may be rendered in a browser with the [CreateJs](https://createjs.com/) library. The `.js` output of Animate requires modifications before it can be used with the simulation.

The publishing script does several things:

* Replaces the reserved palette colors to JavaScript variable names so they can be set dynamically based on the participants' avatar customizations.
* Prepends `if` statements to avatar feature layers (eyes, hair), allowing them to be similarly toggled on and off with variables.
* Prepends `if` statements to all avatar layers associated with a figure to allow toggling between body shapes.
* Prepends `// Published.` to the file and checks for this line before running to ensure the script is never accidentally run more than once.