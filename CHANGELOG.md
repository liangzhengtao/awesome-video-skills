# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-08-17

### Added

#### 视频剪辑 (Video Editing)
- `ffmpeg-master.md` — Complete FFmpeg video editing skill with cut/merge/compress templates, hardware acceleration (NVENC, QSV, VideoToolbox, AMF), batch processing, speed change, resolution scaling, and GIF conversion.
- `davinci-resolve.md` — DaVinci Resolve workflow covering all 7 pages (Media, Cut, Edit, Fusion, Color, Fairlight, Deliver), node-based color grading, Fusion VFX templates, Fairlight audio mixing, and export presets.
- `premiere-pro.md` — Adobe Premiere Pro skill with sequence settings for all platforms, Media Encoder export presets, Dynamic Link workflows, Essential Graphics templates, proxy workflow, and Lumetri color correction.

#### 特效制作 (Effects)
- `motion-graphics.md` — Motion graphics and animation skill with 30+ After Effects expressions, CSS keyframe animations, Lottie export workflow, lower third templates, and transition library.
- `ai-video-generation.md` — AI video generation skill covering Runway Gen-3, Pika, Sora, Kling, and more. Includes the STRUCTURE prompt engineering method, image-to-video prompts, AI upscaling pipeline, and style transfer workflows.

#### 字幕处理 (Subtitles)
- `subtitle-generation.md` — Automatic subtitle generation with Whisper setup and configuration, SRT/ASS format reference, FFmpeg subtitle burning with custom styling, batch processing, and bilingual subtitle templates.
- `translation-subtitles.md` — Subtitle translation skill with automated Python pipeline, language reading speed reference table, bilingual ASS templates, glossary management, and translation QA checklist.

#### 音频处理 (Audio)
- `audio-mixing.md` — Audio processing and mixing skill with FFmpeg audio filter chains, Python/pydub processing pipeline, music mixing with sidechain ducking, Audacity processing chains, and sound effects library organization.

#### 发布优化 (Publishing)
- `youtube-optimization.md` — YouTube SEO and optimization with title formulas, description templates, thumbnail design guide, tag research strategy, upload scheduling, and analytics dashboard.
- `multi-platform-publish.md` — Multi-platform publishing for YouTube, TikTok, Bilibili, Instagram, Douyin, LinkedIn, Twitter/X, and WeChat Video Channel. Includes platform specs table, FFmpeg batch export script, metadata adaptation matrix, and content repurposing pipeline.

#### Community Files
- `README.md` — Bilingual (English + Chinese) project documentation with hooks, before/after comparison, skills table, quick start guides for Cursor, Claude Code, and Kimi Code, and See Also links.
- `CONTRIBUTING.md` — Bilingual contribution guidelines with skill file template and requirements.
- `CODE_OF_CONDUCT.md` — Contributor Covenant Code of Conduct v2.0.
- `SECURITY.md` — Security policy for responsible disclosure.
- `LICENSE` — MIT License.
- `CHANGELOG.md` — This file.
- `.gitignore` — Git ignore rules for media files, IDE files, and build outputs.
- `.github/workflows/ci.yml` — CI pipeline for markdown linting, link checking, and skill file validation.
- `.github/ISSUE_TEMPLATE/request_skill.md` — Issue template for requesting new skills.
- `.github/pull_request_template.md` — PR template for skill contributions.

### Notes
- Initial release with 10 video production skills across 5 categories.
- All skill files follow a consistent structure: When to Use, Instructions for AI Assistant, Templates, Common Patterns, Pitfalls to Avoid.
- Each skill file is 100+ lines with practical, copy-paste-ready templates.
