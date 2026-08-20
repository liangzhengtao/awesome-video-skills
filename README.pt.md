[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> Pare de pesquisar comandos do FFmpeg. Escreva a habilidade uma vez. Edite vídeos com IA para sempre.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

</div>

---



## O Problema

Você gasta **horas** pesquisando flags do FFmpeg, consultando atalhos do DaVinci Resolve e reescrevendo os mesmos scripts de legenda — em cada projeto. Seu assistente de IA não conhece seu fluxo de trabalho, seus predefinições ou suas preferências.

## A Solução

Escreva seu conhecimento de edição de vídeo como **habilidades de IA** uma vez. Seu assistente de IA lê a habilidade e gera exatamente o pipeline, preset ou script correto — sempre.

<div align="center">

| ❌ Sem Habilidade | ✅ Com Habilidade |
|:---:|:---:|
| 30 min pesquisando flags do FFmpeg | "Comprima isso para o YouTube" → comando perfeito |
| Redimensionando manualmente para 5 plataformas | Exportação em lote com um clique para todas as plataformas |
| Reescrevendo scripts de legenda | IA gera exatamente o pipeline Whisper que você quer |
| Adivinhando SEO do YouTube | Otimização estruturada de título/descrição/tag |

</div>

---

## Habilidades

### 视频剪辑 (Edição de Vídeo)

| Habilidade | Descrição | Arquivo |
|-------|-------------|------|
| 🎥 FFmpeg Master | Cortar, mesclar, converter, comprimir — automação completa do pipeline FFmpeg | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | Correção de cor, VFX do Fusion, áudio Fairlight, predefinições de entrega | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | Configuração de sequência, predefinições de exportação, Dynamic Link, Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作 (Efeitos)

| Habilidade | Descrição | Arquivo |
|-------|-------------|------|
| ✨ Motion Graphics | Expressões After Effects, animações CSS, templates Lottie | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI Video Generation | Engenharia de prompts em Runway, Pika, Sora e pós-processamento | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕处理 (Legendas)

| Habilidade | Descrição | Arquivo |
|-------|-------------|------|
| 📝 Subtitle Generation | Transcrição Whisper, formatação SRT/ASS, gravação de legendas | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Translation Subtitles | Pipelines de legendas multilíngues, sobreposições bilíngues, QA | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### 音频处理 (Áudio)

| Habilidade | Descrição | Arquivo |
|-------|-------------|------|
| 🎵 Audio Mixing | Remoção de ruído, EQ, compressão, normalização, mixagem musical | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 发布优化 (Publicação)

| Habilidade | Descrição | Arquivo |
|-------|-------------|------|
| 📈 YouTube Optimization | Títulos SEO, design de thumbnail, tags, análise, agendamento de upload | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Multi-Platform Publish | YouTube, TikTok, Bilibili, Instagram — especificações, exportação em lote, automação | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## Início Rápido

### Cursor

Copie qualquer arquivo de habilidade para o diretório `.cursorrules` ou `.cursor/rules/` do seu projeto:

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

Ou referencie múltiplas habilidades:

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

Adicione habilidades como contexto do projeto no seu `CLAUDE.md`:

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

Copie os arquivos de habilidade para a raiz do projeto ou diretório `.kimi/`:

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### Usando as Habilidades

Depois de instaladas, basta pedir ao seu assistente de IA naturalmente:

```
"Comprima este vídeo para menos de 50MB para e-mail"
"Gere legendas em chinês para esta entrevista"
"Crie uma versão TikTok do meu vídeo do YouTube"
"Otimize meu título e descrição do YouTube para SEO"
"Mixe música de fundo nesta narração a -18dB"
```

---

## Contribuindo

Recebemos novas habilidades de vídeo! Consulte [CONTRIBUTING.md](CONTRIBUTING.md) para diretrizes.

Forma rápida de contribuir:
1. Faça um fork deste repositório
2. Adicione sua habilidade na categoria apropriada em `skills/`
3. Siga o formato do template de habilidade (Quando Usar, Instruções, Templates, Armadilhas)
4. Envie um PR

---

## Veja Também

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — Coleção curada de habilidades de IA para todos os domínios
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — Regras e configurações de IA para assistentes de código
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — Valide e teste a qualidade das suas habilidades de IA
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — Geração de mensagens de commit com IA
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — Servidores Model Context Protocol para ferramentas de IA

---

## Licença

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
