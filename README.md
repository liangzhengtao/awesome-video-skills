# 🎬 Awesome Video Skills

> Stop googling FFmpeg commands. Write the skill once. Edit videos with AI forever.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

**[English](#english)** | **[中文](#中文)**

</div>

---

<a name="english"></a>

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

<a name="中文"></a>

<div id="中文">

# 🎬 Awesome Video Skills — 中文版

> 别再谷歌 FFmpeg 命令了。把技能写一次，让 AI 永远帮你剪视频。

## 问题

你每次做项目都要花**大量时间**搜索 FFmpeg 参数、查 DaVinci Resolve 快捷键、重写同样的字幕脚本。你的 AI 助手不知道你的工作流、你的预设、你的偏好。

## 解决方案

把你的视频编辑知识写成 **AI 技能**。你的 AI 助手读取技能后，能生成完全正确的命令行、预设或脚本 — 每次都是。

## 全部技能

| 分类 | 技能 | 说明 |
|------|------|------|
| 视频剪辑 | FFmpeg Master | 剪切、合并、转换、压缩 — 完整 FFmpeg 流水线自动化 |
| 视频剪辑 | DaVinci Resolve | 调色、Fusion 特效、Fairlight 音频、输出预设 |
| 视频剪辑 | Premiere Pro | 序列设置、导出预设、Dynamic Link、Essential Graphics |
| 特效制作 | Motion Graphics | After Effects 表达式、CSS 动画、Lottie 模板 |
| 特效制作 | AI Video Generation | Runway、Pika、Sora 提示词工程与后期处理 |
| 字幕处理 | Subtitle Generation | Whisper 转录、SRT/ASS 格式、字幕烧录 |
| 字幕处理 | Translation Subtitles | 多语言字幕流水线、双语字幕、质量检查 |
| 音频处理 | Audio Mixing | 降噪、EQ、压缩、标准化、背景音乐混音 |
| 发布优化 | YouTube Optimization | SEO 标题、缩略图设计、标签、分析、发布排期 |
| 发布优化 | Multi-Platform Publish | YouTube、TikTok、Bilibili、Instagram — 规格、批量导出 |

## 快速开始

```bash
# 复制技能到你的项目
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/

# 然后自然地问你的 AI 助手：
# "把这个视频压缩到 50MB 以内"
# "给这个视频生成中文字幕"
# "把我的 YouTube 视频做成抖音版本"
```

## 参与贡献

欢迎提交新的视频技能！详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 相关项目

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — 各领域 AI 技能精选合集
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — AI 编程助手规则配置
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — AI 技能质量验证工具
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — AI 驱动的 Git 提交信息生成
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — MCP 服务器合集

## 许可证

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

</div>
