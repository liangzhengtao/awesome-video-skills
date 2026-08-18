# Audio Processing & Mixing

> Process audio for videos — noise removal, normalization, equalization, compression, and background music mixing.

## When to Use

- Removing background noise from recorded audio
- Normalizing audio levels to broadcast standards
- Equalizing voice recordings for clarity
- Mixing background music with dialogue
- Adding sound effects and ambient audio
- Processing podcast or interview audio
- Converting audio formats and sample rates

## Instructions for AI Assistant

You are an audio processing expert covering FFmpeg audio filters, Audacity workflows, and programmatic audio processing. When the user describes an audio task:

1. **Identify the problem** — Is it noise, levels, frequency balance, or mixing?
2. **Choose the right tool** — FFmpeg for batch/programmatic, Audacity for interactive, Python for custom.
3. **Preserve quality** — Always work in WAV/FLAC until final export.
4. **Check loudness standards** — Match the target platform's requirements.
5. **Non-destructive workflow** — Keep original files untouched; always output to new files.
6. **Order of operations** — Noise removal → EQ → Compression → Normalization → Limiting.

### Audio Processing Chain

```
Source Audio
  → Noise Reduction (remove hum, hiss, room noise)
  → EQ (remove mud, add presence)
  → De-Esser (tame sibilance)
  → Compressor (even out dynamics)
  → Normalize (set target loudness)
  → Limiter (prevent clipping)
  → Output (format conversion)
```

## Templates

### Template 1: FFmpeg Audio Filters

```bash
## Noise Removal
# High-pass filter (remove low-frequency rumble below 80Hz)
ffmpeg -i input.wav -af "highpass=f=80" output.wav

# Low-pass filter (remove high-frequency hiss above 8kHz)
ffmpeg -i input.wav -af "lowpass=f=8000" output.wav

# Band-pass (keep only voice frequencies 300Hz-3kHz)
ffmpeg -i input.wav -af "highpass=f=300,lowpass=f=3000" output.wav

# Afftdn (FFmpeg's built-in noise reduction)
ffmpeg -i input.wav -af "afftdn=nf=-25" output.wav
# nf = noise floor in dB (more negative = more reduction)

## Equalization
# Boost presence (2-5kHz for voice clarity)
ffmpeg -i input.wav -af "equalizer=f=3000:t=q:w=1.5:g=3" output.wav

# Cut mud (200-400Hz range)
ffmpeg -i input.wav -af "equalizer=f=300:t=q:w=1:g=-4" output.wav

# Bass boost
ffmpeg -i input.wav -af "equalizer=f=100:t=q:w=1:g=4" output.wav

# De-essing (reduce sibilance at 5-8kHz)
ffmpeg -i input.wav -af "equalizer=f=6000:t=q:w=2:g=-6" output.wav

## Compression
# Voice compressor
ffmpeg -i input.wav -af "acompressor=threshold=-20dB:ratio=4:attack=5:release=50:makeup=2" output.wav

# Gentle music compressor
ffmpeg -i input.wav -af "acompressor=threshold=-18dB:ratio=2:attack=20:release=200:makeup=1" output.wav

## Normalization
# Loudness normalization (EBU R128)
ffmpeg -i input.wav -af "loudnorm=I=-16:TP=-1.5:LRA=11" output.wav

# Peak normalization to -1dB
ffmpeg -i input.wav -af "volume=0dB:precision=fixed" -af "alimiter=limit=0.891" output.wav

# Simple volume adjustment (+3dB)
ffmpeg -i input.wav -af "volume=3dB" output.wav

## Complete Processing Chain
ffmpeg -i input.wav -af "\
  highpass=f=80,\
  afftdn=nf=-20,\
  equalizer=f=300:t=q:w=1:g=-3,\
  equalizer=f=3000:t=q:w=1.5:g=2,\
  acompressor=threshold=-20dB:ratio=4:attack=5:release=50:makeup=2,\
  loudnorm=I=-16:TP=-1.5:LRA=11\
" output.wav
```

### Template 2: Audio Mixing with FFmpeg

```bash
## Mix Voice + Background Music
# Simple overlay (voice on top of music)
ffmpeg -i voice.wav -i music.wav \
  -filter_complex "[0:a]volume=1.0[voice];[1:a]volume=0.15[music];[voice][music]amix=inputs=2:duration=first" \
  output.wav

# Sidechain-style ducking (music lowers when voice plays)
ffmpeg -i voice.wav -i music.wav \
  -filter_complex "[1:a][0:a]sidechaincompress=threshold=0.02:ratio=20:attack=5:release=200[music_ducked];[0:a][music_ducked]amix=inputs=2:duration=first" \
  output.wav

# Fade in/out for music
ffmpeg -i voice.wav -i music.wav \
  -filter_complex "[1:a]afade=t=in:st=0:d=2,afade=t=out:st=58:d=2,volume=0.15[music];[0:a][music]amix=inputs=2:duration=first" \
  output.wav

## Add Intro/Outro Music
# Concatenate: intro_music → voiceover → outro_music
ffmpeg -i intro.mp3 -i voiceover.wav -i outro.mp3 \
  -filter_complex "\
    [0:a]afade=t=out:st=3:d=1,volume=0.8[intro];\
    [1:a]volume=1.0[voice];\
    [2:a]afade=t=in:st=0:d=1,volume=0.8[outro];\
    [intro][voice][outro]concat=n=3:v=0:a=1[out]" \
  -map "[out]" output.wav

## Extract and Replace Audio in Video
# Extract audio
ffmpeg -i video.mp4 -vn audio_only.wav

# Process audio (apply filters)
ffmpeg -i audio_only.wav -af "loudnorm=I=-14:TP=-1.5" processed.wav

# Replace audio in video
ffmpeg -i video.mp4 -i processed.wav -c:v copy -map 0:v -map 1:a output.mp4
```

### Template 3: Python Audio Processing (pydub)

```python
#!/usr/bin/env python3
"""
Audio Processing Pipeline using pydub
pip install pydub numpy scipy
"""

from pydub import AudioSegment
from pydub.effects import normalize, compress_dynamic_range
from pydub.silence import split_on_silence
import numpy as np

def load_audio(filepath: str) -> AudioSegment:
    """Load any audio format."""
    return AudioSegment.from_file(filepath)

def remove_silence(audio: AudioSegment, 
                   silence_thresh=-40, 
                   min_silence_len=500) -> AudioSegment:
    """Remove silent portions from audio."""
    chunks = split_on_silence(
        audio,
        min_silence_len=min_silence_len,
        silence_thresh=silence_thresh,
        keep_silence=250  # Keep 250ms padding
    )
    if chunks:
        return sum(chunks)
    return audio

def adjust_speed(audio: AudioSegment, speed: float) -> AudioSegment:
    """Change audio speed without changing pitch (approximate)."""
    # pydub doesn't have native time-stretch
    # Use ffmpeg under the hood for better quality
    import tempfile, subprocess
    with tempfile.NamedTemporaryFile(suffix='.wav', delete=False) as tmp_in:
        audio.export(tmp_in.name, format='wav')
        tmp_out = tmp_in.name.replace('.wav', '_out.wav')
        subprocess.run([
            'ffmpeg', '-y', '-i', tmp_in.name,
            '-filter:a', f'atempo={speed}',
            tmp_out
        ], capture_output=True)
        return AudioSegment.from_wav(tmp_out)

def add_background_music(voice: AudioSegment, 
                         music: AudioSegment, 
                         music_volume: float = -18) -> AudioSegment:
    """Mix background music under voice."""
    # Adjust music length to match voice
    if len(music) < len(voice):
        # Loop music
        loops = (len(voice) // len(music)) + 1
        music = music * loops
    
    # Trim to voice length
    music = music[:len(voice)]
    
    # Apply fade in/out
    music = music.fade_in(2000).fade_out(3000)
    
    # Adjust volume
    music = music + music_volume  # dB adjustment
    
    # Mix
    return voice.overlay(music)

def batch_process(input_dir: str, output_dir: str, 
                  target_lufs: float = -16.0):
    """Batch process all audio files in a directory."""
    import os, glob
    os.makedirs(output_dir, exist_ok=True)
    
    for filepath in glob.glob(os.path.join(input_dir, '*.*')):
        if not filepath.lower().endswith(('.wav', '.mp3', '.m4a', '.flac')):
            continue
        
        print(f"Processing: {filepath}")
        audio = load_audio(filepath)
        
        # Process chain
        audio = normalize(audio, headroom=1.0)  # Normalize to -1dBFS
        audio = compress_dynamic_range(
            audio,
            threshold=-20.0,
            ratio=4.0,
            attack=5.0,
            release=50.0
        )
        
        # Export
        filename = os.path.basename(filepath)
        output_path = os.path.join(output_dir, filename)
        audio.export(output_path, format='wav')
        print(f"  → Saved: {output_path}")

# === Usage ===
if __name__ == "__main__":
    # Load
    voice = load_audio("voiceover.wav")
    music = load_audio("background_music.mp3")
    
    # Process voice
    voice = normalize(voice, headroom=1.0)
    voice = compress_dynamic_range(voice, threshold=-20, ratio=4)
    
    # Mix
    final = add_background_music(voice, music, music_volume=-18)
    
    # Export
    final.export("final_mix.wav", format="wav")
    print("Mix exported successfully")
```

### Template 4: Audacity Macro / Chain

```
## Audacity Processing Chains

### Voice Processing Chain
1. Noise Reduction
   - Get Noise Profile from silent section
   - Amount: 12dB, Sensitivity: 6, Frequency Smoothing: 3

2. Equalization
   - High-pass filter: 80Hz, 6dB/octave
   - Presence boost: +3dB at 3kHz, Q=1.5
   - Mud cut: -3dB at 300Hz, Q=1

3. Compressor
   - Threshold: -20dB
   - Noise Floor: -40dB
   - Ratio: 4:1
   - Attack: 0.1s
   - Release: 0.5s
   - Make-up gain: Yes

4. Limiter
   - Type: Soft Limit
   - Limit to: -1dB
   - Hold: 0ms

5. Loudness Normalization
   - Normalize to: -16 LUFS

### Music Mastering Chain
1. EQ: High-pass at 30Hz
2. Compressor: Threshold -14dB, Ratio 2:1, slow attack/release
3. Limiter: -0.3dB ceiling
4. Loudness: -14 LUFS
```

### Template 5: Sound Effects Library Organization

```
## SFX Library Structure
sound_effects/
├── transitions/
│   ├── whoosh_01.wav
│   ├── swoosh_02.wav
│   └── riser_01.wav
├── ui/
│   ├── click_01.wav
│   ├── notification_01.wav
│   └── pop_01.wav
├── ambient/
│   ├── room_tone_quiet.wav
│   ├── city_traffic.wav
│   └── nature_birds.wav
├── impacts/
│   ├── bass_hit_01.wav
│   ├── cinematic_boom.wav
│   └── punch_01.wav
└── music/
    ├── intro_jingle.wav
    ├── background_chill.wav
    └── outro_theme.wav

## Free SFX Sources
- freesound.org (CC licensed)
- mixkit.co (royalty free)
- zapsplat.com (free with attribution)
- pixabay.com/sound-effects (royalty free)
```

## Common Patterns

### Podcast / Interview Processing

```
## Quick Podcast Processing Chain

1. Record in quiet room with good mic (dynamic preferred)
2. Noise removal: FFmpeg afftdn or Audacity noise profile
3. EQ: highpass=80, cut mud at 250-400, presence boost 2-5k
4. Compressor: threshold=-18dB, ratio=3:1, attack=10ms, release=100ms
5. Normalize to -16 LUFS (YouTube) or -19 LUFS (Spotify)
6. Export: MP3 128kbps (mono) or 320kbps (stereo)
```

### Room Tone Generation

```bash
# Generate room tone (silence with subtle noise floor)
ffmpeg -f lavfi -i "anoisesrc=d=10:c=pink:r=44100:a=0.001" room_tone.wav

# Use for filling gaps in dialogue editing
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Normalizing before compression | Compressor changes peak levels, undoing normalization | Always: Noise → EQ → Compress → Normalize → Limit |
| Too much noise reduction | Creates underwater/robotic artifacts | Use minimal settings (6-12dB), accept some background noise |
| Not dithering when reducing bit depth | Quantization noise in quiet passages | Enable dither when going from 24-bit to 16-bit |
| Mixing music and voice at same level | Music masks the voice | Music should be 12-18dB below voice level |
| Processing MP3/AAC and re-encoding | Double compression artifacts | Always work in WAV/FLAC until final export |
| Ignoring sample rate mismatch | Pops, clicks, or speed changes | Match all source files to the project sample rate |
| Over-compressing dynamics | Audio sounds flat and lifeless | Use gentle ratios (2:1 to 4:1), preserve natural dynamics |
| Not checking on multiple devices | Audio may sound good on headphones but bad on speakers | Check mix on headphones, speakers, and phone |

---

## 中文版本

### 使用场景

- 去除录音中的背景噪音
- 将音频电平归一化到广播标准
- 均衡人声录音以提高清晰度
- 混合背景音乐与对白
- 添加音效和环境音
- 处理播客或采访音频
- 转换音频格式和采样率

### 核心步骤

1. **识别问题** — 确认是噪音、电平、频率平衡还是混音问题
2. **选对工具** — FFmpeg 做批处理/编程，Audacity 做交互式，Python 做自定义
3. **保持品质** — 最终导出前始终用 WAV/FLAC 工作
4. **检查响度标准** — 匹配目标平台要求（YouTube: -14 LUFS）
5. **非破坏性工作流** — 原始文件不动，始终输出到新文件
6. **处理顺序** — 降噪 → EQ → 压缩 → 归一化 → 限幅

### 模板说明

| 模板 | 用途 | 要点 |
|------|------|------|
| FFmpeg 音频滤镜 | 降噪/EQ/压缩/归一化 | highpass/lowpass/afftdn/equalizer/acompressor/loudnorm |
| FFmpeg 音频混合 | 人声+音乐混合 | 简单叠加、侧链压低（音乐自动让位）、淡入淡出 |
| Python pydub 处理 | 程序化音频处理 | 静音去除、速度调整、背景音乐混合、批量处理 |
| Audacity 处理链 | 交互式处理 | 降噪→EQ→压缩→限幅→响度归一化，完整人声处理链 |

### 常见陷阱

| 陷阱 | 问题 | 解决方案 |
|------|------|----------|
| 先归一化再压缩 | 压缩器改变峰值，归一化白做 | 始终按顺序：降噪→EQ→压缩→归一化→限幅 |
| 降噪过度 | 产生水下/机器人音效 | 用最小设置（6-12dB），接受少量背景噪音 |
| 降低位深不加抖动 | 安静段落出现量化噪声 | 24-bit 转 16-bit 时启用 dither |
| 音乐和人声同电平 | 音乐掩盖人声 | 音乐应低于人声 12-18dB |
| 处理 MP3/AAC 再重编码 | 双重压缩伪影 | 最终导出前始终用 WAV/FLAC 工作 |
| 忽略采样率不匹配 | 爆音、咔嗒声或速度变化 | 所有源文件匹配项目采样率 |
| 过度压缩动态 | 音频平淡无生气 | 用温和比率（2:1 到 4:1），保留自然动态 |
