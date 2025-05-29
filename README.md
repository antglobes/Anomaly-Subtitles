# Anomaly Subtitles

- Translation/Transcription of all voicelines and mutant sounds from Russian to English
- Co-authors: **VodoXleb, Lin (@synthcalibur), tehanow**

## Disclaimer

- The Majority of the subtitles are machine translated, since this is in Beta state until we can check the accuracy of translations,  some are missing, others don't make complete sense.
- If you want to help our read the "Helping with Translations" Section.
- Undergoing complete re-translation.

## Displaying Subtitles

- Using an engine patch, there is now a callback "on_phrase_callback" that whenever an npc makes a sound
  the path-name and the npc game object, from that depending on the MCM option the subtitle is displayed
  via ~~the news manager~~ a customisable HUD with a few options for accessibility
- ~~xr_sound is also monkey-patched and subtitle info is gathered similar to the prior process~~.

## How it's works

- The engine callback `on_phrase_callback` spits out a path to a sound file and a game object of the npc that is playing a sound using that sound file
- Since the path often doesn't point to an actual sound file but rather a sound_file and an incorrect id or just a chain of subdirectiories.
- We parse the path turning it into a readable path and providing a similar alternative if the orginal can't be found in the sounds directory.
- Then the path is turned into a xml id, from which various info is grabbed
- This is validated and added to a queue for that npc if it's valid
- The Subtitles HUD, adds a Caption UI per npc that stays active until the npc is despawned
- The Caption UI gets the first subtitle info from the queue assigned to that npc
- Subtitle tokens are added to the caption box every second until fade time has been reached
- Both caption box and background (if enabled) are faded until total display time is reached
- UI is Reset when display time has ended
  
## Adding your own Subtitles

- The file name doesn't matter, however the structure has to be like any other "<string_table>" file
- The Tag must start with "as_sub_" in order to be recognised
- The path-name to the sound file HAS to included in the tag after the "as_sub_" prefix (Starting with the folder under the root folder aka characters_voice under sounds)
- The actual string inside can be whatever

## Helping with Translations

- If you check the [github](https://github.com/antglobes/Anomaly-Subtitles) for this addon, under the transcriptions folder should be a copy of each file's transcription in russian.
- Since we don't have the full ability nor the time to dedicate to manual transcription and translation of each and every voice sound file, the majority of the ones present in this addon have been machine translated.
- If you want access to the script that is used to translate/transcribe .ogg files and write the outputs to xml, please dm me on discord @antglobes, you can see an example [here](https://discord.com/channels/912320241713958912/1237842568067416165/1370775389869309978)
- If you feel like you can help out and check the accuracy of the transcriptions/provide relplacements for the nonsensical or incorrect ones please dm or make an issue stating so on the github repo.

## Subtitles for own mod/addon

- If you want subtitles for your mod that affects npc voicelines, please raise an issue on the github and ~~fill out the form~~ or dm me with a link to your mod via moddb dms and i'll send you what details i'll need from you.

## Installation

### M02

- Download the mod, M02, DLTX/Modded Exes, MCM
- Place the zip file in M02 downloads folder
- Right click on the zip from within M02, it should be underneath the downloads tab next to the data tab
- Click Install
- Select Main
- Done

### Manual

- Copy across the gamedata folder
- DONT COPY ACROSS THE FOMOD FOLDER
- Done
  
### Requirements

- [MO2](https://github.com/ModOrganizer2/modorganizer) (optional but preferred)
- [DLTX/Modded Exes](https://github.com/themrdemonized/STALKER-Anomaly-modded-exes) (Required, at least Release 2024.10.05)
- [MCM](https://www.moddb.com/mods/stalker-anomaly/addons/anomaly-mod-configuration-menu) (If using the required Modded Exes, use at least v1.7.0 of MCM)
- Compatible with 1.5.2 and 1.5.3 (From v0.9.0 onwards)

## License

[GNU GPL 3](https://www.gnu.org/licenses/gpl-3.0.en.html)

## Credits

- Lucy, xcvb, mrdemonized, SimplyLeo (Vinci), Meeps (meepysama), GhenToung, Catspaw
  
## Known Issues

- Version with issues (Version with issues fixed) Reason for issues occuring.
- v0.5.2+ (Fixed in v0.6.0) Subtitles HUD not showing due to removed mcm opt meaning continous nil variable.
- v0.6.0 (Fixed in v0.6.1) Certain npc portraits are missing causing CTD.
- v0.5.2+ (Fixed in v0.6.2) Cooldown mcm option was present but not being applied during queue processing.
- v0.6.2 (Fixed in v0.6.3) Queue stuck in finite suspension after dialog/inventory window opened, skipping over subtitles due to incorrect timer updating, nil/invalid subtitles not being caught and still displayed.
- v0.6.4 (Fixed in v0.7.1) Missing Icon textures (specifically prof. kalancha) causing CTD beacuse of missing texture xml.
- v0.7.2 (Fixed in v0.7.3) Failure to catch last part of the sentence, causing unintented functionality.
- v0.8.0 (Partial Fix in v0.8.1) Incorrect Calculation of hearing multiplier when headgear removed.
- v0.7.3 (FIxed v0.8.3) Additional or Missing Tokens when grouping subtitle truncation tokens.
- v0.8.4 (Fixed v0.8.4) Incorrect solution for calculating hearing distance; equipping/removing headgear/NVGs.
- v0.8.5 (Fixed v0.9.0) Incorrect Pattern Matching for Unusual soundnames, Ignore Setting/Resetting Distance on item pickup or drop from inventory.
- v0.9.0 (Fixed v0.9.1) Prevent Setting Hearing Distance until setup complete
- v0.9.1 (Fixed v0.10.0-alpha) Included More Special Characters
- v0.6.1 (Fixed v0.10.0) HUD(UI) HUD blocks other subtitles being shown, Scrapped Completely.
- v0.10.0 (Fixed v0.10.1) CTD when attemptting to display nil subtitles
- v0.10.1 (Fixed v0.10.2) Fail to load due to nil table index
- v0.10.2 (Fixed v0.11.0) Subtitles not showing up at all and causing a CTD.
- v0.11.0 (Fixed v0.11.1) Background Size, Subtitle Color being reset when faction clr not enabled
- v0.11.1 (Fixed v0.11.2) CTD when attempting to generate subtitle for zombified stalker
- v0.11.2 (Fixed v0.11.3) CTD when attempting to get end digits for sound file

## Changelog

- v0.5.2 Base Version
- v0.5.3 Active Dialog/Inventory Opened Prevents queue processing, NPC Distance based queue .priority, Exclude Silent Subtitles, Inclusion of Trader Faction, Reworked HUD Activation.
- v0.6.0 Fixed HUD not showing, Inclusion of some missing subtitles.
- v0.6.1 Include News Manager Icons for HUD.
- v0.6.2 Fixed Queue Timer, Reintergrated Subtitle Cooldown.
- v0.6.3 Reworked queue processing, More verification for subtitle.
- v0.6.4 Added Debugging Levels to debug print functions.
- v0.7.1 Fixed Missing Icon Texture, UI Defaults.
- v0.7.2 Subtitle Truncation.
- v0.7.3 Ask to Queue, Fixed Subtitle Truncation.
- v0.8.0 Headgear Affects Hearing Distance.
- v0.8.1 Reset Headgear when Removed.
- v0.8.2 Material Effects Haring Chance, Dev Utils.
- v0.8.3 Collect Icon Textures for Subtitle Verification, Fixed Subtitle Grouping Truncation Tokens. Majority Sounds Translated.
- v0.8.4 Ray Shown Only If Debugging Enabled
- v0.8.5 Ray Shown Only at higher debug levels, Hearing Distance and Truncation Token Duplicate Fix.
- v0.9.0 Hear Chance Calculation Altered, Helmet Condition Effects Total Multiplier, Equip Table Multiplier Values Lowered, Subtitles Removed if Timer Expired, Ignore/Remove Subtitles After NPC Death.
- v0.9.1 Prevent Setting Hearing Distance until setup complete
- v0.10.0-alpha Bulk Remove Dead NPC Subtitles, Active Hear Distance Check, Rework: Displaying Shorten Subtitles via News Manager; Material Ray Direction via Position, MCM Option: Enable Mutant Subtitles.
- v0.10.0 Scrapped Custom UI, Fix for subtitle timing, Using just news manager for UI, Removed MCM Options.
- v0.10.1 Group Sub Tokens to increase time shown on screen, More Subtitles for 100 Rads located NPCs.
- v0.11.0 Complete Rework, New sound file parsing, per NPC UI with accessibility options.
- v0.11.1 Resized Background, Added Texture Preview for Subtitle, Changed MCM defaults.
- v0.11.2 Try all parts of visual string when getting faction for zombied faction.
- v0.11.3 Sanity Check for getting end digits for sound path.
- v0.11.4 MCM Option to turn off fight subtitles
