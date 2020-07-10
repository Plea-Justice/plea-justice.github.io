---
layout: page
title: Source Tree
permalink: /simulation/docs/source-tree
parent: Simulation
---
## Source Tree
<pre>
<b>/src/</b>
├── <b>css/</b>       ----------------------------- CSS Stylesheets
│   ├── <b>bootstrap/</b>                           Bootstrap stylesheet used on index page
│   │   └── <b>4.3.1/</b>
│   │       └── <b>css/</b>
│   │           └── bootstrap.min.css
│   ├── avatar_creation.css                         Styles for avatar creator
│   └── stylesheet.css                              Simulation styles
├── <b>libs/</b>      ----------------------------- Library and simulation package code
│   ├── actor.js
│   ├── avatar_customization.js
│   ├── color_pickers.js
│   ├── createjs-2015.11.26.min.js
│   ├── flow.js
│   ├── init.js
│   ├── new_renderer.js
│   ├── params.js
│   ├── parser.js
│   ├── renderer.js
│   └── ui.js
├── <b>locales/</b>   ----------------------------- Translated strings for prompts in other languages
│   ├── en_US.js                                    U.S. English
│   ├── es_DO.js                                    Domenican Republic Spanish
│   └── localetest.html                             Displays localized strings
├── <b>modules/</b>   ----------------------------- Assets and scenario initialization
│   ├── <b>assets/</b>                              Images, animation components and publishing scripts
│   │   ├── <b>actors/</b>
│   │   │   ├── <b>avatar/</b>
│   │   │   │   ├── AllScenarios_AvatarCustomization_Figure0.fla
│   │   │   │   ├── AllScenarios_AvatarCustomization_Figure0.js
│   │   │   │   ├── AllScenarios_AvatarCustomization_Figure1.fla
│   │   │   │   └── AllScenarios_AvatarCustomization_Figure1.js
│   │   │   ├── defenseattorney.js
│   │   │   ├── judge.js
│   │   │   ├── prosecutor.js
│   │   │   └── TEMPLATE_animation_frame.js
│   │   ├── <b>clips/</b>
│   │   │   ├── <b>fla/</b>
│   │   │   │   ├── AllScenarios_Jail_Figure0.fla
│   │   │   │   ├── AllScenarios_Jail_Figure1.fla
│   │   │   │   ├── AllScenarios_PhoneRoom_Figure0.fla
│   │   │   │   ├── AllScenarios_PhoneRoom_Figure1.fla
│   │   │   │   ├── Defense_Attorney.fla
│   │   │   │   ├── Judge_Main_File.fla
│   │   │   │   ├── Prosecutor.fla
│   │   │   │   ├── Scenario1_FlashbackGuilty_Figure0.fla
│   │   │   │   ├── Scenario1_FlashbackGuilty_Figure1.fla
│   │   │   │   ├── Scenario1_FlashbackInnocent_Figure0.fla
│   │   │   │   ├── Scenario1_FlashbackInnocent_Figure1.fla
│   │   │   │   ├── Scenario1_Intro_Figure0.fla
│   │   │   │   ├── Scenario1_Intro_Figure1.fla
│   │   │   │   ├── Scenario1_SecurityFootage_AllFigures.fla
│   │   │   │   ├── Scenario2_FlashbackGuilty_Figure0.fla
│   │   │   │   ├── Scenario2_FlashbackGuilty_Figure1.fla
│   │   │   │   ├── Scenario2_FlashbackInnocent_Figure0.fla
│   │   │   │   ├── Scenario2_FlashbackInnocent_Figure1.fla
│   │   │   │   ├── Scenario2_Intro_Figure0.fla
│   │   │   │   ├── Scenario2_Intro_Figure1.fla
│   │   │   │   ├── Scenario2_SecurityCam_Figure0.fla
│   │   │   │   └── Scenario2_SecurityCam_Figure1.fla
│   │   │   ├── <b>images/</b>
│   │   │   │   ├── jailcellday.jpg
│   │   │   │   └── jailcell.jpg
│   │   │   ├── AllScenarios_Jail_Figure0.js
│   │   │   ├── AllScenarios_Jail_Figure1.js
│   │   │   ├── AllScenarios_LibFixer.js
│   │   │   ├── prologue.js
│   │   │   ├── Scenario1_FlashbackGuilty_Figure0.js
│   │   │   ├── Scenario1_FlashbackGuilty_Figure1.js
│   │   │   ├── Scenario1_FlashbackInnocent_Figure0.js
│   │   │   ├── Scenario1_FlashbackInnocent_Figure1.js
│   │   │   ├── Scenario1_Intro_Figure0.js
│   │   │   ├── Scenario1_Intro_Figure1.js
│   │   │   ├── Scenario1_SecurityFootage_AllFigures.js
│   │   │   ├── Scenario2_FlashbackGuilty_Figure0.js
│   │   │   ├── Scenario2_FlashbackGuilty_Figure1.js
│   │   │   ├── Scenario2_FlashbackInnocent_Figure0.js
│   │   │   ├── Scenario2_FlashbackInnocent_Figure1.js
│   │   │   ├── Scenario2_Intro_Figure0.js
│   │   │   ├── Scenario2_Intro_Figure1.js
│   │   │   ├── Scenario2_SecurityCam_Figure0.js
│   │   │   ├── Scenario2_SecurityCam_Figure1.js
│   │   │   └── securityfootagestatic.js
│   │   ├── <b>customizer/</b>
│   │   │   ├── arrowleft.png
│   │   │   ├── arrowright.png
│   │   │   ├── SilhouetteFigure0.png
│   │   │   └── SilhouetteFigure1.png
│   │   ├── <b>publishing-scripts/</b>              Bash scripts to prepare Adobe Animate generated JS files
│   │   │   ├── <b>test-files/</b>
│   │   │   │   ├── <b>job/</b>
│   │   │   │   │   ├── minimal_animate_publish_test.js
│   │   │   │   │   └── Scenario2_Intro_Figure0.js
│   │   │   │   ├── <b>libs/</b>
│   │   │   │   │   └── createjs-2015.11.26.min.js
│   │   │   │   ├── auto_publish.sh
│   │   │   │   ├── directory-test.sh
│   │   │   │   ├── minimal_animate_publish_test.js
│   │   │   │   ├── Scenario2_Intro_Figure0 2.js
│   │   │   │   ├── Scenario2_Intro_Figure0.html
│   │   │   │   ├── Scenario2_Intro_Figure0.js
│   │   │   │   ├── tester2.sh
│   │   │   │   └── tester.sh
│   │   │   ├── add-lib.sh                          Fix JS files from Adobe Animate for compatibility
│   │   │   ├── palettize.sh                        Replace hardcoded colors with color pallete variables
│   │   │   ├── prepare-avatar-feature-toggling.sh  Add if statements to allow toggling of avatar attributes
│   │   │   └── publish-scene.sh                    Run the scripts in sequence on a given JS file from Animate
│   │   └── <b>scenes/</b>
│   │       ├── <b>backgrounds/</b>
│   │       │   ├── blankjail.png
│   │       │   ├── courtroom_2019.png
│   │       │   ├── courtroom.png
│   │       │   ├── guiltytext1.png
│   │       │   ├── guiltytext2.png
│   │       │   ├── judgecourtroom.png
│   │       │   ├── JudgeSeat.png
│   │       │   ├── meetingroom.png
│   │       │   └── plainwhite.png
│   │       └── <b>foregrounds/</b>
│   │           ├── easeljs.png
│   │           ├── jailcellgeneral1.png
│   │           ├── jailcellgeneral2.png
│   │           ├── jailcellgeneral3da.png
│   │           ├── jailcellgeneral3.png
│   │           ├── jailcellgeneral4.png
│   │           ├── jailcellguilty1.png
│   │           ├── jailcellguilty2.png
│   │           ├── jailcellinnocent1.png
│   │           ├── jailcellinnocent2.png
│   │           ├── jailcellinnocent3.png
│   │           └── table.png
│   ├── binding.js                                  Create and map names to clip and actor objects
│   ├── hitandrun_1.2.js                            Hit and run initialization
│   ├── hitandrun.json                              Configuration for hit and run
│   ├── honors_1.0.js
│   └── shoplifting.js
├── avatar_creation.html                            Avatar creator page
├── favicon.png                                     University logo
├── simulation2.0.html                              Simulation restructured to load flow from JSON configuration
├── simulation-hitandrun.html                       Hit and run simulation page
├── simulation-honors.html                          Hit and run honors simulation
├── simulation.html                                 Load a particular simulation module given by parameter
└── simulation-shoplifting.html                     Shoplifting simulation page
</pre>
