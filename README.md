# VIKI Assets

Downloadable bits for [VIKI](https://github.com/iamamoose/viki), the
mildly judgemental Home Assistant voice assistant.

Configs and sounds are in the repo; the model itself is too big for git,
so it ships in [Releases](../../releases/latest).

## Voices

A folder per voice in [`voices/`](voices). Right now there's one:

- **viki** — default anime judgemental home assistant

Download `viki-voice-<version>.zip` from the release and unzip it. You
get that folder with the `.onnx` filled in.

The `.onnx` and `.json` go together — for the Home Assistant Piper
add-on that's `/share/piper/`, then restart it. The wavs don't go there;
see below.

```bash
echo "Your kettle has boiled." | piper --model en_US-viki-medium.onnx --output_file test.wav
```

## Sounds

The wavs beside each voice are the noises she makes that aren't words —
currently `mhmm.wav`, to show she's listening. They're cloned from the
voice, so each voice needs its own.

Play them as media, not TTS: in Home Assistant `media_player.play_media`,
not `tts.speak`. espeak reads "mhmm" as "em aitch em em".

`mhmm.wav` is 24kHz; `mhmm-22050.wav` matches the voice model for
players that dislike switching rates.

## Making your own

`voices/viki/reference.wav` is the clip VIKI_'s voice was cloned from —
keep it if you want *this* voice, since the prompt alone only gets you a
similar one.

Everything else is in the main repo: [Make your own VIKI_
voice](https://github.com/iamamoose/viki/blob/main/docs/make-your-own-voice.md).

## Licence

[CC BY-SA 4.0](LICENSE) — use it, change it, sell it if you like, just
credit us and share changes under the same licence.

We can offer that because nothing upstream stops us: the Piper base
checkpoint is LJSpeech (public domain), Piper and TextyMcSpeechy are
MIT, Qwen3-TTS is Apache-2.0, and the voice was invented rather than
recorded.

```
VIKI assets — https://github.com/iamamoose/viki-assets — CC BY-SA 4.0
```
