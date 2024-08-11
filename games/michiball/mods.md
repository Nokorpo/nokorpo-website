---
layout: default
title: How to create mods for Michiball
---

## {{ page.title }}

> ⚠️ _This page is still a work in progress. The whole detailed instructions will be released when the game finally comes out._

Our game [Michiball](/games/michiball) has mod support.

## How to create custom characters

You can add new custom characters to Michiball, and use them as any other character in the game.

### 1. Open the mods folder

Open the mods folder, the easiest way to locate it, is to open Michiball, and go to `settings > mods` you will see the mod folder path, and a handy button to open the folder.

![Michiball settings menu](/assets/images/games/michiball/mods-tutorial-1.jpg)


### 2. Navigate the files

You will see there is a default `/custom_resources/characters/sample_character/` folder, you can use this as a base for creating new mods, let's take a look at what files it has:

- `info.cfg`: has the config files, open this with any text editor and set the `name="Sample character"` to anything you want, and the most important things is that you have to change `enabled=false` to `enabled=ture` in order to enable it inside the game.
- `preview.png`: is the image preview of the character, in the character selection screen.
- `sample_character.gltf`: is the 3D [.gltf file](https://en.wikipedia.org/wiki/GlTF) of the character

So you just need to change these files to create a custom character. You can have as many folders with as many mods as you want.

### 3. Modify the default sample character

You can open and modify the `sample_character.gltf` as you want.

The easiest way we offer, is to download the `sample_character.bbmodel`, and modify it using the open source [Blockbench](https://www.blockbench.net/) app.

<a href="/games/michiball/mods/sample_character.bbmodel" download="sample_character.bbmodel">
<button>Click to download the sample character</button>
</a>

You will see the character is composed of different parts _(Head, Body, Hands, RightHand, Wrist...)_. Do not change or move these pivots, since the animation system of Michiball needs them to animate the charactes.

You can modify the different parts of the body of this character, repaint it's texture, and even add new parts. Then export is as a `.gltf` and add it to the character mod folder.

![A screenshot of a character in a 3D editor](/assets/images/games/michiball/mods.jpg)


## How to create custom maps
⚠️ _This section is still a work in progress..._