---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
nav_order: 1
---

# The Plea Justice Project
The Plea Justice Project provides an interactive simulation of legal procedures (it was originally designed to simulate the plea bargaining process specifcally), offering an alternative to existing paradigms in legal decision-making research (e.g., vignettes/narratives, high-stakes deception studies; Redlich et al., 2017; Wilford et al., 2019).

Participants are presented with animated scenarios in which they are represented by a customizable avatar. These scenarios incorporate animated clips, dynamic actors (i.e., law enforcment officer, judge, attorneys) and a variety of backgrounds to increase the participant's immersion in the study. 

This simulation can be integrated with the Qualtrics survey platform and features a graphical configuration tool for researchers.
<details>
<summary><a href="https://demo.pleajustice.org">Click here for a demo</a> of the plea simulation.</summary>
The link will bring you to the <i>Researcher's Preview</i> page on which you may select one of the two existing scenarios (<i>Hit and Run</i> or <i>Shoplifting</i>), variables such as the participant's first name, and other configuration options. The right-hand side of the page provides a sample of the different experimental conditions a participant could be assigned to and the variables manipulated: guilt status, sentencing duration (if found guilty), and the probability of conviction. This demo (and its experimental parameters) represents one of the first published studies using the simulation (Wilford, Sutherland et al., 2021).

It is recommended to turn on the "Avatar Customization" feature located on the same Preview Simulation page for the full immersive experience.
</details>

***

<div style="display: flex; flex-direction: column; width: 100%; align-items: center;">
<p style="text-align: center;"><b><i>A demonstration of an interactive simulation of legal procedures.</i> <br> Virtual workshop with Law and Human Behavior and the American Psychology-Law Society</b></p>
<iframe width="560" height="315" src="https://www.youtube.com/embed/RleYRcLIwjQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

***

## Features

### Animation & Dialogue

Participants are presented with a dynamic story composed of video clips and dialogue with legal actors. The participant experiences parts of the simulation in the third person (in which they are represented by an avatar) and in the first person.

| <img src="./img/home/driving.png" alt="Avatar driving a car" width="100%"> | <img src="./img/home/shopping.png" alt="Avatar pointing to the salesclerk an item they want in an eyeglass store" width="100%"> |

One of two unique scenarios is depicted -- one in which the participant-avatar is leaving a parking lot, and the other in which the participant-avatar is browsing for a pair of glasses at the mall. These animated sequences provide context to the participant as they illustrate a plausible series of events resulting in the participant-avatar being brought to court over accusations of either a hit-and-run or larceny (though, other scenarios are in development)

| <img src="./img/home/judge.PNG" alt="judge reminding the reader their rights" width="100%"> | <img src="./img/home/district_attorney.PNG" alt="district attorney reminding the outcomes if pleading guilty" width="100%"> |

Both sequences lead up to the participant-avatar being summoned to court. For plea decision-making studies, these events culminate with the participant-avatar being offered a plea deal (typically by a defense attorney). The participant navigates the simulation by clicking through interactions with other actors. As the simulation progresses, they learn more about the incident and the context of the accusation (e.g., their guilt status).

### Customizable Avatars

Participants may customize an avatar to represent him or her in the simulation, providing personal depth to the story.

<p align="center">
<img src="./img/home/avatar_creation.PNG" align="center" alt="menu showing customizable aspects of the avatar" width="75%">
</p>

Controls are provided to select among body types, eye shapes, and hairstyles. The colors of the skin, eyes, hair, and outfit of the participant-avatar are also customizable.

### Qualtrics Integration and In-Simulation Prompts

This simulation is designed for integration with Qualtrics. Participants may be routed from a survey to the simulation. Any data collected within the simulation (via "Question"s), is sent to Qualtrics when participants complete the simulation and are directed to a Qualtrics survey.

<p align="center">
<img src="./img/home/plea_offer.PNG" align="center" alt="a meeting room where two buttons are on the center of the screen: 'Plead Guilty' and 'Reject Offer'" width="75%">
</p>

Random assignment to different simulations and manipulation of the text presented in a simulation can be done using Qualtrics' branching logic, embedded data variables, and features of the survey flow.

### Configuration Console for Researchers

An online configuration tool makes it easy for researchers to design new simulation studies without the need for special software.

<p align="center">
<img src="./img/home/research_console.png" align="center" alt="a view of the researcher console assets page" width="100%">
</p>

With the console, researchers may write their own simulated narratives, manipulate variables, create prompts, access a library of animated assets and more. To access this interface, click the *Researcher Console* tab above or visit [researcher.pleajustice.org][reseacher-console-site].

***

## Software and Art Contributors

Interested in contributing to the development of this project or collaborating on related research? You can [contact the Principal Investigator here][contact-PI] if you have any questions, comments, concerns or inquiries regarding the project or the related research.

New developers, please read through _all_ of the documentation on this site. The project is written in vanilla JavaScript and the animated assets are created in _Adobe Animate_. You may find further technical docmentation in the project repositories.

### Software Licensing
This project is distributed under [GNU GPLv3][licensing].

```
    Plea Bargain Simulation
    Copyright (C) 2021 The Plea Justice Project

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

***

## Related Publications
* 10/2021 - [Psychology Today (In)Justice System][article-1]: Increasing the realism (or 'ecological validity') of psychological research
* 08/2021 - [Law and Human Behavior][article-2]: Guilt status influences plea outcomes beyond the shadow-of-the-trial in an interactive simulation of legal procedures
* 06/2021 - [Journal of Experimental Psychology: Applied][article-3]: Innocence in the shadow of COVID-19: Plea decision-making during a pandemic

<!--- below are 1. comments that address long-term changes that need to be made to this page and 2. reference variables that represent external links -->

["Installing; Note: The current implementation"]: <> (be sure to update the method for implementing it on a remote server)
["Recording responses in Qualtrics"]: <> (add a link documentation on data cleaner)
["Licensing implementation"]: <> (will need to look into implementation on licensing; an About page)

[simulation-demo]: https://demo2.pleajustice.org/
[reseacher-console-site]:https://researcher.pleajustice.org/
[git]: https://git-scm.com/downloads
[python]: https://www.python.org/
[http-server]: https://www.npmjs.com/package/http-server
[contact-PI]: https://mikowilford.wixsite.com/website-1
[github-page]: https://github.com/Plea-Justice/pleabargain-simulation
[licensing]: https://github.com/Plea-Justice/pleabargain-simulation/blob/master/LICENSE.txt
[article-1]: https://www.psychologytoday.com/intl/blog/injustice-system/202110/how-could-video-game-improve-the-justice-system
[article-2]: https://psycnet.apa.org/record/2021-90818-001
[article-3]: https://psycnet.apa.org/record/2021-55856-001
