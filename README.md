# Arkenbird-softening
<img src="https://upload.wikimedia.org/wikipedia/commons/5/53/Thunderbird_2023_icon.png" alt="Thunderbird logo" width="200"/>

Thunderbird can and should be made more secure. This script uses [an existing preset](https://github.com/HorlogeSkynet/thunderbird-user.js/) and loses it up again, to make Thunderbird work normally. It also includes and automatic updater.

A `user.js` is a settings overwrite file. Settings mentioned in here will always overwrite your Thunderbird settings. This is useful to have a preset of hardening switches, because like Firefox, Thunderbird is very customizable and a bit too open by default.

Avoid setting configs in this file, that are noncritical and can be changed in the Settings GUI, as this file makes changing them in the GUI impossible, they are gone after relaunch.

## Installation

### 1. Go to your Thunderbird / Betterbird user directory.

Regular installs:

```
cd ~/.thunderbird
```

Flatpak:

```
cd ~/.var/app/org.mozilla.Thunderbird/.thunderbird
#or
cd ~/.var/app/eu.betterbird.Betterbird/.thunderbird
```

Snap:

```
I have no idea and dont care
````

### 2. Download and run

```
wget https://github.com/trytomakeyouprivate/Arkenbird-softening/raw/main/thunderbird-hardening-overwrite &&\
chmod +x thunderbird-hardening-overwrite &&\
. ./thunderbird-hardening.overwrite
```


### Technical details
- It downloads the user.js from [HorlogeSkynet](https://raw.githubusercontent.com/HorlogeSkynet/thunderbird-user.js/master/user.js) which is a bit messed up, has lots of Firefox configs in it and some unnecessary hardening.
- It uses `sed` to change values from `true` to `false`, or set Numbers (explanations in the user.js) to change some settings
- It uses `sed` again, to deactivate some lines that may be okay, but should not be forced, like Dictionary Check. This doesnt change anything, either if you already "hardened" your Thunderbird, or if its default. So you may want to look into the file and change the settings yourself.
- It creates an autostart entry to start the script on every login after 2min. There are several breakout commands, to not run it if there is no need. GUI messages are only used for errors.
