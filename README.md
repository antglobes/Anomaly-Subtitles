# Anomaly Subtitles
- Translation/Transcription of all voicelines and mutant sounds from Russian to English
- Co-author **VodoXleb**

## Disclaimer
- The Majority of the subtitles are machine translated, since this is in Beta state until we can check the accuracy of translations,  some are missing, others don't make complete sense.
- If you want to help our read the "Helping with Translations" Section.
- Factions Not Yet Translated Zombied, Killer (Mercs), Greh (Sin).

## Displaying Subtitles
- Using an engine patch, there is now a callback "on_phrase_callback" that whenever an npc makes a sound
  the path-name and the npc game object, from that depending on the MCM option the subtitle is displayed
  via the news manager or a customisable HUD with a few options for accessibility
  - If using news manager + localisation mcm options and the flag you want isn't showing replace "eng" with any field in gamedata\configs\plugins\mod_news_tips_icons_as.ltx.
- With either way of displaying the subtitles, they are processed in a fifo(first in first out) queue. It's sorted based on the npc's distance to the player with the closest speaker taking highest priority. More filtering options to be added.

## How it's built
- 6 Variables are used to build a table used to assit with how long it's shown, the contents of the subtitle, who said the subtitle, an icon to identify the speaker, the localisation (if needed) and the speakers faction.
- Speaker Name, Speaker Icon, Speaker Faction, Subtitle, Locale, Duration
  
## Adding your own Subtitles
- The file name doesn't matter, however the structure has to be like any other "<string_table>" file
- The Tag must start with "as_sub_" in order to be recognised
- The path-name to the sound file HAS to included in the tag after the "as_sub_" prefix (Starting with the folder under the root folder aka characters_voice under sounds)
- The actual string inside can be whatever 

## Helping with Translations
- If you check the [github](https://github.com/antglobes/Anomaly-Subtitles) for this addon, under the transcriptions folder should be a copy of each file's transcription in russian.
- Since we don't have the full ability nor the time to dedicate to manual transcription and translation of each and every voice sound file, the majority of the ones present in this addon have been machine translated.
- If you want access to the script that is used to translate/transcribe .ogg files and write the outputs to xml, please dm me on discord @antglobes
- If you feel like you can help out and check the accuracy of the transcriptions/provide relplacements for the nonsensical or incorrect ones please dm or make an issue stating so on the github repo.

## Subtitles for own mod/addon
- If you want subtitles for your mod please raise an issue on the github and fill out the form or dm me with a link to your mod via moddb dms and i'll send you what details i'll need from you.

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
- [DLTX/Modded Exes](https://github.com/themrdemonized/STALKER-Anomaly-modded-exes) (Required, at least Release 2024.03.08)

## License
[GNU GPL 3](https://www.gnu.org/licenses/gpl-3.0.en.html)

## Credits
- Lucy, xcvb, mrdemonized, SimplyLeo (Vinci).
  
## Known Issues
Example: Version with issues (Version with issues fixed) Reason for issues occuring.
- v0.5.2+ (Fixed in v0.6.0) Subtitles HUD not showing due to removed mcm opt meaning continous nil variable.
- v0.6.0 (Fixed in v0.6.1) Certain npc portraits are missing causing CTD.
- v0.5.2+ (Fixed in v0.6.2) Cooldown mcm option was present but not being applied during queue processing.
- v0.6.2 (Fixed in v0.6.3) Queue stuck in finite suspension after dialog/inventory window opened, skipping over subtitles due to incorrect timer updating, nil/invalid subtitles not being caught and still displayed.
- v0.6.4 (Fixed in v0.7.1) Missing Icon textures (specifically prof. kalancha) causing CTD beacuse of missing texture xml.
- v0.7.2 (Fixed in v0.7.3) Failure to catch last part of the sentence, causing unintented functionality.
  
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