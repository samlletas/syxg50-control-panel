# Yamaha S-YXG50 Control Panel
A [Reaper](https://www.reaper.fm/) JSFX midi effect that allows to control the Yamaha S-YXG50 synth, this effect is a modified version of [Shiru's control panel](https://www.kvraudio.com/forum/viewtopic.php?t=486318).

![Screenshot](https://github.com/samlletas/syxg50-control-panel/assets/7089504/b4ebd288-2771-4511-b788-33c6d2f1d3c3)

## Description
The following features were added:

- Default values for every parameter (obtained from the [XG Specifications manual](http://www.jososoft.dk/yamaha/pdf/XGspec2-00e.pdf)).
- A new editor tab that allows the user to edit common voice parameters (filter, envelope, vibrato, portamento, etc).
- Instruments are now saved per channel (parameters from the editor tab are saved per channel as well).
- When changing MIDI channel the instrument category switches accordingly.
- Serialize parameter values instead of slider positions to avoid inconsistencies due to float precision loss.

> 💡 This modified version is **NOT** compatible with Shiru's original version due to serialization changes, if you need to open old projects then you should keep both versions installed.

## Download
TODO.

## Development & Contributing

If a new parameter needs to be serialized please add it after the previous ones to avoid breaking compatibility.

### Making Commits
All commits should be made using the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary) specification, to help with this a git hook that validates commit messages can be installed with:

     cp -r -T .githooks .git/hooks
