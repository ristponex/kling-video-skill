---
name: kling-video
description: Generate AI videos using Kling (Kuaishou) models via Atlas Cloud API. Supports text-to-video, image-to-video, 4K, multi-shot, avatar, motion control. Use when user asks to "generate a video with Kling" or "create a 4K video".
---
# Kling Video Skill

You have access to the `kling-video` CLI tool for generating videos using Kling AI via Atlas Cloud.

## When to Use

Activate this skill when the user:
- Asks to "generate a video", "create a video", or "make a video"
- Mentions "Kling" or "Kling AI"
- Wants to convert an image to video (image-to-video)
- Asks for video editing, motion control, or avatar generation
- Requests text-to-video generation

## Command Format

```bash
kling-video "<prompt>" [options]
```

## Available Options

| Option | Values | Default |
|--------|--------|---------|
| `--model` | See model list below | `kwaivgi/kling-v3.0-pro/text-to-video` |
| `--mode` | `t2v`, `i2v`, `ref`, `edit` | `t2v` |
| `--duration` | `5`, `10` | `5` |
| `--resolution` | `480p`, `720p`, `1080p`, `4k` | `1080p` |
| `--aspect-ratio` | `16:9`, `9:16`, `1:1`, `4:3`, `3:4`, `21:9` | `16:9` |
| `--audio` | (flag, no value) | disabled |
| `--image` | file path | — |
| `--output` | file path | `./output/{timestamp}.mp4` |

## Models

### Text-to-Video
- `kwaivgi/kling-v3.0-pro/text-to-video` — Best quality ($0.204/req)
- `kwaivgi/kling-v3.0-std/text-to-video` — Balanced ($0.102/req)
- `kwaivgi/kling-v2.6-pro/text-to-video` — Proven ($0.168/req)
- `kwaivgi/kling-v2.5-turbo-pro/text-to-video` — Fast ($0.084/req)
- `kwaivgi/kling-o3-pro/text-to-video` — Smooth motion ($0.204/req)
- `kwaivgi/kling-o1/text-to-video` — Cost-effective ($0.102/req)

### Image-to-Video
- `kwaivgi/kling-v3.0-pro/image-to-video` — Best quality ($0.204/req)
- `kwaivgi/kling-v3.0-std/image-to-video` — Balanced ($0.102/req)
- `kwaivgi/kling-v2.6-pro/image-to-video` — Proven ($0.168/req)
- `kwaivgi/kling-o3-pro/image-to-video` — Smooth motion ($0.204/req)

## Usage Examples

### Text-to-Video
```bash
kling-video "A majestic eagle soaring through mountain valleys at golden hour" --duration 10 --resolution 1080p
```

### Image-to-Video
```bash
kling-video "The flowers gently sway in the breeze" --mode i2v --image ./flower.jpg --duration 5
```

### With Audio
```bash
kling-video "Ocean waves crashing on a rocky shore" --audio --duration 10
```

### High Quality Cinematic
```bash
kling-video "Epic dragon flying over medieval castle" --model kwaivgi/kling-v3.0-pro/text-to-video --resolution 4k --aspect-ratio 21:9 --duration 10
```

### Quick Preview
```bash
kling-video "Cat playing with yarn" --model kwaivgi/kling-v2.5-turbo-pro/text-to-video --duration 5
```

## Important Notes

- The `ATLASCLOUD_API_KEY` environment variable must be set
- Image-to-video mode (`--mode i2v`) requires `--image` flag with a valid file path
- Video generation takes 1-5 minutes depending on model and settings
- Output files are saved as `.mp4`
- Always provide descriptive, detailed prompts for best results
- For vertical video (e.g., mobile/social), use `--aspect-ratio 9:16`
- For cinematic widescreen, use `--aspect-ratio 21:9`
