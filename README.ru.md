[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> Хватит гуглить команды FFmpeg. Напишите навык один раз. Монтируйте видео с помощью ИИ навсегда.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

</div>

---



## Проблема

Вы тратите **часы** на поиск флагов FFmpeg, горячих клавиш DaVinci Resolve и переписывание одних и тех же скриптов субтитров — в каждом проекте. Ваш ИИ-ассистент не знает ваш рабочий процесс, пресеты или предпочтения.

## Решение

Запишите свои знания видеомонтажа как **ИИ-навыки** один раз. Ваш ИИ-ассистент прочитает навык и сгенерирует именно тот конвейер, пресет или скрипт, который нужен — каждый раз.

<div align="center">

| ❌ Без навыка | ✅ С навыком |
|:---:|:---:|
| 30 минут поиска флагов FFmpeg | «Сожми это для YouTube» → идеальная команда |
| Ручное изменение размера для 5 платформ | Пакетный экспорт одним кликом для всех платформ |
| Переписывание скриптов субтитров | ИИ генерирует именно тот конвейер Whisper, который вам нужен |
| Угадывание SEO YouTube | Структурированная оптимизация заголовков/описаний/тегов |

</div>

---

## Навыки

### 视频剪辑 (Видеомонтаж)

| Навык | Описание | Файл |
|-------|-------------|------|
| 🎥 FFmpeg Master | Нарезка, объединение, конвертация, сжатие — полная автоматизация конвейера FFmpeg | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | Цветокоррекция, Fusion VFX, аудио Fairlight, пресеты рендера | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | Настройка последовательности, пресеты экспорта, Dynamic Link, Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作 (Эффекты)

| Навык | Описание | Файл |
|-------|-------------|------|
| ✨ Motion Graphics | Выражения After Effects, CSS-анимации, шаблоны Lottie | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI Video Generation | Инженерия промптов в Runway, Pika, Sora и постобработка | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕处理 (Субтитры)

| Навык | Описание | Файл |
|-------|-------------|------|
| 📝 Subtitle Generation | Транскрипция Whisper, форматирование SRT/ASS, встраивание субтитров | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Translation Subtitles | Многоязычные конвейеры субтитров, двуязычные наложения, контроль качества | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### 音频处理 (Аудио)

| Навык | Описание | Файл |
|-------|-------------|------|
| 🎵 Audio Mixing | Удаление шума, эквализация, компрессия, нормализация, сведение музыки | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 发布优化 (Публикация)

| Навык | Описание | Файл |
|-------|-------------|------|
| 📈 YouTube Optimization | SEO-заголовки, дизайн превью, теги, аналитика, планирование загрузки | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Multi-Platform Publish | YouTube, TikTok, Bilibili, Instagram — спецификации, пакетный экспорт, автоматизация | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## Быстрый старт

### Cursor

Скопируйте любой файл навыка в директорию `.cursorrules` или `.cursor/rules/` вашего проекта:

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

Или подключите несколько навыков:

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

Добавьте навыки как контекст проекта в `CLAUDE.md`:

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

Скопируйте файлы навыков в корень проекта или директорию `.kimi/`:

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### Использование навыков

После установки просто задайте вопрос вашему ИИ-ассистенту естественным образом:

```
"Сожми это видео до 50 МБ для отправки по почте"
"Сгенерируй китайские субтитры для этого интервью"
"Создай TikTok-версию моего YouTube-видео"
"Оптимизируй заголовок и описание YouTube для SEO"
"Сведи фоновую музыку под этот голосовой комментарий на -18 дБ"
```

---

## Участие в проекте

Мы приветствуем новые навыки для видео! Смотрите [CONTRIBUTING.md](CONTRIBUTING.md) для руководства.

Быстрый способ внести вклад:
1. Сделайте форк этого репозитория
2. Добавьте свой навык в соответствующую категорию в `skills/`
3. Следуйте формату шаблона навыка (Когда использовать, Инструкции, Шаблоны, Подводные камни)
4. Отправьте PR

---

## Смотрите также

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — Кураторская коллекция ИИ-навыков для любой области
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — Правила и конфигурации ИИ для ассистентов программирования
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — Проверьте и протестируйте качество ваших ИИ-навыков
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — Генерация сообщений коммитов с помощью ИИ
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — Серверы Model Context Protocol для инструментов ИИ

---

## Лицензия

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
