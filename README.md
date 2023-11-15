# Yamaha S-YXG50 Control Panel
A [Reaper](https://www.reaper.fm/) JSFX midi effect that allows to control the Yamaha S-YXG50 synth, this effect is a modified version of [Shiru's control panel](https://www.kvraudio.com/forum/viewtopic.php?t=486318).

![Screenshot](https://github.com/samlletas/syxg50-control-panel/assets/7089504/aa2eb9a3-c4a2-42ce-ba76-2adfe4173dd5)

## Description
The following features were added:

- Default values for every parameter (obtained from the [XG Specifications manual](http://www.jososoft.dk/yamaha/pdf/XGspec2-00e.pdf)).
- A new editor tab that allows the user to edit common voice parameters (filter, envelope, vibrato, portamento, etc).
- Instruments are now saved per channel (parameters from the editor tab are saved per channel as well).
- When changing MIDI channel the instrument category switches accordingly.
- Serialize parameter values instead of slider positions to avoid inconsistencies due to float precision loss.

> 💡 This modified version is **NOT** compatible with Shiru's original version due to serialization changes, if you need to open old projects then you should keep both versions installed.

## Download & Install
Download the JSFX file from the [Releases](https://github.com/samlletas/syxg50-control-panel/releases) page and copy it to your Reaper effects folder.

## Usage

In order to enable variation effects the Control Panel sends the `variation connection` sysex message, however this happens once during instantiation so [variation effects won't work unless the FX Chain is created in the following order](https://www.kvraudio.com/forum/viewtopic.php?p=7350751#p7350751):

1. Add the S-YXG50 plugin into the FX Chain.
1. Drag the Control Panel from the FX Browser and drop it **ABOVE** the S-YXG50 plugin.

## Development & Contributing

If a new parameter needs to be serialized please add it after the previous ones to avoid breaking compatibility.

### Making Commits
All commits should be made using the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary) specification, to help with this a git hook that validates commit messages can be installed with:

     cp -r -T .githooks .git/hooks
