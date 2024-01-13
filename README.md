# Yamaha S-YXG50 Control Panel
A [Reaper](https://www.reaper.fm/) JSFX midi effect that allows to control the Yamaha S-YXG50 synth, this effect is a modified version of [Shiru's control panel](https://www.kvraudio.com/forum/viewtopic.php?t=486318).

![Screenshot](https://github.com/samlletas/syxg50-control-panel/assets/7089504/37988d9c-2f44-4c5a-8670-59b271415121)

## Description
The following features were added:

- Default values for every parameter (obtained from the [XG Specifications manual](http://www.jososoft.dk/yamaha/pdf/XGspec2-00e.pdf)).
- A new editor tab that allows the user to edit common voice parameters (filter, envelope, vibrato, portamento, etc).
- Instruments are now saved per channel (parameters from the editor tab are saved per channel as well).
- Adds the few missing reverb, chorus and variation effects.
- UI improvements:
     - New UI colors and bigger font for increased readability.
     - Highlight user-changed parameters.
     - When changing channel the instrument category switches accordingly.
- Serialize parameter values instead of slider positions to avoid inconsistencies due to float precision loss.

> 💡 This modified version is **NOT** compatible with Shiru's original version due to serialization changes, if you need to open old projects then you should keep both versions installed.

## Download & Install
Download the zip file from the [Releases](https://github.com/samlletas/syxg50-control-panel/releases) page, extract it and copy its contents to your Reaper effects folder.

## Usage

In order to enable variation effects the Control Panel sends the `variation connection` sysex message, however this happens once during instantiation so [variation effects won't work unless the FX Chain is created in the following order](https://www.kvraudio.com/forum/viewtopic.php?p=7350751#p7350751):

1. Add the S-YXG50 plugin into the FX Chain.
1. Drag the Control Panel from the FX Browser and drop it **ABOVE** the S-YXG50 plugin.

### Mouse Controls

`Sliders`

- Left click to change value.
- Right click or Ctrl+Left click to reset to default value.
- Scroll wheel to change value by small increments/decrements.

`Channel`

- Left click to select next channel.
- Right click to select previous channel.
- Scroll wheel to select next/previous channel.
- Number keys to change channel (from 1 to 10).

## FAQ

### Why are variation effects not working?

The FX Chain needs to be setup in a specific way, please see the [Usage](#usage) section for more details.

### Why does the S-YXG50 synth occasionally produces stuck midi notes and/or misses midi notes?

This seems to be an issue when bridging 32-bit plugins within the 64-bit version of Reaper. Since the S-YXG50 synth is a 32-bit plugin it is recommended to either:

- Use the 32-bit version of Reaper.
- Use an alternative bridging solution like [jBridge](https://jstuff.wordpress.com/jbridge/) (make sure to use version 1.77beta or newer).

## Development & Contributing

If a new parameter needs to be serialized please add it after the previous ones to avoid breaking compatibility.

### Making Commits
All commits should be made using the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary) specification, to help with this a git hook that validates commit messages can be installed with:

     cp -r -T .githooks .git/hooks
