---
layout: page
title: Asset Customization
permalink: /internal/dev/asset-customization
parent: Developers
grand_parent: Internal Documentation
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
|Outfit|`#AC3CA0`|`#AC3CA1`\*|`#AC3CA2`\*|`#AC3CA3`\*|_Purple_|
|Outfit Dark|`#AC2CA0`|`#AC2CA1`\*|`#AC2CA2`\*|`#AC2CA3`\*||
||`#3CAC30`\*|`#3CAC31`\*|`#3CAC32`\*|`#3CAC33`\*|_Green_|
||`#3CACA0`\*|`#3CACA1`\*|`#3CACA2`\*|`#3CACA3`\*|_Teal_|

\* Unused color.

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

## Implementation Details

To support customization, the publishing script performs find and replace operations on the `.js` exported by Adobe Animate.

Each customizable asset has a _palette_ object defined in the global array `assetPalettes`. Feature selection is achieved by prepending `if` statements to layers such that they may be toggled with the palette. Color selections are achieved by replacing reserved color codes colors in the palette.

Customizable layers must begin with `slot` followed by the slot number (e.g. `slot0figure0hair3`).

### Palette Object

For each customizable actor (any that uses a reserved color code), a palette object must be defined in the global `assetPalettes` array. This palette may be loaded from the URL parameters (passed by the avatar customizer) or it may be preset in the manifest. Palettes that are not defined will use the default colors.

```javascript
window.assetPalettes[slot] = {
    colors: {
        0:   "#663300",
        1:   "#663300",
        2:   "#E5CCFF",
        3:   "#FFCC99",
        4:   "#000000",
        5:   "#000000"
    },
    // colorsDark generated by simulation code.
    features: {
        eyes: 0,
        hair: 0,
        figure: 0
    }
};
```

### Color Mappings

Six color slots are assumed, alternating RGB such that each color is distinct. Any occurences of these colors in the published `.js` will be replaced with the corresponding reference to `assetPalettes[slot].colors[i]`.

```javascript
{
     '#3C3CA0': 0,    // Eye    #33A
     '#3CAC30': 1,    //        #3A3
     '#3CACA0': 2,    //        #3AA
     '#AC3C30': 3,    // Hair   #A33
     '#AC3CA0': 4,    // Outfit #A3A
     '#ACAC30': 5     // Skin   #AA3

     // Following this pattern, we should also have #333 and #AAA.
     // These colors have been omitted as they are both grey and more difficult to find visually.
}
```

Dark versions of these colors (or six additional colors) are denoted by a decrement of the most significant digit of the second byte.

```javascript
{
     '#3C2CA0': 0,    // Eye    #32A
     '#3C9C30': 1,    //        #393
     '#3C9CA0': 2,    //        #39A
     '#AC2C30': 3,    // Hair   #A23
     '#AC2CA0': 4,    // Outfit #A2A
     '#AC9C30': 5     // Skin   #A93
}
```

# Advanced Asset Customization

The avatar is not the only customizable asset. Other assets which utilize customization slots may be modified from the researcher console. This allows for manipulations such as of the gender of the defense attorney or the day/night animation in the jail scene.

Customizations to the avatar, or whichever asset occupies customization slot `#0`, may be specified in the URL of the simulation. URL query parameters override any configured customizations. Configured customizations further override the default customizations.

An asset's configuration object is its `palette`. When the simulation loads, an array of default palettes is defined, providing a default appearance to the customizable actors (e.g. male, dark hair, etc.). Elements of this array (customization slots) may be overwritten by any palettes defined in the simulation's `manifest.json` (generated by the console).

```javascript
manifest = {
	name: "Example scenario.",
	description: "Demonstrating asset customization.",
	// ...
	customizable_presets: {
		// Slot 1 (Default slot of the Judge asset)
		1: {
			colors: {
				0: "#663300",
				// ...
			},
			features: {
				eyes: 0,
				// ...
			}
		}
	},
	// ...
}
```

The researcher console stores a set of customizations per condition. The following format is used by the server:

```javascript
{
  assets: {
  ["5fb97ada07387114aa21678d"]: {
    _id: ObjectId("5fc67a90fc93bac2bfd470c9"),
    description: "",
    public: true,
    readOnly: false,
    version: "1.0.0",
    owner: ObjectId("5fb7d9558816d632bfe27d56"),
    author: ObjectId("5fb7d9558816d632bfe27d56"),
    path: "actor/AllScenarios_Jail.js",
    name: "AllScenarios_Jail",
    type: "actor",
    customizables: [

    /**** Colorables ****/
    {
      name: "Color 3 (Hair)",
      slot: 0,
      type: "color",
      color: 3 // color sub-slot number
    },  // e.g. assetPalettes[0].colors[3] = "#efefef";
    {
      name: "Color 5 (Skin)",
      slot: 0,
      type: "color",
      color: 5
    },
    {
      name: "Color 4 (Outfit)",
      slot: 0,
      type: "color",
      color: 4
    },

    /**** Features ****/
    {
      name: "figure",
      slot: 0,
      type: "feature",
      range: 2 // figure 0 or 1
    }, // e.g. assetPalettes[0].features.figure = 1;
    {
      name: "hair",
      slot: 0,
      type: "feature",
      range: 4 // hairstyle 0, 1, 2, or 3
    }, // e.g. assetPalettes[0].features.hair = 3;

    /**** Toggleable Layers ****/
    // Custom layers like the animated day night cycle
    // Display as a boolean switch (isVisible)
    {
      name: 'daynightanimation',
      slot: 0,
      type: 'toggle',
      layer: 'daynightanimation'
    },

    /**** Numbered Layers ****/
    // Custom layers like the static day/static night
    // Allows for more than just one boolean, layers are selected
    // by enum like the feature layers are.
    {
      name: "layer",
      slot: 4,
      type: "numbered",
      layer: "layer",
      range: 2   // layer0, layer1
    }
    ],
    created: ISODate("2020-12-01T17:17:04.745Z"),
    modified: ISODate("2020-12-01T17:17:04.745Z"),
    __v: 0
  }
  ,

  ...getAssetsServerResponse,
  }
```

