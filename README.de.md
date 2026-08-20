[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> Schluss mit dem Googeln von FFmpeg-Befehlen. Schreiben Sie den Skill einmal. Bearbeiten Sie Videos für immer mit KI.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

</div>

---



## Das Problem

Sie verbringen **Stunden** damit, FFmpeg-Flags zu googeln, DaVinci-Resolve-Tastenkürzel nachzuschlagen und dieselben Untertitelskripte neu zu schreiben — bei jedem einzelnen Projekt. Ihr KI-Assistent kennt Ihren Workflow, Ihre Voreinstellungen oder Ihre Präferenzen nicht.

## Die Lösung

Schreiben Sie Ihr Videobearbeitungswissen einmal als **KI-Skills**. Ihr KI-Assistent liest den Skill und generiert genau die richtige Pipeline, Voreinstellung oder das richtige Skript — jedes Mal.

<div align="center">

| ❌ Ohne Skill | ✅ Mit Skill |
|:---:|:---:|
| 30 Min. FFmpeg-Flags googeln | „Für YouTube komprimieren" → perfekter Befehl |
| Manuell für 5 Plattformen skalieren | Ein-Klick-Stapelexport für alle Plattformen |
| Untertitelskripte neu schreiben | KI generiert genau die gewünschte Whisper-Pipeline |
| YouTube-SEO raten | Strukturierte Titel/Beschreibungen/Tags-Optimierung |

</div>

---

## Skills

### 视频剪辑 (Videoschnitt)

| Skill | Beschreibung | Datei |
|-------|-------------|------|
| 🎥 FFmpeg Master | Schneiden, zusammenführen, konvertieren, komprimieren — vollständige FFmpeg-Pipeline-Automatisierung | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | Farbkorrektur, Fusion VFX, Fairlight Audio, Ausgabe-Voreinstellungen | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | Sequenzeinrichtung, Export-Voreinstellungen, Dynamic Link, Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作 (Effekte)

| Skill | Beschreibung | Datei |
|-------|-------------|------|
| ✨ Motion Graphics | After-Effects-Ausdrücke, CSS-Animationen, Lottie-Vorlagen | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI Video Generation | Prompt-Engineering und Nachbearbeitung in Runway, Pika, Sora | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕处理 (Untertitel)

| Skill | Beschreibung | Datei |
|-------|-------------|------|
| 📝 Subtitle Generation | Whisper-Transkription, SRT/ASS-Formatierung, Untertiteleinblendung | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Translation Subtitles | Mehrsprachige Untertitel-Pipelines, zweisprachige Überlagerungen, QA | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### 音频处理 (Audio)

| Skill | Beschreibung | Datei |
|-------|-------------|------|
| 🎵 Audio Mixing | Rauschunterdrückung, EQ, Kompression, Normalisierung, Musikmischung | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 发布优化 (Veröffentlichung)

| Skill | Beschreibung | Datei |
|-------|-------------|------|
| 📈 YouTube Optimization | SEO-Titel, Thumbnail-Design, Tags, Analytik, Upload-Planung | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Multi-Platform Publish | YouTube, TikTok, Bilibili, Instagram — Spezifikationen, Stapelexport, Automatisierung | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## Schnellstart

### Cursor

Kopieren Sie eine beliebige Skill-Datei in das `.cursorrules`- oder `.cursor/rules/`-Verzeichnis Ihres Projekts:

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

Oder referenzieren Sie mehrere Skills:

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

Fügen Sie Skills als Projektkontext in Ihrer `CLAUDE.md` hinzu:

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

Kopieren Sie die Skill-Dateien in das Projekt-Root oder das `.kimi/`-Verzeichnis:

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### Skills verwenden

Nach der Installation fragen Sie einfach Ihren KI-Assistenten auf natürliche Weise:

```
"Komprimiere dieses Video auf unter 50 MB für E-Mail"
"Generiere chinesische Untertitel für dieses Interview"
"Erstelle eine TikTok-Version meines YouTube-Videos"
"Optimiere meinen YouTube-Titel und die Beschreibung für SEO"
"Mixe Hintergrundmusik unter diesen Voiceover bei -18 dB"
```

---

## Mitwirken

Wir freuen uns über neue Video-Skills! Siehe [CONTRIBUTING.md](CONTRIBUTING.md) für Richtlinien.

Schneller Weg zum Beitrag:
1. Forken Sie dieses Repository
2. Fügen Sie Ihren Skill in die entsprechende Kategorie unter `skills/` ein
3. Folgen Sie dem Skill-Template-Format (Wann verwenden, Anleitungen, Vorlagen, Fallstricke)
4. Reichen Sie einen PR ein

---

## Siehe auch

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — Kuratierte Sammlung von KI-Skills für jeden Bereich
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — KI-Regeln und -Konfigurationen für Coding-Assistenten
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — Überprüfen und testen Sie die Qualität Ihrer KI-Skills
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — KI-gesteuerte Git-Commit-Nachrichtengenerierung
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — Model Context Protocol Server für KI-Werkzeuge

---

## Lizenz

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
