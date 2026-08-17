# Automatic Subtitle Generation

> Generate, edit, style, and burn subtitles into videos using Whisper, FFmpeg, and ASS styling.

## When to Use

- Transcribing video/audio to subtitles automatically
- Generating SRT or ASS subtitle files from speech
- Burning (hardcoding) subtitles into video
- Styling subtitles with custom fonts, colors, and effects
- Batch processing subtitle generation for multiple videos
- Syncing subtitles with video timing
- Creating karaoke-style or animated subtitles

## Instructions for AI Assistant

You are a subtitle and captioning expert. When the user needs subtitles:

1. **Choose the right tool** — Whisper for transcription, FFmpeg for burning, Aegisub for advanced styling.
2. **Language detection** — Ask what language(s) the audio contains.
3. **Accuracy vs speed tradeoff** — Larger Whisper models are more accurate but slower.
4. **Format selection** — SRT for simplicity, ASS for styling, VTT for web.
5. **Timing accuracy** — Always verify timing with the source video.
6. **Accessibility** — Ensure subtitles meet accessibility standards (contrast, size, position).

### Subtitle Format Comparison

```
Format │ Styling │ Positioning │ Compatibility │ Best For
───────┼─────────┼─────────────┼───────────────┼──────────────────
SRT    │ None    │ Basic       │ Universal     │ Simple subtitles
ASS    │ Full    │ Full        │ Most players  │ Styled subtitles
VTT    │ Basic   │ Good        │ Web/HTML5     │ Web video
SCC    │ Limited │ Limited     │ Broadcast     │ TV broadcast
TTML   │ Full    │ Full        │ Streaming     │ Netflix/streaming
```

## Templates

### Template 1: Whisper Transcription Setup

```bash
## Installation
pip install openai-whisper

## Basic Transcription
whisper video.mp4 --language zh --model medium --output_format srt

## Model Selection Guide
# tiny   — Fastest, least accurate (1GB VRAM)
# base   — Fast, ok accuracy (1GB VRAM)
# small  — Balanced (2GB VRAM)
# medium — Good accuracy, slower (5GB VRAM)
# large  — Best accuracy, slowest (10GB VRAM)
# turbo  — Fast + accurate, recommended (6GB VRAM)

## Advanced Options
whisper video.mp4 \
  --language zh \
  --model turbo \
  --output_format srt \
  --output_dir ./subtitles \
  --word_timestamps True \
  --condition_on_previous_text True \
  --initial_prompt "以下是普通话的句子。" \
  --verbose False

## Batch Processing
for f in *.mp4; do
  whisper "$f" --language auto --model turbo --output_format srt --output_dir ./subtitles
done

## PowerShell Batch
Get-ChildItem *.mp4 | ForEach-Object {
  whisper $_.FullName -l auto -m turbo -f srt -o ./subtitles
}
```

### Template 2: SRT Format Reference

```srt
1
00:00:01,000 --> 00:00:04,000
Welcome to this tutorial on
video editing with AI.

2
00:00:04,500 --> 00:00:08,000
Today we'll cover the basics
of subtitle generation.

3
00:00:08,500 --> 00:00:12,000
Let's start by setting up
our workspace and tools.

## SRT Rules
- Sequence number: integer starting from 1
- Timestamp: HH:MM:SS,mmm --> HH:MM:SS,mmm (comma, not period)
- Text: One or more lines, max ~42 characters per line
- Blank line between entries
- Encoding: UTF-8 with BOM for CJK characters
```

### Template 3: ASS Subtitle Styling

```ass
[Script Info]
Title: Styled Subtitles
ScriptType: v4.00+
PlayResX: 1920
PlayResY: 1080
WrapStyle: 0

[V4+ Styles]
Format: Name, Fontname, Fontsize, PrimaryColour, SecondaryColour, OutlineColour, BackColour, Bold, Italic, Underline, StrikeOut, ScaleX, ScaleY, Spacing, Angle, BorderStyle, Outline, Shadow, Alignment, MarginL, MarginR, MarginV, Encoding
Style: Default,Arial,68,&H00FFFFFF,&H000000FF,&H00000000,&H80000000,-1,0,0,0,100,100,0,0,1,3,1,2,20,20,40,1
Style: Title,Microsoft YaHei,80,&H0000FFFF,&H000000FF,&H00000000,&H80000000,-1,0,0,0,100,100,2,0,1,4,2,2,20,20,50,1
Style: Karaoke,Arial,72,&H0000D4FF,&H00FFFFFF,&H00000000,&H80000000,-1,0,0,0,100,100,0,0,1,3,0,2,20,20,40,1

[Events]
Format: Layer, Start, End, Style, Name, MarginL, MarginR, MarginV, Effect, Text
Dialogue: 0,0:00:01.00,0:00:04.00,Default,,0,0,0,,{\fad(300,300)}Welcome to this tutorial
Dialogue: 0,0:00:04.50,0:00:08.00,Default,,0,0,0,,{\fad(300,300)\pos(960,900)}Today's topic: AI subtitles
Dialogue: 0,0:00:08.50,0:00:12.00,Title,,0,0,0,,{\fad(500,500)\an8}Chapter 1: Getting Started

## Common ASS Override Tags
# {\fad(in_ms,out_ms)} — Fade in/out
# {\pos(x,y)} — Position (alignment point)
# {\an1-9)} — Alignment (numpad layout)
# {\b1} / {\b0} — Bold on/off
# {\i1} / {\i0} — Italic on/off
# {\c&HBBGGRR&} — Text color (BGR hex)
# {\3c&HBBGGRR&} — Outline color
# {\4c&HBBGGRR&} — Shadow color
# {\fs<size>} — Font size
# {\fn<name>} — Font name
# {\k<duration>} — Karaoke (duration in centiseconds)
# {\K<duration>} — Karaoke fill (sweep)
# {\move(x1,y1,x2,y2)} — Movement animation
# {\t(<start>,<end>,<tags>)} — Transform over time
```

### Template 4: Burning Subtitles with FFmpeg

```bash
## Soft Subtitles (embedded, can be toggled)
ffmpeg -i video.mp4 -i subs.srt -c copy -c:s mov_text output.mp4

## Hard Subtitles (burned into video) — SRT
ffmpeg -i video.mp4 -vf "subtitles=subs.srt:force_style='FontSize=24,PrimaryColour=&H00FFFFFF,OutlineColour=&H00000000,Outline=2,Shadow=1,MarginV=30'" output.mp4

## Hard Subtitles — ASS (preserves styling)
ffmpeg -i video.mp4 -vf "ass=subs.ass" output.mp4

## Subtitles with Font Customization
ffmpeg -i video.mp4 -vf "subtitles=subs.srt:force_style='FontName=Noto Sans CJK SC,FontSize=20,PrimaryColour=&H00FFFFFF,OutlineColour=&H00000000,BorderStyle=1,Outline=2,Shadow=0,MarginV=25'" output.mp4

## Position Subtitles at Top
ffmpeg -i video.mp4 -vf "subtitles=subs.srt:force_style='Alignment=8,MarginV=20'" output.mp4

## Multiple Subtitle Tracks
ffmpeg -i video.mp4 -i subs_en.srt -i subs_zh.srt \
  -c copy -c:s mov_text \
  -metadata:s:s:0 language=eng -metadata:s:s:0 title="English" \
  -metadata:s:s:1 language=chi -metadata:s:s:1 title="中文" \
  output.mp4
```

### Template 5: Auto-Sync & Correction

```bash
## Subtitle Timing Adjustment with FFmpeg
# Delay all subtitles by 2.5 seconds
ffmpeg -i video.mp4 -itsoffset 2.5 -i subs.srt -c copy output.mkv

## SubtitleEdit (GUI tool for sync and correction)
# Install: https://github.com/SubtitleEdit/subtitleedit
# Features:
# - Auto-sync to audio
# - Fix overlapping timestamps
# - Spell check
# - OCR for bitmap subtitles
# - Batch convert formats

## Python Subtitle Processing
pip install pysrt srt

# Adjust timing
import pysrt
subs = pysrt.open('subs.srt')
for sub in subs:
    sub.shift(seconds=2.5)  # Delay by 2.5s
subs.save('adjusted.srt')

# Merge short lines
import srt
with open('subs.srt', 'r', encoding='utf-8') as f:
    subtitles = list(srt.parse(f.read()))
# Process and save
with open('merged.srt', 'w', encoding='utf-8') as f:
    f.write(srt.compose(subtitles))
```

## Common Patterns

### Subtitle Workflow Pipeline

```
## Full Pipeline: Audio → Subtitles → Burned Video

### Step 1: Extract Audio
ffmpeg -i video.mp4 -vn -acodec pcm_s16le -ar 16000 -ac 1 audio.wav

### Step 2: Transcribe with Whisper
whisper audio.wav --language auto --model turbo --output_format srt --output_dir .

### Step 3: Review & Edit
- Open in SubtitleEdit or Aegisub
- Fix recognition errors
- Adjust timing
- Merge/split lines for readability

### Step 4: Style (Optional)
- Convert SRT to ASS
- Apply styling template
- Set font, color, position

### Step 5: Burn into Video
ffmpeg -i video.mp4 -vf "ass=subs.ass" -c:v libx264 -crf 20 -c:a copy output.mp4
```

### Bilingual Subtitles

```
## Dual-Language Subtitle Setup (ASS)

### Format: Primary language on bottom, secondary above

Style: Primary,Noto Sans CJK SC,52,&H00FFFFFF,&H000000FF,&H00000000,&H80000000,-1,0,0,0,100,100,0,0,1,3,1,2,20,20,40,1
Style: Secondary,Arial,40,&H0080DDFF,&H000000FF,&H00000000,&H80000000,0,0,0,0,100,100,0,0,1,2,1,8,20,20,40,1

Dialogue: 0,0:00:01.00,0:00:04.00,Primary,,0,0,0,,欢迎来到本教程
Dialogue: 0,0:00:01.00,0:00:04.00,Secondary,,0,0,0,,Welcome to this tutorial

### Key: Both lines share the same time range, different styles
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Using tiny model for production | High error rate, especially for accents | Use medium or turbo for production subtitles |
| Not specifying language | Whisper may mis-detect and hallucinate | Always set `--language` if you know it |
| Burning SRT without styling control | Looks basic and unprofessional | Use ASS format with custom styling for burned subs |
| Forgetting UTF-8 BOM for CJK | Chinese/Japanese characters show as garbled | Always save as UTF-8 with BOM |
| Subtitles too fast (< 1 sec display) | Viewers can't read them | Minimum 1.5 seconds, scale with text length |
| Lines too long (> 42 chars) | Hard to read quickly | Split at natural phrase boundaries |
| Not proofreading Whisper output | Whisper makes errors, especially with names | Always review and correct before burning |
| Ignoring subtitle accessibility | Users with hearing impairments depend on accuracy | Include speaker identification, sound effects in brackets |
