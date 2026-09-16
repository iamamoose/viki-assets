# VIKI Assets

Downloadable bits for [VIKI](https://github.com/iamamoose/viki), the
mildly judgemental Home Assistant voice assistant.

The big files live in [Releases](../../releases/latest) — grab the
latest one and take what you need. Everything else is here in the repo:
configs, sounds, and the sources for rebuilding it all yourself.

## Voices

A folder per voice in [`voices/`](voices). Right now there's one:

- **viki** — southern English, early twenties, quick and clipped.

Each holds the Piper config and the noises that voice makes — everything
except the model itself, which is too big for git.

Download `viki-voice-<version>.zip` from the release and unzip it. You
get the same folder with the `.onnx` filled in, ready to use.

The `.onnx` and `.json` go together — same folder, same name — because
Piper finds the config by sticking `.json` on the end of the model path.
For the Home Assistant Piper add-on that's usually `/share/piper/`, then
restart it. The wavs don't go there; see below.

```bash
echo "Your kettle has boiled." | piper --model en_US-viki-medium.onnx --output_file test.wav
```

There's no human voice donor anywhere in this. We wrote a description of
a voice, Qwen3-TTS made one up, and we trained Piper on it. See
[Voice](docs/voice.md) for how, and what to avoid.

## Sounds

The wavs alongside each voice are the noises she makes that aren't words
— currently `mhmm.wav`, the affirmative grunt. They live with the voice
because they're cloned from it, so each voice needs its own.

Play these as media files, not through TTS. espeak reads "mhmm" as "em
aitch em em", which is not the effect we were after. See
[Sounds](docs/sounds.md).

## Source

[`src/`](src) mirrors the folders above. [`src/voices/`](src/voices) has
the scripts, the 416-line training script, and the reference clip VIKI's
voice was cloned from. That last one matters: regenerating from the
prompt gives you a *similar* voice, not this one.

## Licence

[CC BY-SA 4.0](LICENSE) — use it, change it, sell it if you like, just
credit us and share changes under the same licence.

We can offer that because nothing upstream stops us. The Piper base
checkpoint is LJSpeech (public domain), Piper and TextyMcSpeechy are
MIT, Qwen3-TTS is Apache-2.0, and the voice itself was invented rather
than recorded.

```
VIKI voice — https://github.com/iamamoose/viki-assets — CC BY-SA 4.0
```
