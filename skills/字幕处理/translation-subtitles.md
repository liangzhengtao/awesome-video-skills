# Subtitle Translation

> Translate subtitles for multilingual audiences — automated translation pipelines, timing adjustment, bilingual subtitle generation, and quality assurance.

## When to Use

- Translating subtitles from one language to another
- Creating bilingual subtitles for language learning
- Adjusting subtitle timing after translation (different reading speeds)
- Building a multi-language subtitle package for distribution
- Quality-checking machine-translated subtitles
- Maintaining subtitle consistency across a video series

## Instructions for AI Assistant

You are a subtitle translation expert. When the user needs translated subtitles:

1. **Source quality first** — Bad source subtitles produce bad translations. Verify source accuracy.
2. **Translation approach** — Machine translation (fast, needs review), AI-assisted (balanced), or human (best quality).
3. **Cultural adaptation** — Don't just translate words; adapt idioms, references, and humor.
4. **Reading speed** — Different languages require different display times (Chinese: fast, German: slow).
5. **Character limits** — Enforce per-language character limits per line.
6. **Consistency** — Maintain a glossary for recurring terms across episodes/series.

### Language Reading Speed Reference

```
Language   │ Chars/Line │ Min Display │ Reading Speed
───────────┼────────────┼─────────────┼──────────────
Chinese    │ 16-18      │ 1.5s        │ ~4 chars/sec
Japanese   │ 14-16      │ 1.5s        │ ~4 chars/sec
Korean     │ 16-20      │ 1.5s        │ ~5 chars/sec
English    │ 37-42      │ 1.2s        │ ~20 chars/sec
Spanish    │ 37-42      │ 1.3s        │ ~18 chars/sec
French     │ 35-40      │ 1.3s        │ ~18 chars/sec
German     │ 32-38      │ 1.4s        │ ~15 chars/sec
Arabic     │ 35-40      │ 1.3s        │ ~18 chars/sec
Russian    │ 32-38      │ 1.4s        │ ~15 chars/sec
Portuguese │ 35-40      │ 1.3s        │ ~18 chars/sec
```

## Templates

### Template 1: AI Translation Pipeline

```python
#!/usr/bin/env python3
"""
Subtitle Translation Pipeline
Translates SRT subtitles using AI (OpenAI, Claude, or local model)
"""

import re
import srt
from datetime import timedelta
from pathlib import Path

# === Configuration ===
SOURCE_LANG = "en"
TARGET_LANG = "zh"
BATCH_SIZE = 10  # Translate N subtitles at once for context
CHARS_PER_LINE = 18  # For CJK; use 42 for Latin scripts

def load_srt(filepath: str) -> list:
    with open(filepath, 'r', encoding='utf-8-sig') as f:
        return list(srt.parse(f.read()))

def save_srt(subtitles: list, filepath: str):
    with open(filepath, 'w', encoding='utf-8-sig') as f:
        f.write(srt.compose(subtitles))

def batch_subtitles(subs: list, batch_size: int) -> list:
    """Group subtitles into batches for context-aware translation."""
    return [subs[i:i+batch_size] for i in range(0, len(subs), batch_size)]

def build_translation_prompt(batch: list, source_lang: str, target_lang: str) -> str:
    """Build a prompt for translation with context."""
    entries = []
    for sub in batch:
        entries.append(f"[{sub.index}] {sub.content}")
    
    source_text = "\n".join(entries)
    
    return f"""Translate the following subtitles from {source_lang} to {target_lang}.

Rules:
- Keep the [number] prefix for each entry
- Maintain the same line count per entry
- Respect character limits: max {CHARS_PER_LINE} characters per line
- Preserve timing cues and speaker tags if present
- Adapt idioms naturally; don't translate literally
- Keep proper nouns in their commonly-used form in {target_lang}
- Output ONLY the translated entries, nothing else

Subtitles:
{source_text}"""

def apply_translations(subs: list, translated_text: str) -> list:
    """Parse translated text and apply to subtitle objects."""
    pattern = r'\[(\d+)\]\s*(.*?)(?=\n\[|\Z)'
    matches = re.findall(pattern, translated_text, re.DOTALL)
    
    index_map = {sub.index: sub for sub in subs}
    for idx_str, content in matches:
        idx = int(idx_str)
        if idx in index_map:
            index_map[idx].content = content.strip()
    
    return subs

def adjust_timing_for_reading_speed(subs: list, target_lang: str) -> list:
    """Ensure minimum display time based on text length and language."""
    # Approximate reading speed (characters per second)
    reading_speed = {
        "zh": 4, "ja": 4, "ko": 5, "en": 20, "es": 18,
        "fr": 18, "de": 15, "ar": 18, "ru": 15, "pt": 18,
    }
    speed = reading_speed.get(target_lang, 15)
    min_duration = timedelta(seconds=1.2)
    
    for sub in subs:
        text_len = len(sub.content.replace('\n', ''))
        needed_duration = timedelta(seconds=text_len / speed)
        actual_duration = sub.end - sub.start
        
        if actual_duration < needed_duration and actual_duration < timedelta(seconds=5):
            # Extend end time, but don't overlap with next subtitle
            sub.end = sub.start + max(needed_duration, min_duration)
    
    # Fix overlaps
    for i in range(len(subs) - 1):
        if subs[i].end > subs[i+1].start:
            subs[i].end = subs[i+1].start - timedelta(milliseconds=100)
    
    return subs

# === Main Pipeline ===
if __name__ == "__main__":
    source_file = "subtitles_en.srt"
    target_file = "subtitles_zh.srt"
    
    # Load
    subs = load_srt(source_file)
    print(f"Loaded {len(subs)} subtitles")
    
    # Batch and translate (replace with your API call)
    batches = batch_subtitles(subs, BATCH_SIZE)
    for i, batch in enumerate(batches):
        prompt = build_translation_prompt(batch, SOURCE_LANG, TARGET_LANG)
        # translated = call_translation_api(prompt)  # Your API here
        # apply_translations(batch, translated)
        print(f"Batch {i+1}/{len(batches)} translated")
    
    # Adjust timing
    subs = adjust_timing_for_reading_speed(subs, TARGET_LANG)
    
    # Save
    save_srt(subs, target_file)
    print(f"Saved to {target_file}")
```

### Template 2: Command-Line Translation (Whisper + Translate)

```bash
## Full Pipeline: Transcribe → Translate → Generate Subtitles

### Step 1: Transcribe with Whisper
whisper video.mp4 --language en --model turbo --output_format srt --output_dir ./subs

### Step 2: Translate with Python script (using deep-translator)
pip install deep-translator pysrt

python3 - <<'EOF'
from deep_translator import GoogleTranslator
import pysrt

subs = pysrt.open('subs/video.srt')
translator = GoogleTranslator(source='en', target='zh-CN')

for sub in subs:
    translated = translator.translate(sub.text)
    sub.text = translated

subs.save('subs/video_zh.srt', encoding='utf-8')
print(f"Translated {len(subs)} subtitles")
EOF

### Step 3: Burn subtitles into video
ffmpeg -i video.mp4 -vf "subtitles=subs/video_zh.srt:force_style='FontName=Noto Sans CJK SC,FontSize=22'" output_zh.mp4

### Step 4: Create bilingual version
python3 - <<'EOF'
import pysrt

en_subs = pysrt.open('subs/video.srt')
zh_subs = pysrt.open('subs/video_zh.srt')

for en, zh in zip(en_subs, zh_subs):
    en.text = f"{zh.text}\n{en.text}"

en_subs.save('subs/video_bilingual.srt', encoding='utf-8')
EOF
```

### Template 3: Bilingual Subtitle Template (ASS)

```ass
[Script Info]
Title: Bilingual Subtitles
ScriptType: v4.00+
PlayResX: 1920
PlayResY: 1080

[V4+ Styles]
Format: Name, Fontname, Fontsize, PrimaryColour, SecondaryColour, OutlineColour, BackColour, Bold, Italic, Underline, StrikeOut, ScaleX, ScaleY, Spacing, Angle, BorderStyle, Outline, Shadow, Alignment, MarginL, MarginR, MarginV, Encoding
Style: Primary,Noto Sans CJK SC,52,&H00FFFFFF,&H000000FF,&H00000000,&H80000000,-1,0,0,0,100,100,0,0,1,3,1,2,20,20,40,1
Style: Secondary,Arial,40,&H0080DDFF,&H000000FF,&H00000000,&H80000000,0,-1,0,0,100,100,0,0,1,2,0,8,20,20,60,1

[Events]
Format: Layer, Start, End, Style, Name, MarginL, MarginR, MarginV, Effect, Text
Dialogue: 0,0:00:01.00,0:00:04.00,Primary,,0,0,0,,{\fad(300,300)}欢迎来到本教程
Dialogue: 0,0:00:01.00,0:00:04.00,Secondary,,0,0,0,,{\fad(300,300)\i1}Welcome to this tutorial

## Style Notes
# Primary (bottom): Target language, bold, larger
# Secondary (top, using \an8): Source language, italic, slightly smaller, different color
# Both fade in/out together for a cohesive look
```

### Template 4: Translation Quality Checklist

```
## Subtitle Translation QA Checklist

### Accuracy
- [ ] All sentences translated (no missing entries)
- [ ] Meaning preserved (not word-for-word, but conceptually accurate)
- [ ] Numbers, dates, and units converted correctly
- [ ] Proper nouns in their commonly-used target-language form
- [ ] Technical terms use industry-standard translations

### Readability
- [ ] Lines don't exceed character limit for target language
- [ ] No orphaned words (single word alone on a line)
- [ ] Line breaks at natural phrase boundaries
- [ ] No awkward word order from literal translation

### Timing
- [ ] Minimum display time met for each subtitle
- [ ] No overlapping subtitles
- [ ] Reading speed comfortable for target language
- [ ] Subtitles appear in sync with speech

### Cultural
- [ ] Idioms adapted, not literally translated
- [ ] Humor and wordplay localized where possible
- [ ] No culturally insensitive translations
- [ ] Units converted (miles → km, Fahrenheit → Celsius) where appropriate

### Technical
- [ ] File encoding: UTF-8 with BOM
- [ ] File format correct (SRT/ASS/VTT)
- [ ] Timestamps in correct format
- [ ] No empty subtitle entries
```

## Common Patterns

### Glossary Management

```
## Translation Glossary (CSV/JSON)

### For Consistent Translation Across Episodes
{
  "character_names": {
    "John": "约翰",
    "Dr. Smith": "史密斯博士"
  },
  "technical_terms": {
    "machine learning": "机器学习",
    "neural network": "神经网络",
    "gradient descent": "梯度下降"
  },
  "catchphrases": {
    "Let's get started!": "让我们开始吧！",
    "That's all for today": "今天就到这里"
  }
}

### Usage: Pre-process source text before translation
- Replace known terms with placeholders
- Translate
- Replace placeholders back with glossary terms
```

### Multi-Language Export

```
## Export Pipeline for Multiple Languages

### Directory Structure
subtitles/
├── en/
│   └── episode01.srt
├── zh/
│   └── episode01.srt
├── ja/
│   └── episode01.srt
├── ko/
│   └── episode01.srt
└── es/
    └── episode01.srt

### Batch Translation Script
for lang in zh ja ko es; do
  python translate_srt.py \
    --input subtitles/en/episode01.srt \
    --output subtitles/${lang}/episode01.srt \
    --source en \
    --target ${lang} \
    --glossary glossary.json
done
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Machine translation without review | Garbled or nonsensical output | Always have a human reviewer, at minimum spot-check |
| Keeping original line breaks | Target language may have different phrase structure | Re-break lines at natural phrase boundaries |
| Ignoring reading speed differences | Chinese subtitles need more time than English | Adjust timing per language reading speed table |
| Translating proper nouns literally | "New York" should not become "新约克" | Use established translations from glossary |
| Losing speaker identification | Multi-speaker content becomes confusing | Preserve `[Speaker A]` tags in translation |
| Not accounting for text expansion | German/French translations are 20-30% longer | Allow flexible line wrapping and timing |
| Translating cultural references literally | Jokes and idioms don't translate word-for-word | Adapt to target culture's equivalent expressions |
| Forgetting subtitle format specifics | ASS color codes, tags need careful handling | Preserve formatting tags when translating |
