# FFmpeg Master

> Turn natural language into precise FFmpeg pipelines. Cut, merge, convert, compress, and process videos without memorizing a single flag.

## When to Use

- Cut, trim, or split video clips by timecode
- Merge multiple video files into one
- Convert between formats (MP4, MKV, AVI, WebM, MOV)
- Compress videos to target file size or bitrate
- Extract audio tracks from video
- Add watermarks, overlays, or subtitles
- Batch process multiple files
- Hardware-accelerated encoding/decoding

## Instructions for AI Assistant

You are an FFmpeg expert. When the user describes a video processing task:

1. **Clarify the goal** — Ask about input format, output format, quality requirements, and target platform if not specified.
2. **Build the command incrementally** — Start with the core operation, then add filters and options.
3. **Explain each flag** — Never output a command without explaining what each significant flag does.
4. **Warn about destructive operations** — If the command will overwrite files or re-encode lossy→lossy, say so.
5. **Offer dry-run** — Suggest the user test on a short clip first for long videos.
6. **Check hardware** — Ask if the user has NVIDIA (nvenc), AMD (amf), Intel (qsv), or Apple Silicon (videotoolbox) for acceleration.

### Decision Tree

```
User wants to...
├── Cut/Trim → Use -ss / -to / -t with -c copy (stream copy, no re-encode)
├── Merge → Use concat demuxer for same-format, concat filter for mixed
├── Convert → Identify source codec, choose target, set quality (CRF / bitrate)
├── Compress → Use CRF mode (libx264 CRF 23-28, libx265 CRF 24-30)
├── Extract audio → Use -vn with appropriate audio codec
├── Add watermark → Use overlay filter with position expressions
├── Batch process → Build shell loop or use -f concat
└── Speed change → Use setpts (video) and atempo (audio) filters
```

## Templates

### Template 1: Cut a Segment (No Re-encode)

```bash
# Cut from 01:30 to 03:45 without re-encoding
ffmpeg -i input.mp4 -ss 00:01:30 -to 00:03:45 -c copy output.mp4

# Cut first 60 seconds
ffmpeg -i input.mp4 -t 60 -c copy output.mp4

# Note: -ss before -i is fast seek (approximate), after -i is precise seek
# For precise cuts, put -ss after -i:
ffmpeg -i input.mp4 -ss 00:01:30 -to 00:03:45 -c copy output.mp4
```

### Template 2: Merge Multiple Videos

```bash
# Method 1: Concat demuxer (same codec/container required)
# Create filelist.txt:
# file 'part1.mp4'
# file 'part2.mp4'
# file 'part3.mp4'
ffmpeg -f concat -safe 0 -i filelist.txt -c copy merged.mp4

# Method 2: Concat filter (works with different codecs/formats)
ffmpeg -i part1.mp4 -i part2.mp4 -i part3.mp4 \
  -filter_complex "[0:v][0:a][1:v][1:a][2:v][2:a]concat=n=3:v=1:a=1[outv][outa]" \
  -map "[outv]" -map "[outa]" merged.mp4
```

### Template 3: Compress Video

```bash
# H.264 with CRF (constant quality, smaller file)
ffmpeg -i input.mp4 -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 128k output.mp4

# H.265 for better compression (slower encode, smaller file)
ffmpeg -i input.mp4 -c:v libx265 -crf 28 -preset medium -c:a aac -b:a 128k output.mp4

# Target specific file size (two-pass)
# Example: 50MB target for a 10-minute video
# Bitrate = (50 * 8 * 1024) / 600 ≈ 682 kbps
ffmpeg -i input.mp4 -c:v libx264 -b:v 682k -pass 1 -an -f null /dev/null
ffmpeg -i input.mp4 -c:v libx264 -b:v 682k -pass 2 -c:a aac -b:a 128k output.mp4
```

### Template 4: Hardware-Accelerated Encoding

```bash
# NVIDIA NVENC (H.264)
ffmpeg -i input.mp4 -c:v h264_nvenc -preset p4 -cq 23 -c:a aac output.mp4

# NVIDIA NVENC (H.265/HEVC)
ffmpeg -i input.mp4 -c:v hevc_nvenc -preset p4 -cq 28 -c:a aac output.mp4

# Intel Quick Sync
ffmpeg -i input.mp4 -c:v h264_qsv -preset medium -global_quality 23 output.mp4

# Apple VideoToolbox (macOS)
ffmpeg -i input.mp4 -c:v h264_videotoolbox -b:v 5M output.mp4

# AMD AMF
ffmpeg -i input.mp4 -c:v h264_amf -quality quality -rc cqp -qp 23 output.mp4
```

### Template 5: Extract Audio

```bash
# Extract audio as MP3
ffmpeg -i input.mp4 -vn -c:a libmp3lame -q:a 2 output.mp3

# Extract audio as AAC (copy, no re-encode)
ffmpeg -i input.mp4 -vn -c:a copy output.aac

# Extract audio as WAV (lossless)
ffmpeg -i input.mp4 -vn -c:a pcm_s16le output.wav

# Extract specific audio stream
ffmpeg -i input.mp4 -map 0:a:0 -c:a copy output.aac
```

### Template 6: Add Watermark

```bash
# Bottom-right corner with 10px padding
ffmpeg -i input.mp4 -i watermark.png \
  -filter_complex "overlay=W-w-10:H-h-10" output.mp4

# Top-left with transparency
ffmpeg -i input.mp4 -i watermark.png \
  -filter_complex "[0:v][1:v]overlay=10:10:format=auto" output.mp4

# Animated watermark (fade in/out)
ffmpeg -i input.mp4 -i watermark.png \
  -filter_complex "[1:v]format=rgba,fade=in:st=0:d=1:alpha=1,fade=out:st=4:d=1:alpha=1[wm];[0:v][wm]overlay=10:10" \
  output.mp4
```

## Common Patterns

### Batch Processing

```bash
# Convert all AVI files to MP4
for f in *.avi; do
  ffmpeg -i "$f" -c:v libx264 -crf 23 -c:a aac "${f%.avi}.mp4"
done

# Compress all MP4 files in a directory
for f in *.mp4; do
  ffmpeg -i "$f" -c:v libx265 -crf 28 -c:a aac "compressed_${f}"
done

# Windows PowerShell equivalent
Get-ChildItem *.avi | ForEach-Object {
  ffmpeg -i $_.FullName -c:v libx264 -crf 23 -c:a aac ($_.BaseName + ".mp4")
}
```

### Speed Change

```bash
# 2x speed (half duration)
ffmpeg -i input.mp4 -filter_complex "[0:v]setpts=0.5*PTS[v];[0:a]atempo=2.0[a]" -map "[v]" -map "[a]" output.mp4

# 0.5x speed (double duration)
ffmpeg -i input.mp4 -filter_complex "[0:v]setpts=2.0*PTS[v];[0:a]atempo=0.5[a]" -map "[v]" -map "[a]" output.mp4

# 4x speed (atempo only supports 0.5-2.0, chain for larger)
ffmpeg -i input.mp4 -filter_complex "[0:v]setpts=0.25*PTS[v];[0:a]atempo=2.0,atempo=2.0[a]" -map "[v]" -map "[a]" output.mp4
```

### Resolution & Aspect Ratio

```bash
# Scale to 1080p (maintain aspect ratio)
ffmpeg -i input.mp4 -vf "scale=-2:1080" output.mp4

# Scale to 720p
ffmpeg -i input.mp4 -vf "scale=-2:720" output.mp4

# Pad to 16:9 (add black bars)
ffmpeg -i input.mp4 -vf "scale=1920:1080:force_original_aspect_ratio=decrease,pad=1920:1080:(ow-iw)/2:(oh-ih)/2" output.mp4

# Crop to 9:16 (vertical/portrait from landscape)
ffmpeg -i input.mp4 -vf "crop=ih*9/16:ih" output.mp4
```

### GIF Conversion

```bash
# Video to high-quality GIF
ffmpeg -i input.mp4 -vf "fps=15,scale=480:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" output.gif

# Video to GIF with size limit
ffmpeg -i input.mp4 -vf "fps=10,scale=320:-1:flags=lanczos" -t 10 output.gif
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| `-ss` before `-i` for precise cuts | Fast seek is approximate, may cut at wrong frame | Put `-ss` after `-i` for frame-accurate cuts |
| Re-encoding when you don't need to | Quality loss + wasted time | Use `-c copy` for cut/merge of same-format files |
| CRF 0 thinking it's "lossless" | For H.264, CRF 0 is near-lossless but not truly lossless | Use `-c:v libx264 -qp 0` or FFV1 for true lossless |
| Using `-b:v` without two-pass | Single-pass VBR is less efficient for target bitrate | Use two-pass for target file size; use CRF for quality |
| Mixing container formats in concat demuxer | Concat demuxer requires identical codecs/containers | Use concat filter for mixed formats |
| Forgetting `-movflags +faststart` for web | MP4 won't play until fully downloaded | Add `-movflags +faststart` for streaming/web playback |
| Assuming FFmpeg version/features | Older FFmpeg may lack filters or codecs | Always check `ffmpeg -version` and `ffmpeg -encoders` |
| Not quoting paths with spaces | Shell will split the path | Always quote: `ffmpeg -i "my file.mp4"` |

## CRF Quality Reference

| CRF | Quality | Use Case |
|-----|---------|----------|
| 18 | Visually lossless | Archival, mastering |
| 20 | Near-transparent | High-quality distribution |
| 23 | Default, good | General purpose |
| 26 | Acceptable | Web streaming |
| 28 | Noticeable artifacts | Mobile/low bandwidth |
| 30+ | Poor | Preview/thumbnails only |

---

## 中文版本

### 使用场景

- 按时间码裁剪、分割视频片段
- 合并多个视频文件为一个
- 格式转换（MP4、MKV、AVI、WebM、MOV）
- 按目标文件大小或码率压缩视频
- 从视频中提取音频轨道
- 添加水印、叠加层或字幕
- 批量处理多个文件
- 硬件加速编解码

### 核心步骤

1. **明确目标** — 确认输入/输出格式、质量要求和目标平台
2. **逐步构建命令** — 从核心操作开始，再添加滤镜和选项
3. **解释每个参数** — 确保理解每个关键 flag 的作用
4. **破坏性操作警告** — 覆盖文件或有损→有损重编码前必须提醒
5. **先试后用** — 长视频建议先在短片段上测试
6. **检查硬件加速** — 确认是否有 NVIDIA (nvenc)、AMD (amf)、Intel (qsv) 或 Apple Silicon

### 模板说明

| 模板 | 用途 | 关键参数 |
|------|------|----------|
| 裁剪片段 | 无重编码切割 | `-ss`/`-to` + `-c copy` |
| 合并视频 | 拼接多个文件 | concat demuxer（同格式）或 concat filter（混合格式） |
| 压缩视频 | 控制文件大小 | CRF 模式（H.264: 23-28, H.265: 24-30） |
| 硬件加速编码 | 利用 GPU 加速 | nvenc/qsv/videotoolbox/amf |
| 提取音频 | 分离音轨 | `-vn` + 音频编码器 |
| 添加水印 | 叠加图片 | overlay 滤镜 + 位置表达式 |

### 常见陷阱

| 陷阱 | 问题 | 解决方案 |
|------|------|----------|
| `-ss` 放在 `-i` 前面做精确裁剪 | 快速定位是近似的，可能切错帧 | 精确裁剪时将 `-ss` 放在 `-i` 之后 |
| 不必要的重编码 | 质量损失 + 浪费时间 | 同格式文件裁剪/合并用 `-c copy` |
| CRF 0 以为是无损 | H.264 CRF 0 只是接近无损 | 真正无损用 `-qp 0` 或 FFV1 |
| 单次 VBR 码率控制 | 不如双 pass 高效 | 目标文件大小用双 pass；质量优先用 CRF |
| concat demuxer 混用容器格式 | 要求完全相同的编码/容器 | 混合格式用 concat filter |
| Web 视频忘记 `-movflags +faststart` | MP4 需要完全下载才能播放 | 流媒体/网页播放必须加此参数 |
