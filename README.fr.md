[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> Arrêtez de chercher des commandes FFmpeg sur Google. Écrivez la compétence une fois. Montez vos vidéos avec l'IA pour toujours.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#compétences)

</div>

---



## Le problème

Vous passez **des heures** à chercher les drapeaux FFmpeg, à consulter les raccourcis DaVinci Resolve, et à réécrire les mêmes scripts de sous-titres — à chaque projet. Votre assistant IA ne connaît pas votre flux de travail, vos présets, ni vos préférences.

## La solution

Écrivez vos connaissances en montage vidéo sous forme de **compétences IA**, une seule fois. Votre assistant IA lit la compétence et génère exactement le bon pipeline, préset ou script — à chaque fois.

<div align="center">

| ❌ Sans compétence | ✅ Avec compétence |
|:---:|:---:|
| 30 min à chercher les drapeaux FFmpeg | "Compresse cette vidéo pour YouTube" → commande parfaite |
| Redimensionner manuellement pour 5 plateformes | Export batch en un clic pour toutes les plateformes |
| Réécrire les scripts de sous-titres | L'IA génère exactement le pipeline Whisper voulu |
| Deviner le SEO YouTube | Optimisation structurée titre/description/tags |

</div>

---

## Compétences

### Montage vidéo

| Compétence | Description | Fichier |
|------------|-------------|---------|
| 🎥 FFmpeg Master | Découpe, fusion, conversion, compression — automatisation complète du pipeline FFmpeg | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | Étalonnage, VFX Fusion, audio Fairlight, présets de livraison | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | Configuration de séquence, présets d'export, Dynamic Link, Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### Effets spéciaux

| Compétence | Description | Fichier |
|------------|-------------|---------|
| ✨ Motion Design | Expressions After Effects, animations CSS, modèles Lottie | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 Génération vidéo IA | Prompt engineering et post-traitement pour Runway, Pika, Sora | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### Sous-titres

| Compétence | Description | Fichier |
|------------|-------------|---------|
| 📝 Génération de sous-titres | Transcription Whisper, formatage SRT/ASS, incrustation de sous-titres | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Traduction de sous-titres | Pipelines multilingues, sous-titres bilingues, contrôle qualité | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### Audio

| Compétence | Description | Fichier |
|------------|-------------|---------|
| 🎵 Mixage audio | Suppression de bruit, EQ, compression, normalisation, mixage musical | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### Publication

| Compétence | Description | Fichier |
|------------|-------------|---------|
| 📈 Optimisation YouTube | Titres SEO, design de miniature, tags, analytique, planification d'upload | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Publication multiplateforme | YouTube, TikTok, Bilibili, Instagram — spécifications, export batch, automatisation | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## Démarrage rapide

### Cursor

Copiez un fichier de compétence dans le répertoire `.cursorrules` ou `.cursor/rules/` de votre projet :

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

Ou référez plusieurs compétences :

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

Ajoutez les compétences comme contexte projet dans votre `CLAUDE.md` :

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

Copiez les fichiers de compétences à la racine de votre projet ou dans le répertoire `.kimi/` :

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### Utiliser les compétences

Une fois installées, demandez simplement à votre assistant IA en langage naturel :

```
"Compress this video to under 50MB for email"
"Generate Chinese subtitles for this interview"
"Create a TikTok version of my YouTube video"
"Optimize my YouTube title and description for SEO"
"Mix background music under this voiceover at -18dB"
```

---

## Contribuer

Nous accueillons les nouvelles compétences vidéo ! Consultez [CONTRIBUTING.md](CONTRIBUTING.md) pour les directives.

Comment contribuer :
1. Forkez ce dépôt
2. Ajoutez votre compétence dans la catégorie appropriée sous `skills/`
3. Suivez le format de modèle de compétence (Quand l'utiliser, Instructions, Modèles, Pièges)
4. Soumettez une PR

---

## Voir aussi

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — Collection sélectionnée de compétences IA pour chaque domaine
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — Règles et configurations pour assistants IA de programmation
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — Validation et test de la qualité des compétences IA
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — Génération de messages de commit Git par IA
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — Serveurs Model Context Protocol pour outils IA

---

## Licence

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
