# fs2-festival-tts
Script to forward FSO messages to Festival and play speech

## How to install
Software requirements:
- lua-socket for Lua 5.1 (Provided by `lua51-socket` on Arch, `lua-socket` on Debian/Ubuntu)
- Festival, the free and open source TTS engine (provided by `festival` on Arch and Debian/Ubuntu)
- voices for festival (provided by `festival-us` on Arch, ? on Debian/Ubuntu)

1. Merge the data folder with the one in your top knossos or freespcae folder.
2. Adjust the variable `rotten-portability-path` to your actual knossos or freespace folder.
   **The file festival_buf1.wav in that folder will be written to!**
3. Run `festival` in a terminal. Enter `(voice.list)`. The output must contain
   at least `cmu_us_awb_cg` and `cmu_us_slt_cg`.
   Otherwise you need to edit the table `voicetbl` in the script to refer to voices
   that are installed in your distribution.
   
## How to use
Run `festival --server` before launching FreeSpace

## Known issues
- Does not override other message sounds.
- Does not yet respect TTS settings in messages.tbl. Only plays when message sound is set to emptymsg.wav
  (Can be temporarily worked around by removing `or fv.Filename:match("emptymsg.wav")` in line 75
- Needs that buffer file festival_buf1.wav
- __Slow to synthesize long messages. Messages will be truncated or canceled if new message arrives meanwhile.__
  I'll try to fix that by splitting or preparing messages when that buffer issue is resolved.

See also: https://www.hard-light.net/forums/index.php?topic=97279
Contact me there, via PM or when I'm on Discord for any questions or issues!
