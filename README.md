# Yamaha S-YXG50 Control Panel
A [Reaper](https://www.reaper.fm/) JSFX plugin that allows to control the Yamaha S-YXG50 synth, this project is a modified version of [Shiru's control panel](https://www.kvraudio.com/forum/viewtopic.php?t=486318).

![Screenshot](https://github.com/samlletas/syxg50-control-panel/assets/7089504/1b4fbcb5-d8f2-4436-8848-653080780256)

## Description
The following features were added:

- Default values for every parameter (obtained from both XGworks and the [XG Specifications manual](http://www.jososoft.dk/yamaha/pdf/XGspec2-00e.pdf)).
- A new editor tab for changing voice parameters (filter, envelopes, modulation, tuning, etc).
- Instruments are now saved per part (parameters from the editor tab are saved per part as well).
- Adds the few missing reverb, chorus and variation effects.
- UI improvements:
     - New colors and bigger font for increased readability.
     - New "XG" button to force re-send all parameters.
     - Highlight user-changed parameters.
     - Use full names for all voices (thanks @mkruselj).
     - Draw bipolar parameters with bipolar sliders (thanks @mkruselj).
- Serialize parameter values instead of slider positions to avoid inconsistencies due to float precision loss.
- And many more small improvements and bug fixes.

> 💡 This modified version is **NOT** compatible with Shiru's original version due to serialization changes, if you need to open old projects then you should keep both versions installed.

## Download & Install
Download the zip file from the [Releases](https://github.com/samlletas/syxg50-control-panel/releases) page, extract it and copy its contents to your Reaper effects folder.

## Usage

In order to enable variation effects the Control Panel sends the `variation connection` sysex message, however this happens once during instantiation so [variation effects won't work unless the FX Chain is created in the following order](https://www.kvraudio.com/forum/viewtopic.php?p=7350751#p7350751):

1. Add the S-YXG50 synth into the FX Chain.
1. Drag the Control Panel from the FX Browser and drop it **ABOVE** the S-YXG50 synth.

> 💡 Clicking on the **XG** button (located at the top-right corner) will force re-send all the parameters to the S-YXG50 synth. This can be useful if you already changed some parameters but forgot to move the Control Panel above the S-YXG50 synth in the FX Chain.

### Controls

`Sliders`

- Left click to change value.
- Right click or Ctrl+Left click to reset to default value.
- Scroll wheel to change value by small increments/decrements.

`Part`

- Left click to select next part.
- Right click to select previous part.
- Scroll wheel to select next/previous part.
- Number keys to change part (from 1 to 10).
- QWERTY keys to change part (from 11 to 16).

## FAQ

### Why are variation effects not working?

The FX Chain needs to be setup in a specific way, please see the [Usage](#usage) section for more details.

### Why does the S-YXG50 synth occasionally produces stuck midi notes and/or misses midi notes?

This seems to be an issue when bridging 32-bit plugins within the 64-bit version of Reaper. Since the S-YXG50 synth is a 32-bit plugin it is recommended to either:

- Use the 32-bit version of Reaper.
- Use an alternative bridging solution like [jBridge](https://jstuff.wordpress.com/jbridge/) (make sure to use version 1.77beta or newer).

### Can I use the plugin in a different host other than Reaper?

This plugin is in JSFX format so it's intended for use within Reaper only, however there are tools that allow running JSFX plugins outside Reaper so it may be worth giving them a try:

- https://github.com/JoepVanlier/ysfx
- https://github.com/DISTRHO/Ildaeil
- https://www.reaper.fm/reaplugs/

## Development & Contributing

If a new parameter needs to be serialized please add it after the previous ones to avoid breaking compatibility.

### Making Commits
All commits should be made using the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary) specification, to help with this a git hook that validates commit messages can be installed with:

     cp -r -T .githooks .git/hooks
