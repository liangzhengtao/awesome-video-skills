[中文版](README.zh.md)
n<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> Stop googling FFmpeg commands. Write the skill once. Edit videos with AI forever.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

</div>

---



## The Problem

You spend **hours** googling FFmpeg flags, looking up DaVinci Resolve shortcuts, and re-writing the same subtitle scripts — every single project. Your AI assistant doesn't know your workflow, your presets, or your preferences.

## The Solution

Write your video editing knowledge as **AI skills** once. Your AI assistant reads the skill and generates exactly the right pipeline, preset, or script — every time.

<div align="center">

| ❌ Without Skill | ✅ With Skill |
|:---:|:---:|
| 30 min googling FFmpeg flags | "Compress this for YouTube" → perfect command |
| Manually resizing for 5 platforms | One-click batch export for all platforms |
| Re-writing subtitle scripts | AI generates the exact Whisper pipeline you want |
| Guessing YouTube SEO | Structured title/description/tag optimization |

</div>

---

## Skills

### 视频剪辑 (Video Editing)

| Skill | Description | File |
|-------|-------------|------|
| 🎥 FFmpeg Master | Cut, merge, convert, compress — full FFmpeg pipeline automation | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | Color grading, Fusion VFX, Fairlight audio, delivery presets | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | Sequence setup, export presets, Dynamic Link, Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作 (Effects)

| Skill | Description | File |
|-------|-------------|------|
| ✨ Motion Graphics | After Effects expressions, CSS animations, Lottie templates | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI Video Generation | Runway, Pika, Sora prompt engineering and post-processing | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕处理 (Subtitles)

| Skill | Description | File |
|-------|-------------|------|
| 📝 Subtitle Generation | Whisper transcription, SRT/ASS formatting, subtitle burning | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Translation Subtitles | Multilingual subtitle pipelines, bilingual overlays, QA | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### 音频处理 (Audio)

| Skill | Description | File |
|-------|-------------|------|
| 🎵 Audio Mixing | Noise removal, EQ, compression, normalization, music mixing | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 发布优化 (Publishing)

| Skill | Description | File |
|-------|-------------|------|
| 📈 YouTube Optimization | SEO titles, thumbnail design, tags, analytics, upload scheduling | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Multi-Platform Publish | YouTube, TikTok, Bilibili, Instagram — specs, batch export, automation | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## Quick Start

### Cursor

Copy any skill file to your project's `.cursorrules` or `.cursor/rules/` directory:

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

Or reference multiple skills:

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

Add skills as project context in your `CLAUDE.md`:

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

Copy skill files to your project root or `.kimi/` directory:

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### Using Skills

Once installed, just ask your AI assistant naturally:

```
"Compress this video to under 50MB for email"
"Generate Chinese subtitles for this interview"
"Create a TikTok version of my YouTube video"
"Optimize my YouTube title and description for SEO"
"Mix background music under this voiceover at -18dB"
```

---

## Contributing

We welcome new video skills! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Quick way to contribute:
1. Fork this repo
2. Add your skill in the appropriate category under `skills/`
3. Follow the skill template format (When to Use, Instructions, Templates, Pitfalls)
4. Submit a PR

---

## See Also

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — Curated collection of AI skills for every domain
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — AI rules and configurations for coding assistants
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — Validate and test your AI skill quality
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — AI-powered git commit message generation
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — Model Context Protocol servers for AI tools

---

## License

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
