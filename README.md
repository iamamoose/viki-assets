# VIKI Assets

Downloadable bits for [VIKI](https://github.com/iamamoose/viki), the
mildly judgemental Home Assistant voice assistant.

The big files live in [Releases](../../releases/latest). Grab the
latest one and take what you need. Everything else is here in the repo:
configs, sounds, and the sources for rebuilding it all yourself.

## Voices

A folder per voice in [`voices/`](voices). Right now there's one:

- **viki** — default anime judgemental home assistant

Each holds the Piper config and the noises that voice makes (everything
except the model itself, which is too big for git).

Download `viki-voice-<version>.zip` from the release and unzip it. You
get the same folder with the `.onnx` filled in, ready to use.

The `.onnx` and `.json` go together. For Home Assistant Piper add-on
that's in `/share/piper/`, then restart it. The wavs don't go
there; see below.

Quick local test:
```bash
echo "Your kettle has boiled." | piper --model en_US-viki-medium.onnx --output_file test.wav
```

There's no human voice donor anywhere in this. We wrote a description
of a voice, Qwen3-TTS made one up, and we trained Piper on it. Want to
make your own? [Full recipe](https://github.com/iamamoose/viki/blob/main/docs/make-your-own-voice.md), including what to avoid.

Our original Viki model used Index-TTS2 to clone a voice, and the license
isn't as permissive, so we've redone it from scratch using Qwen3-TTS instead.

## Sounds

The wavs alongside each voice are the noises she makes that aren't
words; currently `mhmm.wav`, the noise to show she's listening to
you. They live with the voice because they're cloned from it, so each
voice needs its own.

Play these as media files, not through TTS. espeak reads "mhmm" as "em
aitch em em", which is not the effect we were after. See
[Sounds](docs/sounds.md).

## Rebuilding her

`voices/viki/reference.wav` is the clip her voice was cloned from. That
one matters: regenerating from the prompt gives you a *similar* voice,
not this one.

The scripts and the walkthrough live in the main VIKI_ repo — see
[Make your own VIKI_ voice](https://github.com/iamamoose/viki/blob/main/docs/make-your-own-voice.md). They're code, so they sit under that
repo's Apache-2.0 rather than the CC licence here.

## Licence

[CC BY-SA 4.0](LICENSE) — use it, change it, sell it if you like, just
credit us and share changes under the same licence.

Licence note: The Piper base checkpoint is LJSpeech (public domain),
Piper and TextyMcSpeechy are MIT, Qwen3-TTS is Apache-2.0, and the
voice itself was invented rather than recorded.

```
VIKI assets — https://github.com/iamamoose/viki-assets — CC BY-SA 4.0
```
