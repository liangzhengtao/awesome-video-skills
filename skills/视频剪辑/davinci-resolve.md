# DaVinci Resolve Workflow

> AI-assisted DaVinci Resolve workflows — from project setup to color grading, Fusion compositing, Fairlight audio mixing, and final delivery.

## When to Use

- Setting up a new DaVinci Resolve project with optimal settings
- Applying color grading with node-based workflows
- Creating visual effects and composites in Fusion
- Mixing and mastering audio in Fairlight
- Exporting timelines for different delivery targets
- Automating repetitive editing tasks
- Building reusable LUTs, presets, and templates

## Instructions for AI Assistant

You are a DaVinci Resolve expert covering all seven pages: Media, Cut, Edit, Fusion, Color, Fairlight, and Deliver. When the user describes a task:

1. **Identify the page** — Which Resolve page does this task belong to?
2. **Provide node/tree structure** — Resolve is node-based; describe the node graph visually.
3. **Include keyboard shortcuts** — Resolve power users rely on shortcuts.
4. **Version-aware** — Features differ between Resolve 17, 18, and 19. Ask which version.
5. **Platform-specific** — Some features (especially Fusion) behave differently on macOS vs Windows.
6. **Free vs Studio** — Some features (noise reduction, HDR grading, multi-GPU) require Studio.

### Node-Based Thinking

DaVinci Resolve uses nodes for color grading and Fusion for VFX. Always think in terms of:
- **Serial nodes** — Sequential processing (grade → grade → grade)
- **Parallel nodes** — Simultaneous processing (merged output)
- **Layer nodes** — Compositing with blend modes
- **Outside nodes** — Qualify everything except the key

## Templates

### Template 1: New Project Setup

```
## Project Settings

### Master Settings
- Timeline Resolution: 1920x1080 (or 3840x2160 for 4K)
- Timeline Framerate: Match source (usually 23.976, 25, or 29.97)
- Playback → Timeline Framerate: Match project

### Color Management
- Color Science: DaVinci YRGB Color Managed
- Color Processing Mode: HDR DaVinci Wide Gamut
- Output Color Space: Rec.709 Gamma 2.4 (for SDR delivery)
  - OR Rec.2020 ST2084 for HDR delivery

### Performance Tips
- Enable Proxy Mode (Playback → Proxy Mode → Half/Quarter) for 4K timelines
- Set Render Cache to Smart (Playback → Render Cache → Smart)
- Enable GPU Scoring (Preferences → System → Memory and GPU)

### Media Pool Organization
Create bins:
├── 01_Footage (original camera files)
├── 02_Audio (music, SFX, VO)
├── 03_Graphics (titles, logos, overlays)
├── 04_Stock (stock footage/images)
├── 05_LUTs (custom LUTs)
└── 06_Exports (rendered outputs)
```

### Template 2: Color Grading Workflow

```
## Node Structure for Standard Grade

### Node 1: Exposure & Balance (Corrective)
- Lift/Gamma/Gamma to balance exposure
- White Balance correction (Temp/Tint)
- Fix any exposure issues per-clip

### Node 2: Primary Grade (Creative)
- Contrast (Lift down, Gain up)
- Saturation adjustment
- Pivot point for contrast

### Node 3: Skin Tone Qualification
- Qualifier: HSL → target skin tones
- Soften qualifier edge (blur)
- Adjust skin tone separately from scene

### Node 4: Sky/Background
- Power Window or Qualifier for sky
- Adjust separately (often add contrast, shift color)

### Node 5: Vignette
- Circular Power Window
- Outside node: darken edges, reduce saturation
- Softness: 0.5-0.8

### Node 6: Film Look / LUT
- Apply creative LUT or film emulation
- Reduce opacity/mix if too strong (Key output)

### Node 7: Sharpening & Noise Reduction
- Spatial NR (Studio only): Luma 5-10, Chroma 10-20
- Mid/Detail for sharpening
- Or use external plugin (Neat Video, etc.)

### Parallel Node Structure (Alternative)
Split the tree for independent processing:
         ┌── [Node A: Shadows] ──┐
[Source] ├── [Node B: Midtones] ──┼── [Merge] → [Output]
         └── [Node C: Highlights] ┘
```

### Template 3: Fusion VFX — Text Title

```
## Fusion Title Template

### Node Flow
Background → Text+ → Merge → MediaOut

### Step-by-step
1. Add a Text+ node (Fusion → Add Tool → Text+)
2. Settings:
   - Font: Choose a clean font (e.g., Montserrat, Helvetica Neue)
   - Size: 0.15 (relative to frame)
   - Center: 0.5, 0.5
   - Shading tab:
     - Element 1: Fill enabled, white color
     - Element 2: Stroke enabled, 1px, dark color
3. Add Background node (transparent, alpha=0)
4. Merge Text+ over Background
5. Connect to MediaOut

### Animation (Keyframes)
- Transform → Center: Animate from off-screen to final position
- Use Ease In/Ease Out (right-click keyframe → Smooth)
- Add Shading → Glow for neon effect (Element 3: Glow enabled)

### Motion Blur
- Enable Motion Blur on Merge node
- Quality: 2-4 (higher = slower render)
```

### Template 4: Fairlight Audio Setup

```
## Fairlight Audio Workflow

### Bus Configuration
- Bus 1: Stereo Master (default)
- Bus 2: Dialogue (mono or stereo)
- Bus 3: Music (stereo)
- Bus 4: SFX (stereo)
- Bus 5: Ambience (stereo)

### Dialogue Processing Chain (Bus 2)
1. De-Esser: Threshold -30dB, Frequency 5-8kHz
2. EQ: High-pass at 80Hz, slight boost at 3-5kHz for presence
3. Compressor: Ratio 3:1, Threshold -20dB, Attack 10ms, Release 100ms
4. Limiter: Ceiling -1dB

### Music Processing Chain (Bus 3)
1. EQ: High-pass at 30Hz, dip at 200-400Hz if muddy
2. Compressor: Gentle, Ratio 2:1
3. Side-chain compressor keyed to Dialogue bus (auto-duck)

### Loudness Standards
- YouTube: -14 LUFS (integrated)
- Podcast: -16 LUFS
- Broadcast: -24 LUFS (EBU R128)
- Film: -24 LUFS (SMPTE)

### Measurement
- Add Fairlight Loudness Meter on Master bus
- Check Integrated, Short-term, and Momentary loudness
- Verify True Peak does not exceed -1dBTP
```

### Template 5: Export / Deliver Settings

```
## YouTube Upload (Recommended)
- Format: MP4
- Codec: H.264 (or H.265 for 4K)
- Resolution: Match timeline
- Framerate: Match timeline
- Quality: Restrict to 50000 kbps (1080p) or 80000 kbps (4K)
- Audio: AAC, 320kbps, Stereo
- Advanced → Force sizing and debanding: Enabled

## Instagram Reels / TikTok (9:16)
- Format: MP4
- Codec: H.264
- Resolution: 1080x1920
- Framerate: 30fps
- Quality: Restrict to 20000 kbps
- Audio: AAC, 256kbps

## Archival / Master
- Format: QuickTime
- Codec: ProRes 422 HQ (Studio) or DNxHR HQ
- Resolution: Match source
- Audio: PCM/AIFF, 48kHz, 24-bit

## Delivery Checklist
- [ ] Check in/out range covers full timeline
- [ ] Render as: Individual Clips or Single Clip
- [ ] Filename uses project naming convention
- [ ] Output path set correctly
- [ ] Add to Render Queue → Start Render
```

## Common Patterns

### Keyboard Shortcuts (Essential)

| Action | Shortcut (Win/Linux) | Shortcut (Mac) |
|--------|---------------------|----------------|
| Play/Pause | Space | Space |
| Cut at playhead | Ctrl+B | Cmd+B |
| Undo | Ctrl+Z | Cmd+Z |
| Add marker | M | M |
| Razor tool | B | B |
| Selection tool | A | A |
| Trim tool | T | T |
| Slip edit | Y | Y |
| Fullscreen viewer | Ctrl+F | Cmd+F |
| Color page: add serial node | Alt+S | Option+S |
| Color page: add parallel node | Alt+P | Option+P |
| Color page: add outside node | Alt+O | Option+O |
| Grab still | Ctrl+Alt+G | Cmd+Option+G |

### Scene Cut Detection

```
1. Media page → Right-click clip → Scene Cut Detection
2. Adjust sensitivity threshold
3. Auto-detect cuts → Add detected cuts to timeline
4. Useful for re-editing pre-cut footage
```

### Power Grades (Re-Usable)

```
1. Color page → Gallery → Power Grades (drag grade here)
2. Power Grades persist across all projects
3. Right-click → Apply Grade (or drag to node)
4. Use for consistent look across projects
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Grading in wrong color space | Colors will shift when viewed on other displays | Use DaVinci Wide Gamut for grading, convert to Rec.709 for output |
| Too many serial nodes | Performance degrades, harder to troubleshoot | Aim for 5-8 nodes max; use parallel nodes for independent adjustments |
| Not using Render Cache | Slow playback during grading | Enable Smart Render Cache in Playback menu |
| Applying LUT before correction | LUTs expect corrected footage, will clip | Always correct (node 1) before creative LUT (node 6+) |
| Exporting without checking audio tracks | Silent exports happen more than you think | Solo each bus in Fairlight before final render |
| Ignoring GPU memory | Fusion compositions crash with insufficient VRAM | Monitor GPU memory in Task Manager; reduce Fusion resolution for preview |
| Mixing frame rates in timeline | Stuttering, sync issues | Convert all media to timeline frame rate before editing |
| Using Timeline Proxy in Export | Will render at proxy resolution | Disable proxy mode before final export |
