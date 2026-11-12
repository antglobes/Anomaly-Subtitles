# A Guide to Contributing to Anomaly Subtitles

## Summary

There's a few ways to contribute the anomaly subtitles, if your reading this
after visting the [moddb page](https://www.moddb.com/addons/anomaly-subtitles)
you may be aware of the core points when it comes to how Anomaly Subtitles.
If not i will go over them as to ensure everyone is on the same page.
Anomaly Subtitles is works by comparing (parsed) paths to audio files that
contain npc dialog, mutant sounds etc and gets a pre-translated string to
display. Initally (before i was aware of the ethical issues with AGI) these
files had been machine translated locally using a natural language ML engine,
this meant that whilst the majority of the audio had a translation, the quality
was quite poor overall. Since then i have opted for a different approach that
doesn't use AGI, is more community oriented and relies on the kindness of strangers fluent in
english and/or russian to help with translating and determining the validity
of each audio file. Whilst this is alot slower process, i am sure that the
quality overall will vastly improve.

## Disclaimer

Due to the location and time of the game being released alot of the audio
files will be from an 18+ perspective, they might contain swears and
slurs, if you would be uncomfatable with interacting with such this is
your warning. I will state that (if not implemented at the time of viewing)
there will be option to censor some of this but as for the raw translation
these things will be kept as to keep the understanding as true to it's
original design.

## Contribution Outline

As we proceed i will cover the following for anyone willing the contribute
which should lay out a straight forward workflow:

- The Scope of the work
- How the work should be formatted
- The process for including it Anomaly Subtitles

## Requirements

- A ability to understand standard english in written and auditory format.
- A ability to understand russiand and/or ukrianian in written and auditory format.
- Understanding of different english dialects and slang (optional).
- Understanding of different russian dialects and slang (optional).
- You don't have to be a professional in any of these languages, having a casual understanding is perfectly good enough.
- A basic understanding of Git and Github (optional but preferred and can be taught if willing to make the process smoother).
- A familariarity with S.T.A.L.K.E.R Anomaly's vanilla codebase (optional but preferred and can be taught if willing to make the process smoother).

## Audio Directories that have been translated and verified for accuracy

NPC Dialog, Root directory: `characters_voice\human`

- bandit 1 + 2 + 3 (in proccess)

## Key Areas that will assist in Translation & Verification

### Sound Folder

- The heart of this project lies in the folder `gamedata\sounds`.
- This can be sourced by either using the unpacker found in the distrubtion of anomaly at `.\tools\db_unpacker.bat` or download from [this repository](https://github.com/Tosox/STALKER-Anomaly-gamedata/tree/v1.5.2/gamedata/sounds) that the modder Tosox has kindly provided or by asking myself (antglobes) and i will give you an archive of the sounds folder.
- If you wish to unpack them yourself but only the `gamedata\sounds` folder i have a version of `db_unpacker.bat` that can do so, just message me asking for such.
- Note: Folder and directory will be used interchangable but they mean the same thing.

### Subtitles Folder

- The [Directory](https://github.com/antglobes/Anomaly-Subtitles/tree/main/gamedata/configs/text/eng) that holds the xml files containing the translated audio files.
- All xml files must start with the prefix `st_as_sub`.
- All `<string id="">` must start with the prefix `as_sub_`
- Example: the file `st_as_sub_bandit_3_fight.xml` in the subtitles folder will correspond to the directory in the sounds directory `gamedata\sounds\characters_voice\human\bandit\fight`
- Note: the file names have yet to be normalised (format the file names so that they follow the same standard for readablility), so xml files can appear as `st_as_sub_human_<faction>_<number>_<sub_dir>`, instead of the expected `st_as_sub_<faction>_<number>_<sub_dir>` but still corresspond to the same sound directory (this is an artifact left over from the inital translation).
- Now for every `<string>` in `st_as_sub_bandit_3_fight.xml`  the base for it's id will be `characters_voice_human_bandit_3_fight`.
- If we want to translate the audio file `attack_1.ogg` found in sub directory `gamedata\sounds\characters_voice\human\bandit\fight\attack\` the result `<string id="">` would be a combination of string_id prefix + base_id + every sub directory until the file + audio file name resulting in `as_sub_characters_voice_human_bandit_3_fight_attack_attack_1`.

## Process of Translation

Download a subtitle xml file, find the corresponding audio directory in the sounds folder, listen to each audio file, if the string doesnt exist for it: create using the other subtitle xml files as reference otherwise replace the text with the translation that you have created, optionally leave a comment detailing why you made this as to assist with verification and future reference.

Working from example, if you take a look
[here](https://github.com/antglobes/Anomaly-Subtitles/commits/main/) at this
commit history (record of changes to files in the repository) from May 29 2025
to June 18 2025. This translation and review that previous contributors 'Lin' &
'tehanow' created shows the end result, where they translated the relevaant
audio files, reviewed their translation to ensure that it made sense
contextually, wrote them in the correct format inside a xml file and sent a
pull request to the repo in which i (antglobes) could verify and merge with
the rest of the code.

## Process of Verification

1. choose any files in the [subtitles folder](https://github.com/antglobes/Anomaly-Subtitles/tree/main/gamedata/configs/text/eng) with the prefix `st_as_sub` except for any that has already been stated as translated.
2. download the file.
3. find the ogg file that corresponds to each string id.
4. either download that ogg file from [here](https://github.com/Tosox/STALKER-Anomaly-gamedata/tree/v1.5.2/gamedata/sounds/characters_voice/human) or unpack the anomalys db files to get the sound files, (run the unpacker.bat)
5. listen to the ogg file.
6. translate as best as possible what the meaning is.
7. go back to the downloaded file and write in the translation if you think it to not be accurate enough. (A comment above would help, marking which ones you have changed, refer to this [file](https://github.com/antglobes/Anomaly-Subtitles/blob/main/gamedata/configs/text/eng/st_as_sub_bandit_1_fight.xml) for an example)
8. repeat steps 3 -7 as much as you want, (skipping step 4 if you have the files)

Note: Duplicates have to stay in due to how npc dialogue lines work, if you are to make changes within the xml please only change the text between the `<text>` tags and add comment

## Process of Implementation

If you arent familar with github and wish to keep things simple see the following otherwise please ignore this part.
Once you have either translated or verified the accuracy of the translated files, you should have a bunch of files in a folder, put them in an archive (preferably .zip or .7z) and send them to me for the final verification process either on discord @antglobes or to my email antglobes@gmail.com.

If you are familat with github this part is for you, got to the [Anomaly Subtitles Repo](https://github.com/antglobes/Anomaly-Subtitles) and make a pull request, i'll review and verify these files and merge them once accepted.

## Closing Remarks

If any part of this is unclear, feel free to reach out to me (antglobes) and i will clarify.
