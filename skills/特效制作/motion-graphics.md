# Motion Graphics & Animation

> Create animated titles, transitions, lower thirds, and motion graphics using After Effects expressions, CSS animations, and Lottie.

## When to Use

- Creating animated title cards and intros
- Designing lower third graphics with dynamic data
- Building reusable transition effects
- Animating logos and branding elements
- Creating data-driven motion graphics
- Building Lottie animations for web and mobile
- CSS/SVG animations for web-based video players

## Instructions for AI Assistant

You are a motion graphics expert spanning After Effects, CSS/SVG, and Lottie. When the user describes an animation:

1. **Choose the right tool** — After Effects for complex compositions, CSS for web, Lottie for cross-platform.
2. **Think in keyframes and easing** — Good motion is about timing, not just movement.
3. **Provide expressions, not manual keyframes** — Expressions are reusable and adjustable.
4. **Design for reuse** — Build templates with editable parameters.
5. **Consider performance** — Complex expressions and effects can slow down playback.
6. **12 Principles of Animation** — Reference squash/stretch, anticipation, easing, follow-through.

### Tool Decision Tree

```
Need motion graphics for...
├── Video production → After Effects (export as video or Lottie)
├── Web / App → CSS animations or Lottie
├── Social media → After Effects or Canva-style tools
├── Data visualization → After Effects + expressions, or D3.js
├── Logo animation → After Effects (shape layers + expressions)
└── Interactive → Lottie (via LottieFiles) or CSS + JS
```

## Templates

### Template 1: After Effects — Expressions Library

```javascript
// === LOOPING EXPRESSIONS ===

// Loop Out (cycle)
// Apply to any animated property
loopOut("cycle", 0);

// Loop Out (ping-pong)
loopOut("pingpong", 0);

// Loop Out (offset — continues the trend)
loopOut("offset", 0);

// === EASING EXPRESSIONS ===

// Smooth interpolation (applied to any property)
// Replace keyframes with this on the property
amp = 0.05;
freq = 3.0;
decay = 5.0;
n = 0;
if (numKeys > 0) {
  n = nearestKey(time).index;
  if (key(n).time > time) { n--; }
}
if (n > 0) {
  t = time - key(n).time;
  startVal = key(n).value;
  endVal = value;
  if (n < numKeys) {
    endVal = key(n+1).value;
  }
  w = freq * Math.PI * 2;
  value + (endVal - startVal) * Math.sin(t * w) / Math.exp(decay * t);
} else {
  value;
}

// Elastic easing (overshoot)
// Apply to Scale or Position
t = time - key(1).time;
startVal = key(1).value;
endVal = key(2).value;
duration = key(2).time - key(1).time;
amplitude = 1.0;
period = 0.3;
s = period / (2 * Math.PI) * Math.asin(1 / amplitude);
t = t / duration;
if (t < 1) {
  t * t * ((amplitude + 1) * t - amplitude);
} else {
  t - 1;
}
startVal + (endVal - startVal) * (Math.pow(2, -10 * t) * Math.sin((t - s) * (2 * Math.PI) / period) + 1);

// === WIGGLE EXPRESSIONS ===

// Basic wiggle
wiggle(5, 50); // freq=5, amplitude=50

// Wiggle with control (put on a slider)
freq = effect("Frequency")("Slider");
amp = effect("Amplitude")("Slider");
wiggle(freq, amp);

// Wiggle only X position
w = wiggle(5, 50);
[w[0], value[1]]; // Keep original Y

// === TEXT ANIMATIONS ===

// Typewriter effect (Text Source expression)
str = "Your text here";
idx = Math.round(time * 10); // characters per second
str.substring(0, idx);

// Counting numbers (Text Source expression)
startNum = 0;
endNum = 100;
dur = 2; // seconds
Math.round(linear(time, 0, dur, startNum, endNum));

// Random character scramble (Text Source expression)
origText = "SECRET TEXT";
chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
result = "";
for (i = 0; i < origText.length; i++) {
  if (time > i * 0.1 + 1) {
    result += origText[i];
  } else if (time > i * 0.1) {
    result += chars[Math.floor(Math.random() * chars.length)];
  }
}
result;
```

### Template 2: After Effects — Lower Third

```
## Lower Third Structure

### Composition: Lower_Third_Main (1920x1080, 10sec)

#### Layer 1: Background Bar
- Shape Layer: Rectangle
- Size: 600x120
- Fill: #1A1A2E, Opacity 90%
- Position: Animate from left off-screen to X=400
- Roundness: 8px

#### Layer 2: Accent Line
- Shape Layer: Rectangle
- Size: 4x120
- Fill: Brand color (#E94560)
- Position: Left edge of background
- Animate scale Y from 0% to 100%

#### Layer 3: Name Text
- Text Layer: "JOHN DOE"
- Font: Montserrat Bold, 36pt, White
- Position: Animate with background bar
- Animator: Position Y from +100% to 0%, with opacity 0→100%

#### Layer 4: Title Text
- Text Layer: "Senior Editor"
- Font: Montserrat Regular, 24pt, #AAAAAA
- Same animation as name, delayed by 0.15 sec

### Animation Timing
- Frame 0: Nothing visible
- Frame 1-15: Background slides in
- Frame 5-20: Accent line scales in
- Frame 10-25: Name text animates in
- Frame 15-30: Title text animates in
- Frame 75-90: Everything reverses and exits
```

### Template 3: CSS Animations

```css
/* Fade in from bottom */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-up {
  animation: fadeInUp 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}

/* Typewriter effect */
@keyframes typewriter {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-caret {
  from, to { border-color: transparent; }
  50% { border-color: #E94560; }
}

.typewriter {
  overflow: hidden;
  border-right: 3px solid #E94560;
  white-space: nowrap;
  animation:
    typewriter 2s steps(30) forwards,
    blink-caret 0.75s step-end infinite;
}

/* Scale bounce */
@keyframes scaleBounce {
  0% { transform: scale(0); }
  60% { transform: scale(1.15); }
  80% { transform: scale(0.95); }
  100% { transform: scale(1); }
}

.scale-bounce {
  animation: scaleBounce 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards;
}

/* Slide in from left with stagger */
@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-100px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.stagger-item:nth-child(1) { animation-delay: 0.1s; }
.stagger-item:nth-child(2) { animation-delay: 0.2s; }
.stagger-item:nth-child(3) { animation-delay: 0.3s; }

/* Loading spinner */
@keyframes spin {
  to { transform: rotate(360deg); }
}

.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid rgba(255, 255, 255, 0.3);
  border-top-color: #E94560;
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}
```

### Template 4: Lottie Animation (JSON Export)

```
## Lottie Workflow

### From After Effects to Lottie
1. Create animation in After Effects using shape layers and text
2. Install Bodymovin plugin (Window → Extensions → Bodymovin)
3. Select composition → Configure export settings
4. Export as .json (Lottie format)

### Supported AE Features
✅ Shape layers (paths, fills, strokes, trims)
✅ Text (with some limitations)
✅ Transforms (position, scale, rotation, opacity)
✅ Masks (additive/subtractive)
✅ Alpha/luma mattes
✅ Pre-compositions
✅ Keyframes and easing

### NOT Supported
❌ Effects (blur, glow, drop shadow — use SVG filters instead)
❌ 3D layers
❌ Expressions (baked keyframes only)
❌ Gradient strokes
❌ Merge paths (partially)

### Lottie Player (Web)
```html
<script src="https://unpkg.com/@lottiefiles/lottie-player@latest/dist/lottie-player.js"></script>
<lottie-player
  src="animation.json"
  background="transparent"
  speed="1"
  style="width: 300px; height: 300px"
  loop
  autoplay>
</lottie-player>
```

### Optimization
- Use Lottie Optimizer: https://lottiefiles.com/optimization
- Reduce unnecessary keyframes
- Simplify complex paths
- Target under 100KB for web animations
```

## Common Patterns

### Transition Library

```
## Quick Transitions

### Slide
- Position keyframes: off-screen → on-screen (20 frames)
- Easing: Ease In Out (F9)

### Zoom
- Scale: 120% → 100% with motion blur
- Combined with slight position drift

### Wipe
- Use Linear Wipe effect
- Transition Completion: 0% → 100%
- Feather: 50-100px

### Glitch
- Duplicate layer
- Offset RGB channels (Channel Shift)
- Add displacement map with random seed
- Add scan lines
- Random opacity flickering

### Morph / Reshape
- Match source and target paths
- Use Reshape effect or path keyframing
- Ensure equal number of points on both paths
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Using 3D layers for Lottie | Lottie doesn't support 3D | Stick to 2D shape layers and pre-comp tricks |
| Overusing expressions | Comp slows down, hard to debug | Bake expressions to keyframes for final render |
| No easing on keyframes | Linear motion looks robotic | Always use Ease In/Out (F9) or custom bezier curves |
| Animating too many properties | Viewer can't focus on anything | Animate 2-3 properties max per element |
| Not using pre-compositions | Timeline becomes unmanageable | Group related layers into pre-comps |
| Ignoring motion blur | Animations look stiff | Enable motion blur (shutter angle 180°) |
| Wrong anchor point | Rotation and scaling look wrong | Move anchor point to center of intended rotation |
| Frame rate mismatch | Animation appears choppy in final output | Match comp frame rate to delivery frame rate |

---

## 中文版本

### 使用场景

- 创建动态标题卡和片头
- 设计带动态数据的下方三分之一字幕条
- 构建可复用的转场效果
- 动画化 Logo 和品牌元素
- 创建数据驱动的动态图形
- 为 Web 和移动端构建 Lottie 动画
- 为网页视频播放器制作 CSS/SVG 动画

### 核心步骤

1. **选择合适的工具** — 复杂合成用 After Effects，Web 用 CSS，跨平台用 Lottie
2. **关键帧与缓动** — 好的动画在于节奏，不只是运动
3. **优先用表达式** — 表达式可复用且易于调整，优于手动关键帧
4. **为复用而设计** — 构建带可编辑参数的模板
5. **关注性能** — 复杂表达式和效果会拖慢回放
6. **动画 12 原则** — 参考挤压拉伸、预备动作、缓动、跟随动作

### 模板说明

| 模板 | 用途 | 要点 |
|------|------|------|
| AE 表达式库 | 常用动画表达式 | 循环、缓动、弹性、抖动、打字机、数字计数、字符乱码 |
| AE 下方三分之一 | 人物介绍字幕条 | 背景条 + 强调线 + 姓名 + 标题，4 层动画时序 |
| CSS 动画 | Web 端动效 | 淡入上移、打字机、缩放弹跳、交错滑入、加载旋转 |
| Lottie 导出 | 跨平台矢量动画 | Bodymovin 插件导出，支持形状层/文本/变换，不支持 3D/特效 |

### 常见陷阱

| 陷阱 | 问题 | 解决方案 |
|------|------|----------|
| Lottie 使用 3D 图层 | Lottie 不支持 3D | 限制在 2D 形状层和预合成技巧 |
| 表达式用太多 | 合成变慢，难以调试 | 最终渲染前将表达式烘焙为关键帧 |
| 关键帧无缓动 | 线性运动看起来机械 | 始终使用 Ease In/Out (F9) 或自定义贝塞尔曲线 |
| 同时动画过多属性 | 观众无法聚焦 | 每个元素最多动画 2-3 个属性 |
| 不用预合成 | 时间线变得不可管理 | 将相关图层分组到预合成中 |
| 忽略运动模糊 | 动画看起来生硬 | 启用运动模糊（快门角度 180°） |
| 锚点位置错误 | 旋转和缩放看起来不对 | 将锚点移到预期旋转中心 |
