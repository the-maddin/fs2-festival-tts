# fs2-festival-tts
Script to forward FSO messages to Festival and play speech

## How to install
Software requirements:
- A FSO nightly build from 2021-03-03 or newer
- lua-socket for Lua 5.1 (Provided by `lua51-socket` on Arch, `lua-socket` on Debian/Ubuntu)
- Festival, the free and open source TTS engine (provided by `festival` on Arch and Debian/Ubuntu)
- voices for festival (provided by `festival-us` on Arch, ? on Debian/Ubuntu)

1. Install the data/tables/tts-sct.tbm to your freespace data/tables folder
2. Run `festival` in a terminal. Enter `(voice.list)`. The output must contain
   at least `cmu_us_awb_cg` and `cmu_us_slt_cg`.
   Otherwise you need to edit the table `voicetbl` in the script to refer to voices
   that are installed in your distribution (the function call above list them).
   
## How to use
Run `festival --server` before launching FreeSpace

## Known issues
~~- Does not override other message sounds.~~
~~- Does not yet respect TTS settings in messages.tbl. Only plays when message sound is set to emptymsg.wav
  (Can be temporarily worked around by removing `or fv.Filename:match("emptymsg.wav")` in line 75~~
(The engine now allows scipts to access SimulatedSpeechOverrides)
~~- Needs that buffer file festival_buf1.wav~~
(The engine now allows scipts to play wav data contained in a lua string)
- __Slow to synthesize long messages. Messages will be truncated or canceled if new message arrives meanwhile.__
  I'll try to fix that by splitting or preparing messages now that buffer issue is resolved.
- No support for Command Briefings, Briefings or Debriefings. There might be scripting support for
  getting these texts with the new UI, then I'll try to include them as well.

See also: https://www.hard-light.net/forums/index.php?topic=97279
Contact me there, via PM or when I'm on Discord for any questions or issues!
