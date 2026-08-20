[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md) | [العربية](README.ar.md) | [한국어](README.ko.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Deutsch](README.de.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 مهارات الفيديو الرائعة

> توقف عن البحث عن أوامر FFmpeg. اكتب المهارة مرة واحدة. حرّر الفيديوهات بالذكاء الاصطناعي إلى الأبد.

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#skills)

</div>

---



## المشكلة

تقضي **ساعات** في البحث عن أعلام FFmpeg، ومراجعة اختصارات DaVinci Resolve، وإعادة كتابة نفس نصوص الترجمة — في كل مشروع. مساعدك الذكي لا يعرف سير عملك أو إعداداتك المسبقة أو تفضيلاتك.

## الحل

اكتب معرفتك بتحرير الفيديو كـ**مهارات ذكاء اصطناعي** مرة واحدة. يقرأ مساعدك الذكي المهارة ويُنشئ بالضبط خط الإنتاج أو الإعداد المسبق أو النص المناسب — في كل مرة.

<div align="center">

| ❌ بدون مهارة | ✅ مع مهارة |
|:---:|:---:|
| 30 دقيقة من البحث عن أعلام FFmpeg | "اضغط هذا لليوتيوب" → أمر مثالي |
| تغيير الحجم يدويًا لـ 5 منصات | تصدير دفعي بنقرة واحدة لجميع المنصات |
| إعادة كتابة نصوص الترجمة | الذكاء الاصطناعي يُنشئ خط Whisper بالضبط كما تريد |
| تخمين SEO لليوتيوب | تحسين منظم للعنوان والوصف والوسوم |

</div>

---

## المهارات

### 视频剪辑 (تحرير الفيديو)

| المهارة | الوصف | الملف |
|-------|-------------|------|
| 🎥 FFmpeg Master | قص، دمج، تحويل، ضغط — أتمتة كاملة لخط إنتاج FFmpeg | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | تصحيح الألوان، تأثيرات Fusion، صوت Fairlight، إعدادات التسليم | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | إعداد التسلسل، إعدادات التصدير، Dynamic Link، Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作 (التأثيرات البصرية)

| المهارة | الوصف | الملف |
|-------|-------------|------|
| ✨ Motion Graphics | تعبيرات After Effects، رسوم CSS المتحركة، قوالب Lottie | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI Video Generation | هندسة الأوامر في Runway و Pika و Sora وما بعد المعالجة | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕处理 (الترجمة)

| المهارة | الوصف | الملف |
|-------|-------------|------|
| 📝 Subtitle Generation | نسخ Whisper، تنسيق SRT/ASS، حرق الترجمة | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 Translation Subtitles | خطوط ترجمة متعددة اللغات، تراكبات ثنائية اللغة، ضبط الجودة | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### 音频处理 (الصوت)

| المهارة | الوصف | الملف |
|-------|-------------|------|
| 🎵 Audio Mixing | إزالة الضوضاء، معادل الصوت، الضغط، التطبيع، خلط الموسيقى | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 发布优化 (النشر)

| المهارة | الوصف | الملف |
|-------|-------------|------|
| 📈 YouTube Optimization | عناوين SEO، تصميم الصور المصغرة، الوسوم، التحليلات، جدولة الرفع | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 Multi-Platform Publish | يوتيوب، تيك توك، بيليبيلي، إنستغرام — المواصفات، التصدير الدفعي، الأتمتة | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## البدء السريع

### Cursor

انسخ أي ملف مهارة إلى مجلد `.cursorrules` أو `.cursor/rules/` في مشروعك:

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

أو قم بال referencing لمهارات متعددة:

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

أضف المهارات كسياق للمشروع في `CLAUDE.md`:

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

انسخ ملفات المهارات إلى جذر مشروعك أو مجلد `.kimi/`:

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### استخدام المهارات

بمجرد التثبيت، اطلب من مساعدك الذكي بشكل طبيعي:

```
"اضغط هذا الفيديو لأقل من 50 ميجابايت للبريد الإلكتروني"
"أنشئ ترجمة صينية لهذا المقابلة"
"أنشئ نسخة تيك توك من فيديو يوتيوب خاصتي"
"حسّن عنوان ووصف يوتيوب خاصتي لـ SEO"
"اخلط موسيقى خلفية تحت هذا التعليق الصوتي بمستوى -18dB"
```

---

## المساهمة

نرحب بمهارات فيديو جديدة! انظر [CONTRIBUTING.md](CONTRIBUTING.md) للإرشادات.

طريقة سريعة للمساهمة:
1. قم بعمل Fork لهذا المستودع
2. أضف مهارتك في الفئة المناسبة تحت `skills/`
3. اتبع تنسيق قالب المهارة (متى تُستخدم، التعليمات، القوالب، المزالق)
4. قدم طلب سحب

---

## انظر أيضًا

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — مجموعة منتقاة من مهارات الذكاء الاصطناعي لكل مجال
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — قواعد وتكوينات الذكاء الاصطناعي لمساعدي البرمجة
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — تحقق واختبر جودة مهارات الذكاء الاصطناعي الخاصة بك
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — إنشاء رسائل git commit بالذكاء الاصطناعي
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — خوادم Model Context Protocol لأدوات الذكاء الاصطناعي

---

## الترخيص

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
