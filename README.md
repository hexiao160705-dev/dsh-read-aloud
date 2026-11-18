# dsh-read-aloud (renamed)

> **This repository is superseded.** The plugin was renamed to **`dsh-read-aloud-edge`** because the name `dsh-read-aloud` is already taken on npm by an unrelated plugin.
>
> Use https://github.com/hexiao160705-dev/dsh-read-aloud-edge instead:
>
> ```bash
> dsh plugin --profile desktop add github:hexiao160705-dev/dsh-read-aloud-edge
> ```

Read assistant replies aloud in **DeepSeek Harness (DSH)**, with **1×–4×** playback speed.

DSH ships speech-to-text (voice input) but no text-to-speech model. This plugin uses the locally installed **edge-tts** (Microsoft Edge online voices) to synthesize the reply, then plays it in a small player with speed control.

## Features

- Speaker button in every assistant reply's action row
- Reads only the reply text, not tool cards or reasoning
- Player with play/pause, progress, and **1× / 1.25× / 1.5× / 2× / 2.5× / 3× / 4×**
- Pitch is preserved when speeding up (`preservesPitch`)
- Audio is cached under `~/.dsh/read-aloud/cache/` by a content hash
- Chinese text uses `zh-CN-XiaoxiaoNeural`; English text uses `en-US-AriaNeural`

## Requirements

- `edge-tts` installed and on one of the known paths, or set `EDGE_TTS_PATH`
- Network access to the Edge TTS service (the reply text is sent to Microsoft's TTS endpoint)

Install:

```bash
pip install edge-tts
# or
uv tool install edge-tts
```

## Privacy

- The host reads the text from the request, synthesizes it through `edge-tts`, and returns only a cache id + audio URL.
- No API key, account id, or token is read or sent.
- `edge-tts` sends the text to Microsoft's online TTS service; the audio is cached locally. If the reply must not leave the machine, do not use this plugin (a local TTS engine would be needed).
- Cache files stay under `~/.dsh/read-aloud/cache/`; delete that directory to clear them.

## License

MIT
