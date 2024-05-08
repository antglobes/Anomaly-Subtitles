# Anomaly Subtitles
- Translation/Transcription of all voicelines and mutant sounds from Russian to English
- Co-author VodoXleb

## Disclaimer
- The Majority of the subtitles are machine translated, since this is in Beta state until we can check the accuracy of translations,  some are missing, others don't make complete sense.
- If you want to help our read the "Helping with Translations" Section.

## Displaying Subtitles
- Using an engine patch, there is now a callback "on_phrase_callback" that whenever an npc makes a sound
  the path-name and the npc game object, from that depending on the MCM option the subtitle is displayed
  via the news manager or a customisable HUD with a few options for accessibility
  - If using news manager + localisation mcm options and the flag you want isn't showing replace "eng" with any field in gamedata\configs\plugins\mod_news_tips_icons_as.ltx.

## How it's built
- 6 Variables are used to build a table used to assit with how long it's shown, the contents of the subtitle, who said the subtitle, an icon to identify the speaker, the localisation (if needed) and the speakers faction.
- Speaker Name, Speaker Icon, Speaker Faction, Subtitle, Locale, Duration
  
## Adding your own Subtitles
- The file name doesn't matter, however the structure has to be like any other string table file
- The Tag must start with "as_sub_" in order to be recognised
- The path-name has to included in the tag after the "as_sub_" prefix
- The actual string inside can be whatever 

## Helping with Translations
- If you check the [github](https://github.com/antglobes/Anomaly-Subtitles) for this addon, under the transcriptions folder should be a copy of each file's transcription in russian.
- Since we don't have the full ability nor the time to dedicate to manual transcription and translation of each and every voice sound file, the majority of the ones present in this addon have been machine translated.
- If you want access to the script that is used to translate/transcribe .ogg files and write the outputs to xml please dm me on discord @antglobes
- If you feel like you can help out and check the accuracy of the transcriptions/provide relplacements for the nonsensical or incorrect ones please dm or make an issue stating so on the github repo.

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
- None as of v1.0
  
## Changelog
- v0.5.2 Base Version
- v0.5.3 Active Dialog/Inventory Opened Prevents queue processing, NPC Distance based queue priority, Exclude Silent Subtitles, Inclusion of Trader Faction, Reworked HUD Activation, 