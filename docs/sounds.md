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

Cloned from the same `voices/viki/reference.wav` the voice was trained on, so it matches her timbre.

We generated 72 takes across six spellings and twelve seeds, then picked
the right one!

## Using them

Play as media, not TTS. In Home Assistant that's
`media_player.play_media`, not `tts.speak`.

Two rates: `mhmm.wav` at 24kHz is the original, `mhmm-22050.wav` matches
the voice model for players that dislike switching between the two.

## Making more

Same method works for a sigh, a sniff, an "ahem". Clone from the
reference, generate a few dozen takes across several spellings and
seeds, and pick by measurement — the spread between seeds is much wider
than you'd guess, and the first take is almost never the best one.
