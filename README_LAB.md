# Irodori-TTS Lab

This is a local lab copy of <https://github.com/Aratako/Irodori-TTS> for trying VoiceDesign inference.

## Setup

```bash
cd /Users/kakuayato/my-company/irodori-tts-lab
uv sync
```

The environment has already been created on this machine. Apple Silicon MPS is available, so the default runtime device is `mps`.

## Notebook

```bash
cd /Users/kakuayato/my-company/irodori-tts-lab
uv run python -m ipykernel install --user --name irodori-tts-lab --display-name "Irodori TTS Lab"
```

Then open:

```text
notebooks/irodori_voice_design_lab.ipynb
```

The notebook uses `Aratako/Irodori-TTS-500M-v2-VoiceDesign` and generates the same self-introduction with caption presets such as:

- confident and clear
- confident and calm
- nervous and mumbling
- shy and soft

Generated wav files are written to:

```text
outputs/voice_design_lab/
```

## Quick CLI Smoke Test

```bash
uv run python infer.py \
  --hf-checkpoint Aratako/Irodori-TTS-500M-v2-VoiceDesign \
  --text "はじめまして。私は彩人です。研究と開発を通じて、人の思考を助ける道具を作っています。" \
  --caption "明るく自信に満ちた若い男性の声。ハキハキと、語尾まで明瞭に、堂々と自己紹介してください。" \
  --no-ref \
  --num-steps 12 \
  --output-wav outputs/smoke_confident.wav
```

For better quality, increase `--num-steps` to `32` or `40`.
