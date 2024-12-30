What's the matter?

MIDI 1.0 only has 16 channels: 1..16. Channel 10 is reserved for unpitched drums, that leaves you with 15 pitched channels.

If you export orchestral score with more than 15 pitched instruments from MuseScore to MIDI, it will put several instruments onto a single channel. If they sound simultaneously, it'll mess the timbres.

Even you there isn't too many instruments, there's a MuseScore bug that often sets strings to pizzicato.

Moreover, MuseScore's MIDI export generates a lot of Breath CC 2 which bloats the MIDI file size and crashes Chip-Player-JS's player.

Therefore, we need some scripting.

As a source, export all parts from MuseScore to MIDI separately. Then we'll merge those parts with a script.

The script should decide on two things:
– which instrument parts are merged into a single channel
– which single PC for setting a GM instrument is set at the very beginning of that channel in place of all other PC commands in the source tracks.

Here's a script that I've used to merge [Copland 3/1](https://rawl.rocks/f/copland_symphony_3_mov_1_rewired): https://gist.github.com/vpavlenko/31c35ec331dccf14ad1e0f1d5dd71ac5
