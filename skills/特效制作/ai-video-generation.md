# AI Video Generation

> Generate, style, and enhance videos using AI tools — Runway Gen-3, Pika Labs, OpenAI Sora, Stable Video Diffusion, and more.

## When to Use

- Generating video clips from text prompts
- Creating video from a reference image (image-to-video)
- Applying AI style transfer to existing footage
- Upscaling low-resolution video with AI
- Generating B-roll footage for video projects
- Creating concept videos and mood boards
- Extending or in-painting existing video clips

## Instructions for AI Assistant

You are an AI video generation expert. When the user describes a video they want to create:

1. **Choose the right tool** — Each tool has different strengths (see tool comparison below).
2. **Craft the prompt** — AI video quality depends heavily on prompt engineering.
3. **Set expectations** — Current AI video is best for 2-10 second clips; longer videos need stitching.
4. **Iterative workflow** — Generate → Evaluate → Refine prompt → Regenerate.
5. **Post-processing** — AI output often needs upscaling, stabilization, and color correction.
6. **Ethical considerations** — Disclose AI-generated content; respect copyright and likeness rights.

### Tool Comparison (2025-2026)

```
Tool              │ Best For                  │ Max Duration │ Resolution
──────────────────┼───────────────────────────┼──────────────┼───────────
Runway Gen-3 Alpha│ Cinematic, photorealistic  │ 10s          │ Up to 4K
Pika Labs         │ Stylized, animated         │ 4s           │ 1080p
OpenAI Sora       │ Complex scenes, narrative  │ 60s          │ 1080p
Kling             │ Realistic motion           │ 3min         │ 1080p
Luma Dream Machine│ Quick prototyping          │ 5s           │ 720p
Stable Video Diff  │ Open-source, self-hosted   │ 4s           │ 576x1024
Minimax/Hailuo    │ Smooth motion              │ 6s           │ 768p
CogVideoX         │ Open-source                │ 6s           │ 720p
Vidu              │ Chinese-style, narrative   │ 8s           │ 1080p
```

## Templates

### Template 1: Prompt Engineering Framework

```
## The STRUCTURE Method for Video Prompts

S — Subject: Who or what is the main focus?
T — Type: What kind of shot? (wide, close-up, aerial, tracking)
R — Reality: What's the visual style? (cinematic, anime, 3D render, documentary)
U — Universe: What's the setting/environment?
C — Color: What's the color palette or mood?
T — Timing: What's the camera movement? (static, pan, zoom, dolly)
U — Ultra detail: Any specific lighting, weather, or texture details?
R — Resolution: Specify quality (4K, film grain, shallow DOF)
E — Emotion: What feeling should the viewer experience?

### Example Application
Prompt: "A lone astronaut [S] in a wide establishing shot [T], 
photorealistic cinematic style [R], standing on the edge of a Martian 
crater at sunset [U], warm orange and deep blue tones [C], slow dolly 
forward with subtle parallax [T], dust particles catching the golden 
light, helmet visor reflecting the landscape [U], shot on ARRI Alexa 
with anamorphic lens flare [R], evoking solitude and wonder [E]"
```

### Template 2: Platform-Specific Prompt Templates

```
## Runway Gen-3 Alpha

### Photorealistic
"Cinematic shot, [subject] [action] in [location], 
golden hour lighting, shallow depth of field, 
shot on 35mm film, anamorphic lens flare, 
professional color grading, 4K resolution"

### Product Video
"Product photography, [product name] slowly rotating on 
a reflective black surface, studio lighting with soft 
highlights, clean minimal background, commercial quality, 
smooth 360-degree turntable rotation"

### Nature / Landscape
"Timelapse of [natural phenomenon] over [location], 
hyper-realistic, shot with RED V-RAPTOR, 
dramatic sky colors, smooth camera movement, 
National Geographic quality"

## Pika Labs

### Animated Style
"[Subject] in [action], anime style, vibrant colors, 
Studio Ghibli inspired, soft cel-shading, 
gentle camera pan, magical atmosphere"

### 3D Render
"Low-poly 3D render of [subject], 
isometric perspective, pastel color palette, 
smooth animation, ambient occlusion, 
Blender Cycles render quality"

## OpenAI Sora

### Narrative Scene
"A [character description] walks through [detailed environment]. 
The camera follows in a tracking shot as [action unfolds]. 
The lighting shifts from [state A] to [state B], 
casting [shadow/light description]. 
The mood is [emotional quality]. 
Photorealistic, cinematic 24fps with film grain."

### Comparison Shot
"Side-by-side comparison: [Scene A on the left], [Scene B on the right]. 
Both shots have identical camera angles and lighting. 
Slow reveal from left to right. Clean split-screen composition."
```

### Template 3: Image-to-Video Prompts

```
## Strategy: Describe What Changes, Not What's There

The AI already sees the image. Focus on:
1. Camera movement (dolly, pan, tilt, zoom)
2. Subject animation (what moves and how)
3. Environmental changes (wind, light, particles)
4. Temporal progression (what happens over time)

### Templates

#### Portrait Animation
"Subtle camera push-in, the person blinks naturally, 
hair moves gently in a soft breeze, 
background lights softly pulse, 
natural micro-expressions, cinematic depth of field"

#### Landscape Animation
"Slow aerial dolly forward over the landscape, 
clouds drift across the sky, 
water ripples reflect the changing light, 
trees sway gently, birds fly in the distance, 
golden hour progression"

#### Product Animation
"Slow orbit around the product, 
surface reflections shift with the light, 
steam/particles rise from the surface, 
background gradually de-focuses, 
commercial lighting setup"

#### Architecture
"Timelapse from day to night, 
shadows sweep across the building, 
lights turn on floor by floor, 
cars and pedestrians move below, 
sky transitions from blue to sunset to stars"
```

### Template 4: AI Upscaling & Enhancement

```
## Video Upscaling Pipeline

### Tools
- Topaz Video AI: Best quality, paid
- Real-ESRGAN: Free, open-source, good for anime
- DaVinci Resolve Super Scale: Studio feature
- CapCut: Free, built-in upscaling

### FFmpeg + Real-ESRGAN Workflow
# 1. Extract frames
mkdir frames
ffmpeg -i input.mp4 frames/%06d.png

# 2. Upscale with Real-ESRGAN
realesrgan-ncnn-vulkan -i frames -o upscaled -n realesrgan-x4plus -s 4

# 3. Reassemble video
ffmpeg -framerate 30 -i upscaled/%06d.png -i input.mp4 \
  -map 0:v -map 1:a -c:v libx264 -crf 18 -c:a copy output_4k.mp4

### Topaz Video AI Settings
- Model: Proteus (general) or Artemis (low quality)
- Scale: 2x (for 720p→1440p) or 4x (for 1080p→4K)
- Anti-Alias/Deblur: Adjust per-clip
- Noise/Blur: Auto-detect or manual 0-10
- Grain: Add 1-3 for natural look after upscaling
```

### Template 5: Style Transfer Pipeline

```
## AI Style Transfer Workflow

### Method 1: Re-generation with Style Prompt
1. Take a screenshot or frame of your video
2. Use as reference image in Runway/Pika
3. Add style description to prompt:
   "In the style of [artist/movement], [color palette], 
   [texture], [medium description]"
4. Generate matching clips
5. Stitch in video editor

### Method 2: Temporal Style Transfer (Consistent)
For frame-by-frame consistency:
1. Extract key frames (1 per second)
2. Apply style transfer to each frame
3. Use optical flow to interpolate between styled frames
4. Run RIFE or FILM for smooth intermediate frames

### Style Prompt Modifiers
- "Oil painting style, visible brushstrokes, impasto texture"
- "Watercolor, soft edges, bleeding colors, paper texture"
- "Anime style, bold outlines, cel-shaded, vibrant palette"
- "Film noir, high contrast black and white, dramatic shadows"
- "Cyberpunk, neon lights, rain-soaked streets, holographic"
- "Studio Ghibli, soft pastels, detailed backgrounds, whimsical"
```

## Common Patterns

### Consistent Character Across Clips

```
## Character Consistency Strategy

### Step 1: Reference Sheet
Generate a character reference with multiple angles:
"[Character description] character reference sheet, 
front view, side view, back view, 3/4 view, 
white background, consistent design, 
animation model sheet"

### Step 2: Use Reference in Every Prompt
Always include character description verbatim:
"The same character with [exact features] is now [action] in [setting]"

### Step 3: Seed Locking (if supported)
Use the same seed number across generations for consistency.

### Step 4: Post-Processing
Color-match all clips in DaVinci Resolve or Premiere.
```

### Stitching Short Clips into Longer Videos

```
## Clip Stitching Strategy

### Planning
- Storyboard the full video first
- Identify 3-8 second segments needed
- Plan transition points between AI clips

### Generation
- Generate with similar lighting and color
- Use consistent prompt structure
- Keep the last frame of each clip as reference for the next

### Assembly
1. Import all clips into video editor
2. Trim to best portions (usually the middle)
3. Add transitions: cross-dissolve (0.5s), cut on motion
4. Add continuous music and sound design
5. Color-match all clips (match to a reference clip)
6. Add film grain overlay to unify all clips
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Overly complex prompts | AI gets confused, random results | Keep prompts focused, one main action per clip |
| Ignoring temporal consistency | Character/object changes between clips | Use reference images and consistent descriptions |
| Not disclosing AI generation | Ethical and platform policy issues | Always label AI-generated content |
| Expecting perfect lip sync | Current AI can't reliably do speech | Use separate voice generation + avatar animation |
| Generating long videos in one go | Quality degrades significantly | Generate 3-8 second clips and stitch |
| Skipping post-processing | AI output has artifacts, noise, color issues | Always upscale, stabilize, and color-grade AI output |
| Using copyrighted styles without care | Legal and ethical risk | Use general style descriptions, not specific artist names |
| Assuming all tools are equal | Each has different strengths | Match tool to use case (see comparison table) |
