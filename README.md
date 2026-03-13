<div align="center">

# Kling Video Skill

**An open AI agent skill for generating videos using Kling AI via Atlas Cloud API**

[![npm version](https://img.shields.io/npm/v/kling-video-skill.svg)](https://www.npmjs.com/package/kling-video-skill)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stars](https://img.shields.io/github/stars/thoughtincode/kling-video-skill?style=social)](https://github.com/thoughtincode/kling-video-skill)

Generate stunning AI videos directly from your terminal or through AI coding agents (Claude Code, Cursor, Codex, Copilot, Gemini CLI, Windsurf, and more). Powered by Kling AI's state-of-the-art video generation models, accessible through Atlas Cloud's unified API.

</div>

---

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Agent Skill Integration](#agent-skill-integration)
- [CLI Usage](#cli-usage)
- [Model Variants](#model-variants)
- [Options Reference](#options-reference)
- [API Details](#api-details)
- [Examples](#examples)
- [Pricing](#pricing)
- [Take This to Production](#-take-this-to-production-today)
- [License](#license)

---

## Features

- **Text-to-Video (t2v)** — Generate videos from text prompts with cinematic quality
- **Image-to-Video (i2v)** — Animate still images into dynamic video sequences
- **Reference-to-Video (ref)** — Use reference videos to guide style, motion, and composition
- **Video Editing (edit)** — Modify existing videos with text instructions
- **Avatar Generation** — Create talking head videos from a single portrait image
- **Motion Control** — Fine-grained control over camera movement and subject motion
- **Multi-Shot Generation** — Generate multi-scene videos with consistent characters and settings
- **4K Support** — Output videos in resolutions up to 4096x4096
- **Native Audio Generation** — Generate synchronized audio tracks alongside video
- **Agent Skill** — Works with 15+ AI coding agents including Claude Code, Cursor, OpenAI Codex, GitHub Copilot, Gemini CLI, Windsurf, OpenCode, Kiro, and more

---

## Prerequisites

- [Bun](https://bun.sh/) runtime (v1.0+)
- An [Atlas Cloud](https://www.atlascloud.ai?ref=JPM683&utm_source=github&utm_campaign=kling-video-skill) API key

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/thoughtincode/kling-video-skill.git
cd kling-video-skill
```

### 2. Install Dependencies

```bash
bun install
```

### 3. Link the CLI Globally

```bash
bun link
```

This makes the `kling-video` command available system-wide.

### 4. Set Your API Key

```bash
export ATLASCLOUD_API_KEY=your_api_key_here
```

Or create a `.env` file in the project root:

```
ATLASCLOUD_API_KEY=your_api_key_here
```

---

## Agent Skill Integration

This repository is designed to work as an **open agent skill** compatible with 15+ AI coding agents. Install it once and use it across platforms.

### Supported Agents

Claude Code, Cursor, OpenAI Codex, GitHub Copilot, Gemini CLI, Windsurf, OpenCode, Kiro, and more.

### How It Works

1. Clone this repo and run `bun link`
2. Load the skill in your agent (e.g., run `/init` in Claude Code, or follow your agent's skill loading process)
3. Use natural language to generate videos:

```
"Generate a 5-second video of a sunset over the ocean with gentle waves"
```

```
"Create a video from this image: ./photo.jpg — make the clouds move slowly"
```

```
"Make a 10-second cinematic video of a futuristic city at night using Kling v3.0 Pro"
```

Your AI coding agent will automatically construct and execute the appropriate `kling-video` CLI command based on your natural language request.

---

## CLI Usage

### Basic Text-to-Video

```bash
kling-video "A majestic eagle soaring through mountain valleys at golden hour"
```

### Image-to-Video

```bash
kling-video "The flowers gently sway in the breeze" --mode i2v --image ./flower.jpg
```

### Specify Model and Duration

```bash
kling-video "Cyberpunk city street with neon reflections in rain puddles" \
  --model kwaivgi/kling-v3.0-pro/text-to-video \
  --duration 10
```

### Full Options Example

```bash
kling-video "A time-lapse of storm clouds forming over a desert landscape" \
  --model kwaivgi/kling-v3.0-pro/text-to-video \
  --mode t2v \
  --duration 10 \
  --resolution 1080p \
  --aspect-ratio 16:9 \
  --audio \
  --output ./storm-timelapse.mp4
```

### Reference-to-Video

```bash
kling-video "Recreate this scene with autumn colors" \
  --mode ref \
  --image ./reference-scene.mp4
```

### Video Editing

```bash
kling-video "Add dramatic lightning flashes to the sky" \
  --mode edit \
  --image ./original-video.mp4
```

---

## Model Variants

Kling AI offers multiple model variants through Atlas Cloud, each optimized for different use cases:

| Model | Model ID | Starting Price per Second | Speed | Quality | Best For |
|-------|----------|--------------------------|-------|---------|----------|
| **Kling v3.0 Pro** | `kwaivgi/kling-v3.0-pro/text-to-video` | from $0.204/s | Medium | Highest | Production-quality cinematic videos |
| **Kling v3.0 Standard** | `kwaivgi/kling-v3.0-std/text-to-video` | from $0.102/s | Fast | High | Balanced quality and speed |
| **Kling v2.6 Pro** | `kwaivgi/kling-v2.6-pro/text-to-video` | from $0.168/s | Medium | Very High | Proven reliability, complex scenes |
| **Kling v2.5 Turbo Pro** | `kwaivgi/kling-v2.5-turbo-pro/text-to-video` | from $0.084/s | Very Fast | Good | Rapid iteration, previews |
| **Kling O3 Pro** | `kwaivgi/kling-o3-pro/text-to-video` | from $0.204/s | Medium | Highest | Optimized motion, smooth animation |
| **Kling O1** | `kwaivgi/kling-o1/text-to-video` | from $0.102/s | Fast | High | General purpose, cost-effective |

### Image-to-Video Variants

| Model | Model ID | Starting Price per Second |
|-------|----------|--------------------------|
| **Kling v3.0 Pro i2v** | `kwaivgi/kling-v3.0-pro/image-to-video` | from $0.204/s |
| **Kling v3.0 Std i2v** | `kwaivgi/kling-v3.0-std/image-to-video` | from $0.102/s |
| **Kling v2.6 Pro i2v** | `kwaivgi/kling-v2.6-pro/image-to-video` | from $0.168/s |
| **Kling O3 Pro i2v** | `kwaivgi/kling-o3-pro/image-to-video` | from $0.204/s |

> **Default model:** `kwaivgi/kling-v3.0-pro/text-to-video`

---

## Options Reference

| Option | Flag | Default | Description |
|--------|------|---------|-------------|
| **Prompt** | (positional) | *required* | Text description of the video to generate |
| **Model** | `--model` | `kwaivgi/kling-v3.0-pro/text-to-video` | Model variant to use (see table above) |
| **Mode** | `--mode` | `t2v` | Generation mode: `t2v`, `i2v`, `ref`, `edit` |
| **Duration** | `--duration` | `5` | Video duration in seconds (5, 10) |
| **Resolution** | `--resolution` | `1080p` | Output resolution: `480p`, `720p`, `1080p`, `4k` |
| **Aspect Ratio** | `--aspect-ratio` | `16:9` | Video aspect ratio: `16:9`, `9:16`, `1:1`, `4:3`, `3:4`, `21:9` |
| **Audio** | `--audio` | `false` | Enable native audio generation |
| **Image** | `--image` | — | Input image path for i2v/ref/edit modes |
| **Output** | `--output` | `./output/{timestamp}.mp4` | Output file path |

---

## API Details

This CLI interacts with the Atlas Cloud API to submit video generation jobs and poll for results.

### Workflow

1. **Submit Job** — POST request to create a prediction
2. **Poll Status** — GET request to check prediction status every 5 seconds
3. **Download** — Fetch the completed video and save locally

### Endpoints

```
POST   https://api.atlascloud.ai/api/v1/model/prediction
GET    https://api.atlascloud.ai/api/v1/model/prediction/{request_id}
```

### Authentication

All requests require the `ATLASCLOUD_API_KEY` header:

```
Authorization: Bearer YOUR_API_KEY
```

### Request Body Example (Text-to-Video)

```json
{
  "model": "kwaivgi/kling-v3.0-pro/text-to-video",
  "input": {
    "prompt": "A cinematic shot of a dragon flying over a medieval castle",
    "duration": 5,
    "resolution": "1080p",
    "aspect_ratio": "16:9",
    "audio_generation": false
  }
}
```

### Request Body Example (Image-to-Video)

```json
{
  "model": "kwaivgi/kling-v3.0-pro/image-to-video",
  "input": {
    "prompt": "The clouds move slowly across the sky",
    "image_url": "https://example.com/image.jpg",
    "duration": 5,
    "resolution": "1080p",
    "aspect_ratio": "16:9"
  }
}
```

### Response Example

```json
{
  "request_id": "abc123-def456",
  "status": "completed",
  "output": {
    "video_url": "https://cdn.atlascloud.ai/videos/abc123.mp4"
  },
  "cost": {
    "amount": 0.204,
    "currency": "USD"
  }
}
```

---

## Examples

### 1. Product Demo Video

```bash
kling-video "A sleek smartphone rotating 360 degrees on a dark reflective surface, \
studio lighting with subtle color accents, premium product showcase" \
  --duration 5 --resolution 1080p --aspect-ratio 9:16
```

### 2. Nature Scene

```bash
kling-video "Aerial drone shot of autumn forest with a winding river, \
morning mist rising through golden and red canopy, cinematic color grading" \
  --duration 10 --resolution 1080p --aspect-ratio 21:9
```

### 3. Social Media Content

```bash
kling-video "A barista doing latte art in slow motion, \
warm cafe ambience, shallow depth of field, Instagram aesthetic" \
  --duration 5 --aspect-ratio 9:16 --audio
```

### 4. Animate a Photo

```bash
kling-video "The subject smiles and turns their head slightly to the right, \
wind blows through their hair" \
  --mode i2v --image ./portrait.jpg --duration 5
```

### 5. Cinematic Landscape

```bash
kling-video "Epic wide shot of volcanic eruption at night, \
lava flowing down the mountainside, lightning in the ash cloud, \
National Geographic documentary style" \
  --model kwaivgi/kling-v3.0-pro/text-to-video \
  --duration 10 --resolution 4k --aspect-ratio 21:9
```

### 6. Avatar / Talking Head

```bash
kling-video "The person delivers a confident TED talk presentation, \
natural gestures and facial expressions" \
  --mode i2v --image ./headshot.jpg --duration 10 --audio
```

### 7. Multi-Shot Sequence

```bash
# Scene 1: Establishing shot
kling-video "Wide establishing shot of a cyberpunk megacity, \
flying cars and holographic billboards" \
  --duration 5 --output ./scene1.mp4

# Scene 2: Street level
kling-video "Street-level POV walking through neon-lit alleyways, \
steam rising from vents, holographic street vendors" \
  --duration 5 --output ./scene2.mp4

# Scene 3: Close-up
kling-video "Close-up of a cybernetic eye powering on with blue light, \
reflection of the city visible in the iris" \
  --duration 5 --output ./scene3.mp4
```

### 8. Motion-Controlled Camera

```bash
kling-video "Smooth dolly zoom through a grand library with infinite bookshelves, \
camera slowly pushing forward while zooming out, Vertigo effect, \
warm ambient lighting with dust particles in the air" \
  --duration 10 --resolution 1080p
```

### 9. Video Editing

```bash
kling-video "Transform the daytime scene to nighttime, \
add moonlight and stars, turn on the building lights" \
  --mode edit --image ./daytime-city.mp4
```

### 10. Batch Generation Script

```bash
#!/bin/bash
prompts=(
  "Ocean waves crashing on rocky coastline at sunset"
  "Cherry blossoms falling in slow motion in a Japanese garden"
  "Northern lights dancing over a frozen lake in Iceland"
  "Time-lapse of clouds forming and dissolving over mountains"
)

for i in "${!prompts[@]}"; do
  kling-video "${prompts[$i]}" \
    --duration 5 \
    --resolution 1080p \
    --output "./output/batch_${i}.mp4"
done
```

---

## Pricing

### Kling AI on Atlas Cloud

| Model Variant | Starting Price per Second | Duration | Resolution |
|--------------|--------------------------|----------|------------|
| Kling v3.0 Pro | **from $0.204/s** | 5-10s | Up to 4K |
| Kling v3.0 Standard | from $0.102/s | 5-10s | Up to 1080p |
| Kling v2.6 Pro | from $0.168/s | 5-10s | Up to 1080p |
| Kling v2.5 Turbo Pro | from $0.084/s | 5s | Up to 1080p |
| Kling O3 Pro | from $0.204/s | 5-10s | Up to 4K |
| Kling O1 | from $0.102/s | 5-10s | Up to 1080p |

*Prices shown are starting prices. Higher resolution or longer duration may cost more.*

### Volume Estimates

| Volume | Kling v3.0 Pro | Kling v3.0 Std | Kling v2.5 Turbo |
|--------|---------------|----------------|-----------------|
| 100 videos | $20.40 | $10.20 | $8.40 |
| 500 videos | $102.00 | $51.00 | $42.00 |
| 1,000 videos | $204.00 | $102.00 | $84.00 |

### First-Time Bonus

Atlas Cloud offers a **25% bonus on your first recharge** (up to $100 bonus):

| Top-Up | Bonus (25%) | Total Credits | Effective Rate (v3.0 Pro) |
|--------|-------------|---------------|--------------------------|
| $10 | $2.50 | $12.50 | from $0.163/s |
| $50 | $12.50 | $62.50 | from $0.163/s |
| $100 | $25.00 | $125.00 | from $0.163/s |
| $400 | $100.00 | $500.00 | from $0.163/s |

---

## Take This to Production Today

This workflow is optimized for Atlas Cloud. Move from experiment to enterprise-ready scale.

- **Production-Ready**: 20+ Kling model variants, from $0.204/s
- **Enterprise Security**: SOC I & II Certified | HIPAA Compliant
- **Zero Maintenance**: Serverless architecture — focus on your product, not the servers
- **25% Bonus**: First recharge bonus up to $100

[Start Building](https://www.atlascloud.ai?ref=JPM683&utm_source=github&utm_campaign=kling-video-skill)

---

## Troubleshooting

### Common Issues

**`ATLASCLOUD_API_KEY` not set**
```
Error: ATLASCLOUD_API_KEY environment variable is required
```
Set the environment variable or create a `.env` file.

**Prediction timeout**
```
Error: Prediction timed out after 300 seconds
```
Video generation can take 1-5 minutes. The default timeout is 300 seconds. For complex prompts or higher resolutions, the generation may take longer.

**Invalid model ID**
```
Error: Model not found
```
Check the [Model Variants](#model-variants) table for valid model IDs.

**Image file not found (i2v mode)**
```
Error: Image file not found: ./photo.jpg
```
Ensure the image path is correct and the file exists.

---

## Architecture

```
kling-video-skill/
├── src/
│   └── cli.ts          # Main CLI entry point
├── output/             # Default output directory for generated videos
├── CLAUDE.md           # Claude Code skill definition
├── package.json        # Package configuration
├── .env.example        # Environment variable template
├── .gitignore          # Git ignore rules
├── LICENSE             # MIT License
└── README.md           # This file
```

---

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built for the open agent skills ecosystem — works with Claude Code, Cursor, Codex, Copilot, Gemini CLI, Windsurf, OpenCode, Kiro, and 15+ AI coding agents. Powered by [Atlas Cloud](https://www.atlascloud.ai?ref=JPM683&utm_source=github&utm_campaign=kling-video-skill).**

</div>
