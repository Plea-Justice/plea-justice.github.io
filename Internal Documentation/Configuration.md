---
layout: page
title: Manual Configuration
permalink: /internal/configuration
nav_order: 4
parent: Internal Documentation
---
_The researcher console now configures interactive simulations automatically. This page is meant for users who wish to directly modify the simulation code._

# Configuring the Simulation
This page explains how to customize the plea bargain simulation to the needs of a particular experiment.

**Jump to:**
* [Necessary Software](/internal/dev/configuration#necessary-software)
* [Downloading the Simulation Software](/internal/dev/configuration#downloading-the-simulation-software)
* [Editing the Script and Rearranging Scenes](/internal/dev/configuration#editing-the-script-and-rearranging-scenes)
* [Adding Buttons to Capture Participant Decisions](/internal/dev/configuration#adding-buttons-to-capture-participant-decisions)
* [Note on Scripts and Special Control Sequences](/internal/dev/configuration#note-on-scripts-and-special-control-sequences)
* [Managing Assets](/internal/dev/configuration#managing-assets)

***
## Necessary Software
For this tutorial:
* **Qualtrics Access**
* **A text editor**
> _The Notepad app on any Windows computer is all you need, however an advanced text editor like [Visual Studio Code](https://code.visualstudio.com/) or [Notepad++](https://notepad-plus-plus.org/) is highly recommended._



***
## Downloading the Simulation Software
The latest version may be retrieved from [the releases page](https://github.com/Plea-Justice/pleabargain-simulation/releases). The file called `Source Code.zip` contains the simulation files. Additionally a Qualtrics survey file (ending in `.qsf`) may be available to import into Qualtrics.

Extract the contents of `Source Code.zip` to an appropriate folder on your computer.

***
## Editing the Script and Rearranging Scenes
Inside the extracted folder, go to `src > modules > experiment`. The files in this folder describe how the simulation will operate for each experimental condition.

The file `condition1.json` may be used as a template for your experimental conditions. Make a copy of it for every experimental condition and name each `condition1.json`, `condition2.json`, `condition3.json`...

Each of these experimental condition files uses a format called JSON. This format is computer readable, the values are typically comma-separated, and you must use correct syntax for the file to be read properly. Most importantly, notice that any parenthesis, quotation marks, brackets or braces must have a matching pair.

Each experimental condition files contains a description of each scene in order.

> ```
> {
>     "condition":{
>         "name":"Experimental Condition 7",
>         "description":"This file describes the outline of experimental condition number 7.",
>         "scenes":[
>
>         A description of each scene goes in here surrounded by { curly braces }.
>
>         ]
>     }
> }
> ```

There are two types of scenes. The first is a premade animation scene. This uses a movie clip and does not contain any dialogue or script.

> ```
> {
>     "name":"Introduction",
>     "clip":"IntroClip0"
> },
> ```
This creates a scene called _Introduction_. The scene will play a premade movie clip asset called _IntroClip0_.

The second type of scene is a custom dialogue scene. This type of scene contains an "actor" animation asset and text from a script that will be rendered dialogue on the screen.

> ```
> {
>     "name":"Prosecutor Says Hello", "actor":"prosecutorActor", "fg":"None", "bg":"meetingroom",
>     "script":"Hello, my name is Mr. Clark."
> },
> ```

Breaking it down,
* `"name":"Prosecutor Says Hello",` gives this scene the name _Prosecutor Says Hello_
* `"actor":"prosecutorActor",` puts the character asset called _prosecutorActor_ in the scene
* `"fg":"None",` and `"bg":"meetingroom",` correspond with images to show in the foreground and background of the scene.
   * _None_ means we don't want to put anything in the foreground.
   * _meetingroom_ uses the image file called `meetingroom.png` as a background image.
* `"script":"Hello, my name is Mr. Clark."` writes text in the dialogue box, "Hello, my name is Mr. Clark."

We can now incorporate the configuration file and the two example scenes described in the previous code blocks and combine them together. Our file will look like the following:

> ```
> {
>     "condition":{
>         "name":"Experimental Condition 7",
>         "description":"This file describes the outline of experimental condition number 7.",
>         "scenes":[
>             {
>                 "name":"Introduction",
>                 "clip":"IntroClip0"
>             },
>             {
>                 "name":"Prosecutor Says Hello", "actor":"prosecutorActor", "fg":"None", "bg":"meetingroom",
>                 "script":"Hello, my name is Mr. Clark."
>             }
>         ]
>     }
> }
> ```

Because this example is experimental condition number 7, the file is named `condition7.json`. If a participant is assigned to condition 7, they will view the premade movie clip animation _IntroClip0_ followed by the custom animation _Prosecutor Says Hello_, in which text appears in the speech box "Hello, my name is Mr. Clark".

With different experimental conditions, the json file will have different parameters such as having a scene removed or replaced, the script having different text, or another variable manipulated.

***

## Adding Buttons to Capture Participant Decisions
Buttons may be added to custom animation scenes to present a choice to the participant and record their selection. A scene with a script just needs to have `"buttons":["Choice1", "Choice2", "Choice3"]` added to the end with as many choices as required. This may have a foreground, background, and actor like any other custom scene, or it may omit these and only have a script prompting the participant for their choice. The buttons will be placed in the middle of the screen in the order listed.
> ```
> {
>     "name":"Participant Chooses How to Plea",
>     "script":"Based on this information, will you accept the plea deal offered?",
>     "buttons":["Accept", "Reject"]
> }
> ```

***

## Note on Scripts and Special Control Sequences
The actor assets contain versions of the actor for the mouth shapes (visemes) required to say different sounds. As the actor says a line of script, their mouth will move as if they were speaking. In addition to this functionality, there are special control sequences that may be added to the script to change how the actor says their line and how text appears on the screen.

There are two types of control sequences which consist of an `@` symbol followed by a character.

1. The first type sequence `@` followed by a number between 1 and 9 inserts a pause into the actors speech. These pauses allows for the text to rasterize onto the screen in a more natural pace, similar to someone actually speaking. A larger number represents a longer pause.
2. The second type sequence `@U` inserts the first name of the participant (only if entered and the name is not recorded) into the actor's line.

For instance, consider this script in an actor scene:

>```
> {
>     "name":"Control Seq. Demo", "actor":"daActor", "fg":"None", "bg":"None",
>     "script":"Hello @U, @3my name is Mr. Clark. @7I hope you are well!"
> },
>```

This code block will reference the defense attorney actor and show the _daActor_ asset on the screen. If the participant enters their first name as Jessica, then text will appear under the defense attorney, "Hello Jessica, \*short pause\* my name is Mr. Clark. \*longer pause\* I hope you are well!"

***

## Managing Assets
**Note: The bottom of this section notes how to set the link to the Qualtrics URL.**

The simulation comes with all the movie clip and actor animation assets as well as foreground and background images needed for running basic experiments based on the original plea bargaining simulation. The following assets are already included:

|Actors|Movie Clips|Fg/Bg Images|
|---|---|---|
|prosecutorActor|Scenario1_Intro_Figure0|blankjail|
|judgeActor|Scenario1_Intro_Figure1|courtrooom|
|daActor|Scenario1_FlashbackGuilty_Figure0|courtroom_2019|
||Scenario1_FlashbackGuilty_Figure1|judgecourtroom|
||Scenario1_FlashbackInnocent_Figure0|JudgeSeat|
||Scenario1_FlashbackInnocent_Figure1|meetingroom|
||AllScenarios_Jail_Figure0|plainwhite|
||AllScenarios_Jail_Figure1|table|
||Scenario1_SecurityFootage_AllFigures||

These assets are declared in `src > modules > experiment` in the file called `manifest.json`. If you are adding any new assets to the simulation, you will use this file to tell the program where the assets are and what they are named. The asset files themselves are actually stored in various folders under `modules > assets`. Below is an example of what `manifest.json` might look like.

> ```
> {
>     "path":"modules/assets/",
>     "manifest":[
>         "actors/prosecutor.js",
>         "actors/defenseattorney.js",
>         "actors/judge.js",
>         "clips/Scenario1_Intro_Figure0.js",
>         "clips/Scenario1_Intro_Figure1.js",
>         ...
>         "scenes/backgrounds/meetingroom.png",
>         "scenes/foregrounds/table.png"
>     ],
>     "actors":[
>         "prosecutorActor",
>         "judgeActor",
>         "daActor"
>     ],
>     "clips":[
>         "Scenario1_Intro_Figure0",
>         "Scenario1_Intro_Figure1",
>         ...
>     ],
>     "survey":"https://umasslowell.co1.qualtrics.com/jfe/preview/SV_elZvxtHoalhCs2V"
> }
> ```

<dl>
 <dt><b>"path":"modules/assets/"</b></dt>
 <dd>- tells the program the main folder all of the assets are stored in. This line shouldn't be changed unless the assets are located in a different folder.</dd>
 <dt><b>"manifest":[`  ...  `]</b></dt>
 <dd>- is a list of all of the asset files. This includes actor animations and movie clips ending in `.js` (JavaScript) as well as foreground and background image files ending in `.png`.</dd>
 <dt><b>"actors":[`  ...  `]</b></dt>
 <dd>- and `"clips":[`  ...  `],` tell the program what each movie clip and animation is called internally (the file name might be different than the name in Adobe Animate).</dd>
 <dt>Finally, <b>"survey":"`  ...  `"</b></dt>
 <dd><b>tells the simulation the URL of the Qualtrics survey to bring the participant to when the simulation has completed.</b></dd>
</dl>
