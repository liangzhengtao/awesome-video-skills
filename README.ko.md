[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> FFmpeg 명령어를 검색하는 건 그만. 스킬을 한 번 작성하세요. AI로 영상을 영원히 편집하세요.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

</div>

---



## 문제점

매 프로젝트마다 FFmpeg 플래그를 **시간** 동안 검색하고, DaVinci Resolve 단축키를 찾아보고, 동일한 자막 스크립트를 반복 작성합니다. AI 어시스턴트는 여러분의 워크플로우, 프리셋, 선호도를 알지 못합니다.

## 해결책

영상 편집 지식을 **AI 스킬**로 한 번만 작성하세요. AI 어시스턴트가 스킬을 읽고 정확히 맞는 파이프라인, 프리셋, 스크립트를 매번 생성해 줍니다.

<div align="center">

| ❌ 스킬 없이 | ✅ 스킬과 함께 |
|:---:|:---:|
| FFmpeg 플래그 검색에 30분 | "이걸 유튜브용으로 압축해 줘" → 완벽한 명령어 |
| 5개 플랫폼에 수동 리사이징 | 원클릭 일괄 내보내기로 모든 플랫폼 |
| 자막 스크립트 반복 작성 | AI가 원하는 Whisper 파이프라인 정확히 생성 |
| 유튜브 SEO 추측 | 체계적인 제목/설명/태그 최적화 |

</div>

---

## 스킬 목록

### 视频剪辑 (영상 편집)

| 스킬 | 설명 | 파일 |
|-------|-------------|------|
| 🎥 FFmpeg Master | 자르기, 병합, 변환, 압축 — FFmpeg 파이프라인 전체 자동화 | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | 색 보정, Fusion VFX, Fairlight 오디오, 내보내기 프리셋 | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | 시퀀스 설정, 내보내기 프리셋, Dynamic Link, Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作 (이펙트)

| 스킬 | 설명 | 파일 |
|-------|-------------|------|
| ✨ Motion Graphics | After Effects 표현식, CSS 애니메이션, Lottie 템플릿 | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI Video Generation | Runway, Pika, Sora 프롬프트 엔지니어링 및 후처리 | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕处理 (자막 처리)

| 스킬 | 설명 | 파일 |
|-------|-------------|------|
| 📝 Subtitle Generation | Whisper 전사, SRT/ASS 포맷팅, 자막 굽기 | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Translation Subtitles | 다국어 자막 파이프라인, 이중 언어 오버레이, QA | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### 音频处理 (오디오)

| 스킬 | 설명 | 파일 |
|-------|-------------|------|
| 🎵 Audio Mixing | 노이즈 제거, EQ, 압축, 노멀라이제이션, 음악 믹싱 | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 发布优化 (배포 최적화)

| 스킬 | 설명 | 파일 |
|-------|-------------|------|
| 📈 YouTube Optimization | SEO 제목, 썸네일 디자인, 태그, 분석, 업로드 스케줄링 | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Multi-Platform Publish | YouTube, TikTok, Bilibili, Instagram — 규격, 일괄 내보내기, 자동화 | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## 빠른 시작

### Cursor

任意 스킬 파일을 프로젝트의 `.cursorrules` 또는 `.cursor/rules/` 디렉토리에 복사하세요:

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

여러 스킬을 참조하려면:

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

`CLAUDE.md`에 프로젝트 컨텍스트로 스킬을 추가하세요:

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

스킬 파일을 프로젝트 루트 또는 `.kimi/` 디렉토리에 복사하세요:

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### 스킬 사용하기

설치 후, AI 어시스턴트에게 자연스럽게 요청하세요:

```
"이 영상을 이메일용으로 50MB 미만으로 압축해 줘"
"이 인터뷰의 중국어 자막을 생성해 줘"
"유튜브 영상의 TikTok 버전을 만들어 줘"
"유튜브 제목과 설명을 SEO에 맞게 최적화해 줘"
"이 내레이션 아래에 배경 음악을 -18dB로 믹싱해 줘"
```

---

## 기여하기

새로운 영상 스킬을 환영합니다! 가이드라인은 [CONTRIBUTING.md](CONTRIBUTING.md)를 참조하세요.

기여 방법:
1. 이 저장소를 Fork하세요
2. `skills/` 아래 적절한 카테고리에 스킬을 추가하세요
3. 스킬 템플릿 형식(사용 시기, 지침, 템플릿, 주의사항)을 따르세요
4. PR을 제출하세요

---

## 관련 링크

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — 모든 분야의 AI 스킬 큐레이션 컬렉션
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — 코딩 어시스턴트용 AI 규칙 및 설정
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — AI 스킬 품질 검증 및 테스트
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — AI 기반 git 커밋 메시지 생성
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — AI 도구를 위한 Model Context Protocol 서버

---

## 라이선스

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
