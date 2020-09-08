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

These colors are **reserved** to allow the color customization of the avatar and actors. They will be replaced automatically by the simulation at the participant or researcher's selection. Colors are organized into slots, a number associated with the actor, to allow new customizable actors to be added in the future.

**Do not use these colors anywhere other than in the assets they are associated with.**

<img src="/img/palettization.png">

Copy and paste the color codes exactly as they are below. The eyedropper tool does not accurately find the exact color code. Animate supports [find and replace for colors](https://helpx.adobe.com/au/animate/using/find-replace.html#find_and_replace_colors) if you ever need to quickly modify many colors at a time.

 _Search for each of these colors in each file before you filling to ensure they aren’t already used somewhere._

||Avatar|Judge|Defense Att.|Prosecutor||
|-|:-:|:-:|:-:|:-:|-|
|_Slot #_|_0_|_1_|_2_|_3_||
|Skin|`#ACAC30`|`#ACAC31`|`#ACAC32`|`#ACAC33`|_Yellow_|
|Skin Dark|`#AC9C30`|`#AC9C31`|`#AC9C32`|`#AC9C33`||
|Hair|`#AC3C30`|`#AC3C31`|`#AC3C32`|`#AC3C33`|_Red_|
|Eye|`#3C3CA0`|`#3C3CA1`|`#3C3CA2`|`#3C3CA3`|_Blue_|
|Outfit|`#AC3CA0`|`#AC3CA1`|`#AC3CA2`|`#AC3CA3`|_Purple_|
|Outfit Dark|`#AC2CA0`|`#AC2CA1`|`#AC2CA2`|`#AC2CA3`||
|Unused|`#3CAC30`|`#3CAC31`|`#3CAC32`|`#3CAC33`|_Green_|
|Unused|`#3CACA0`|`#3CACA1`|`#3CACA2`|`#3CACA3`|_Teal_|

## Asset Layer Names

The avatar and actors are composed of multiple layers, __all of which must be enabled when exporting from Animate__. They will later be automatically toggled on or off depending on the participant and/or researcher's selection. These layers must also follow a strict naming convention.

Firstly, actors are referenced with numbers called 'slots'. All actor layers must be prefixed with `slot` followed by their number. For example, the avatar is number 0, so all the avatar's layers begin with `slot0` like `slot0figure1base`.

The base layer of each avatar or actor is the `figure`. This is the body shape of the character. The simulation currently supports two figures, a stereotypical male and a stereotypical female shape. Base layers must be named with the figure number and the actor they are applicable to. For example, `slot1figure0base` and `slot1figure1base` are the two figure options available for the judge asset.

Several feature layers may be overlayed on the figure layers. These include options for hair style and eye shape. These layers must be named with the figure they are applicable to. For example, `slot0figure0hair0` or `slot0figure1eyes2` are the first hairstyle of the masculine avatar and the third eye shape available for the feminine avatar respectively.

The table below lists layers which currently exist.

|Avatar|Judge|Defense Att.|Prosecutor|
|-|-|-|-|
|_Slot 0_|_Slot 1_|_Slot 2_|_Slot 3_|
|`slot0figure0base`|`slot1figure0base`|`slot2figure0base`|`slot3figure0base`|
|`slot0figure0hair0`||||
|`slot0figure0hair1`||||
|`slot0figure0hair2`||||
|`slot0figure0hair3`||||
|`slot0figure0eyes0`||||
|`slot0figure0eyes1`||||
|`slot0figure0eyes2`||||
|`slot0figure0accessory0`||||
|`slot0figure1base`|`slot1figure1base`|`slot2figure1base`|`slot3figure1base`|
|`slot0figure1hair0`||||
|`slot0figure1hair1`||||
|`slot0figure1hair2`||||
|`slot0figure1hair3`||||
|`slot0figure1eyes0`||||
|`slot0figure1eyes1`||||
|`slot0figure1eyes2`||||
|`slot0figure1accessory0`||||

These layers may be organized into any desired folder organization as long as the layers themselves have these names _exactly_, without spaces or capitalization.