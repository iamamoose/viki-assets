# Sounds

The noises VIKI makes that aren't words. Right now that's `mhmm.wav`,
the noise to show she's woken up and listening.

They live in `voices/<name>/` next to the voice they came from — each is
cloned from that voice, so a new voice needs its own.

These are files, not text we send to the voice. That's deliberate.

## Why not just say "mhmm"?

Because espeak, which Piper uses to turn text into phonemes, doesn't
recognise most spellings of a hum and reads them out as letters:

```
mhm     ->  ,Em,eItS'Em      "em aitch em"
mhmm    ->  ,Em,eItS,Em'Em   "em aitch em em"
Mm      ->  ,Em'Em           "em em"
Hm      ->  ,eItS'Em         "aitch em"
```

Three spellings actually hum:

```
Hmm     ->  h'@m
Uh-huh  ->  'Vh'V
M-hmm   ->  'Emh@m           the letter M, then a hum
```

So `Hmm.` works if you want to generate one live. Everything that looks
more like the noise you want gets spelled out. A recorded file sidesteps
the whole problem.

## How this one was made

Cloned from the same `voices/viki/reference.wav` the voice was trained
on, so it matches her timbre. We generated 72 takes across six spellings
and twelve seeds, then picked the right one.

Making one for your own voice: [Make your own VIKI_ voice](https://github.com/iamamoose/viki/blob/main/docs/make-your-own-voice.md).

## Using them

Play as media, not TTS. In Home Assistant that's
`media_player.play_media`, not `tts.speak`.

Two rates: `mhmm.wav` at 24kHz is the original, `mhmm-22050.wav` matches
the voice model for players that dislike switching between the two.
