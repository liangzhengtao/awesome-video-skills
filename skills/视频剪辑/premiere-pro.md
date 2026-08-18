# Adobe Premiere Pro

> Professional video editing workflows in Premiere Pro — sequence setup, export presets, Dynamic Link, Essential Graphics, and platform-specific delivery.

## When to Use

- Setting up sequences for YouTube, TikTok, Instagram, or broadcast
- Creating and using export presets for different platforms
- Working with Dynamic Link to After Effects and Audition
- Building Essential Graphics templates for titles and lower thirds
- Multi-camera editing and sync workflows
- Color correction with Lumetri Color panel
- Audio mixing and sound design in Premiere

## Instructions for AI Assistant

You are an Adobe Premiere Pro expert. When the user describes an editing task:

1. **Identify the workflow** — Is this editing, effects, audio, or delivery?
2. **Version-specific features** — Premiere Pro evolves rapidly; ask about version if it matters.
3. **Provide menu paths** — Premiere has deep menus; give exact paths (e.g., File → Export → Media).
4. **Preset-first approach** — Always recommend saving reusable presets.
5. **Cross-app integration** — Premiere rarely works alone; consider Dynamic Link with After Effects, Audition, Media Encoder.

### Premiere Pro Ecosystem

```
Premiere Pro ──→ After Effects (Dynamic Link for VFX/motion graphics)
       │
       ├──→ Audition (roundtrip audio editing)
       │
       ├──→ Media Encoder (batch rendering, watch folders)
       │
       └──→ Photoshop / Illustrator (Dynamic Link for graphics)
```

## Templates

### Template 1: Sequence Settings by Platform

```
## YouTube (16:9 Landscape)
- Frame Size: 1920x1080 (or 3840x2160)
- Pixel Aspect Ratio: Square Pixels
- Frame Rate: 23.976 / 25 / 29.97 / 59.94
- Fields: No Fields (Progressive Scan)
- Audio: 48kHz, Stereo

## YouTube Shorts / TikTok / Instagram Reels (9:16 Portrait)
- Frame Size: 1080x1920
- Pixel Aspect Ratio: Square Pixels
- Frame Rate: 30fps
- Fields: No Fields

## Instagram Feed (1:1 Square)
- Frame Size: 1080x1080
- Pixel Aspect Ratio: Square Pixels
- Frame Rate: 30fps

## Instagram Stories (9:16)
- Frame Size: 1080x1920
- Frame Rate: 30fps

## Twitter/X (16:9 or 1:1)
- Frame Size: 1920x1080 or 1080x1080
- Frame Rate: 30fps
- Max length: 2:20 (standard) or 10:00 (longer)

## Broadcast (NTSC)
- Frame Size: 1920x1080
- Frame Rate: 29.97fps
- Fields: Upper Field First (interlaced)
- Audio: 48kHz, Stereo

## Cinema / Film
- Frame Size: 4096x2160 (4K DCI) or 2048x1080 (2K DCI)
- Frame Rate: 23.976 / 24fps
- Pixel Aspect Ratio: Square Pixels
```

### Template 2: Export Presets (Media Encoder)

```
## YouTube 1080p (H.264)
- Format: H.264
- Preset: YouTube 1080p HD (built-in, then customize)
- Target Bitrate: 16 Mbps (VBR 2-pass)
- Maximum Bitrate: 20 Mbps
- Profile: High
- Level: 4.2
- Audio: AAC, 320kbps, Stereo
- Multiplexer: MP4
- ✅ Use Maximum Render Quality
- ✅ Render at Maximum Depth

## YouTube 4K (H.265)
- Format: H.265/HEVC
- Target Bitrate: 40-60 Mbps (VBR 2-pass)
- Profile: Main 10
- Audio: AAC, 320kbps

## TikTok / Reels (Mobile Optimized)
- Format: H.264
- Resolution: 1080x1920
- Target Bitrate: 10 Mbps (VBR)
- Profile: High
- Audio: AAC, 256kbps

## Web / Low Bandwidth
- Format: H.264
- Resolution: 1280x720
- Target Bitrate: 5 Mbps
- Profile: Main
- Audio: AAC, 128kbps

## Archival (ProRes)
- Format: QuickTime
- Codec: Apple ProRes 422 HQ
- Audio: Uncompressed PCM, 48kHz, 24-bit
```

### Template 3: Essential Graphics Templates

```
## Lower Third Template Structure

### Layer Stack (Essential Graphics panel)
1. Background Shape
   - Rounded rectangle, full width, 120px height
   - Color: Dark with 90% opacity
   - Position: Bottom-left

2. Name Text
   - Font: Montserrat Bold, 36pt
   - Color: White
   - Position: Inside background, left-aligned

3. Title Text
   - Font: Montserrat Regular, 24pt
   - Color: #CCCCCC
   - Position: Below name

4. Accent Line
   - Rectangle, 4px height, brand color
   - Position: Left edge of background

### Animatable Properties (Export as MOGRT)
- Opacity (fade in/out)
- Position X (slide in from left)
- Name text content (editable text)
- Title text content (editable text)
- Accent color (editable color)

### Export
- Essential Graphics Panel → Export as Motion Graphics Template
- Compatibility: Premiere Pro
- Include: Static thumbnail, multiple font weights
```

### Template 4: Dynamic Link Workflow

```
## Premiere → After Effects (Dynamic Link)

### Creating a Dynamic Link Comp
1. Select clip(s) in Premiere timeline
2. Right-click → Replace With After Effects Composition
3. After Effects opens with the clip in a new comp
4. Edit in After Effects → changes appear live in Premiere

### Best Practices
- Keep Dynamic Link comps short (under 30 seconds)
- Render/preview in After Effects before switching back
- If playback is slow, right-click in Premiere → Render and Replace
- Unrender Replace: Right-click → Restore Unrendered

## Premiere → Audition (Roundtrip Audio)

### Sending Audio to Audition
1. Select clip in timeline
2. Right-click → Edit Clip in Adobe Audition
3. Audition opens with the audio + video reference
4. Edit (noise removal, EQ, restoration)
5. Save → updates automatically in Premiere

### Audition Favorites for Video
- Noise Reduction: Capture noise print → reduce by 12-18dB
- DeReverb: Reduce reverb, Amount 40-60%
- Loudness Meter: Target -14 LUFS for YouTube
```

## Common Patterns

### Multi-Camera Editing

```
## Setup
1. Import all camera angles
2. Select all clips → Right-click → Create Multi-Camera Source Sequence
3. Sync method: Audio (if all cameras recorded audio) or Timecode
4. Open in Timeline → Toggle Multi-Camera (wrench icon in Program Monitor)

## Editing
- Play sequence and click on camera angles in real-time
- Or, make cuts manually and switch angles per segment
- Flatten multicam when done: Right-click → Flatten
```

### Proxy Workflow

```
## Setting Up Proxies
1. Select clips in Project panel
2. Right-click → Proxy → Create Proxies
3. Format: QuickTime, Codec: ProRes 422 Proxy (or H.264 1024x540)
4. Destination: Same as project or dedicated proxy folder

## Toggling Proxies
- Button Editor (Program Monitor wrench icon) → Drag "Toggle Proxies" to toolbar
- Blue outline = proxy mode on, off = full resolution
- Always toggle OFF before final export

## Keyboard Shortcut
- Assign Toggle Proxies in Edit → Keyboard Shortcuts
```

### Color Correction (Lumetri)

```
## Basic Correction
1. Lumetri Color panel → Basic Correction
2. Input LUT: Apply camera-specific LUT (e.g., Sony S-Log3 to Rec.709)
3. White Balance: Use eyedropper on neutral gray
4. Exposure, Contrast, Highlights, Shadows, Whites, Blacks

## Creative Grade
1. Creative tab → Look (apply a LUT, reduce intensity with Faded Film slider)
2. Color Wheels: Lift (shadows), Gamma (midtones), Gain (highlights)
3. Curves: Fine-tune contrast with RGB curves
4. HSL Secondary: Isolate specific colors for targeted correction

## Scopes (Always Check!)
- Lumetri Scopes panel (Window → Lumetri Scopes)
- Waveform (Y): Check exposure levels
- Vectorscope: Check skin tones (should fall on skin tone line)
- Parade (RGB): Check color balance
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Not setting sequence to match footage | Frame rate/resolution mismatches cause rendering issues | Right-click clip → New Sequence From Clip |
| Exporting without checking "Use Maximum Render Quality" | Scaling artifacts, banding | Always enable for final exports |
| Too many Dynamic Link comps | Premiere playback becomes extremely slow | Render and Replace; keep comps short |
| Ignoring GPU acceleration | Software-only rendering is 5-10x slower | File → Project Settings → General → Renderer: Mercury Playback (GPU) |
| Editing H.265 directly | H.265 is computationally expensive for real-time editing | Use proxies or transcode to ProRes/DNxHR first |
| Not saving presets | Recreating the same export settings every time | Save as preset in Media Encoder |
| Overwriting source files on export | Losing original footage is permanent | Always export to a separate folder |
| Using VBR 1-pass for target bitrate | Less efficient than 2-pass | Use 2-pass VBR when targeting specific file size |

---

## 中文版本

### 使用场景

- 为 YouTube、TikTok、Instagram 或电视台设置序列
- 创建和使用不同平台的导出预设
- 通过 Dynamic Link 联动 After Effects 和 Audition
- 构建 Essential Graphics 模板（标题、下方三分之一字幕条）
- 多机位编辑和同步工作流
- 使用 Lumetri Color 面板调色
- 在 Premiere 中进行音频混合和声音设计

### 核心步骤

1. **识别工作流** — 确认是编辑、特效、音频还是输出任务
2. **版本特性** — Premiere Pro 迭代快，关键功能需确认版本
3. **提供菜单路径** — Premiere 菜单层级深，给出精确路径（如 File → Export → Media）
4. **预设优先** — 始终建议保存可复用的导出预设
5. **跨应用集成** — 考虑 Dynamic Link 联动 AE、Audition、Media Encoder

### 模板说明

| 模板 | 用途 | 要点 |
|------|------|------|
| 序列设置 | 各平台序列参数 | YouTube 16:9 / TikTok 9:16 / Instagram 1:1 / 广播 NTSC |
| 导出预设 | Media Encoder 批量导出 | YouTube 1080p 16Mbps VBR 2-pass，TikTok 10Mbps |
| Essential Graphics | 动态图形模板 | 背景条 + 姓名文字 + 标题文字 + 强调线，可导出为 MOGRT |
| Dynamic Link | 联动 AE/Audition | 替换为 AE 合成、右键编辑到 Audition，保持短合成 |

### 常见陷阱

| 陷阱 | 问题 | 解决方案 |
|------|------|----------|
| 序列设置不匹配素材 | 帧率/分辨率不匹配导致渲染问题 | 右键素材 → New Sequence From Clip |
| 导出不勾选 Maximum Render Quality | 缩放伪影、色带 | 最终导出始终启用 |
| Dynamic Link 合成太多 | 回放极其缓慢 | 渲染并替换，保持合成短小 |
| 忽略 GPU 加速 | 仅软件渲染慢 5-10 倍 | File → Project Settings → General → Renderer: GPU |
| 直接编辑 H.265 | 实时编辑计算开销大 | 使用代理或先转码为 ProRes/DNxHR |
| 不保存预设 | 每次重复创建相同导出设置 | 在 Media Encoder 中保存为预设 |
