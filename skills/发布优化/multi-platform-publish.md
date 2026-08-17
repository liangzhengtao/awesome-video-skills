# Multi-Platform Publishing

> Publish videos to YouTube, TikTok, Bilibili, Instagram, and more — with platform-specific specs, batch resizing, and automated workflows.

## When to Use

- Publishing the same video to multiple platforms
- Resizing and reformatting for platform-specific requirements
- Adapting content for vertical (9:16), square (1:1), and landscape (16:9)
- Batch exporting multiple versions of a video
- Scheduling uploads across platforms
- Optimizing metadata for each platform's algorithm

## Instructions for AI Assistant

You are a multi-platform video publishing expert. When the user wants to publish across platforms:

1. **Specs first** — Every platform has different resolution, duration, codec, and aspect ratio requirements.
2. **Content adaptation** — Don't just resize; adapt the content (captions, hooks, CTAs) per platform.
3. **One source, many outputs** — Edit once in the highest quality, then batch-export variants.
4. **Platform-specific hooks** — The first 3 seconds must be optimized differently per platform.
5. **Metadata matters** — Titles, descriptions, hashtags, and thumbnails all differ by platform.
6. **Analytics per platform** — Track performance separately; audiences behave differently.

### Platform Priority Matrix

```
Platform    │ Format  │ Duration  │ Priority Signals
────────────┼─────────┼───────────┼──────────────────────────
YouTube     │ 16:9    │ 8-15 min  │ Watch time, CTR, retention
TikTok      │ 9:16    │ 15-60s    │ Completion rate, shares, rewatch
Instagram   │ 9:16    │ 15-90s    │ Shares, saves, comments
Bilibili    │ 16:9    │ 5-20 min  │ Like/coin ratio, retention, danmaku
Twitter/X   │ 16:9    │ <2:20     │ Views, retweets, replies
LinkedIn    │ 16:9/1:1│ <10 min   │ Engagement, comments, shares
Facebook    │ 16:9    │ 3-5 min   │ Shares, watch time, reactions
Douyin      │ 9:16    │ 15-60s    │ Completion rate, shares, interaction
```

## Templates

### Template 1: Platform Specifications Table

```
## Video Specs by Platform (2025-2026)

### YouTube
- Resolution: Up to 3840x2160 (4K)
- Aspect Ratio: 16:9
- Max Duration: 12 hours (verified) / 15 min (unverified)
- Max Size: 256GB
- Codec: H.264, H.265, AV1
- Frame Rate: 24/25/30/60fps
- Audio: AAC, 128-384kbps
- Shorts: 1080x1920, up to 60s

### TikTok
- Resolution: 1080x1920
- Aspect Ratio: 9:16
- Max Duration: 10 min (upload) / 60s (record)
- Max Size: 287.6MB (web) / 72MB (app)
- Codec: H.264
- Frame Rate: 30fps recommended
- Audio: AAC

### Instagram
- Reels: 1080x1920, 9:16, up to 90s
- Feed Video: 1080x1080 (1:1) or 1080x1350 (4:5), up to 60 min
- Stories: 1080x1920, 9:16, up to 60s
- Max Size: 4GB (Reels/Feed), 250MB (Stories)
- Codec: H.264

### Bilibili
- Resolution: Up to 3840x2160 (4K)
- Aspect Ratio: 16:9
- Max Duration: 120 min (Level 4+) / 60 min (default)
- Max Size: 8GB (Level 4+) / 4GB (default)
- Codec: H.264, H.265, AV1
- Frame Rate: 60fps supported
- Audio: AAC

### Twitter/X
- Resolution: 1920x1200 (max recommended)
- Aspect Ratio: 16:9 or 1:1
- Max Duration: 2:20 (standard) / 60 min (Premium)
- Max Size: 512MB (standard) / 8GB (Premium)
- Codec: H.264
- Frame Rate: 30/60fps

### LinkedIn
- Resolution: 1920x1080 or 1080x1080
- Aspect Ratio: 16:9, 1:1, 4:5, 9:16
- Max Duration: 10 min
- Max Size: 5GB
- Codec: H.264

### Douyin (抖音)
- Resolution: 1080x1920
- Aspect Ratio: 9:16
- Max Duration: 15 min
- Max Size: 4GB
- Codec: H.264

### WeChat Video Channel (微信视频号)
- Resolution: 1080x1920 or 1080x1260
- Aspect Ratio: 9:16 or 6:7
- Max Duration: 30 min
- Max Size: 2GB
```

### Template 2: FFmpeg Batch Export Script

```bash
#!/bin/bash
# multi_export.sh — Export one source video for all platforms
# Usage: ./multi_export.sh input.mp4

INPUT="$1"
BASENAME="${INPUT%.*}"
mkdir -p exports

echo "Exporting for all platforms from: $INPUT"

# === YouTube 1080p ===
echo "[1/8] YouTube 1080p..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 20 -preset medium \
  -vf "scale=-2:1080" \
  -c:a aac -b:a 256k \
  -movflags +faststart \
  "exports/${BASENAME}_youtube_1080p.mp4"

# === YouTube Shorts / TikTok / Reels (9:16, center crop) ===
echo "[2/8] TikTok/Reels 9:16..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 22 -preset medium \
  -vf "crop=ih*9/16:ih,scale=1080:1920" \
  -c:a aac -b:a 256k \
  -t 60 \
  "exports/${BASENAME}_tiktok_reels.mp4"

# === Instagram Feed (1:1 square) ===
echo "[3/8] Instagram 1:1..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 22 -preset medium \
  -vf "crop=min(iw\,ih):min(iw\,ih),scale=1080:1080" \
  -c:a aac -b:a 256k \
  "exports/${BASENAME}_instagram_1x1.mp4"

# === Instagram Feed (4:5 portrait) ===
echo "[4/8] Instagram 4:5..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 22 -preset medium \
  -vf "crop=ih*4/5:ih,scale=1080:1350" \
  -c:a aac -b:a 256k \
  "exports/${BASENAME}_instagram_4x5.mp4"

# === Bilibili 1080p ===
echo "[5/8] Bilibili 1080p..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 20 -preset medium \
  -vf "scale=-2:1080" \
  -c:a aac -b:a 320k \
  -movflags +faststart \
  "exports/${BASENAME}_bilibili_1080p.mp4"

# === Twitter/X ===
echo "[6/8] Twitter/X..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 23 -preset medium \
  -vf "scale=-2:720" \
  -c:a aac -b:a 128k \
  -movflags +faststart \
  -t 140 \
  "exports/${BASENAME}_twitter.mp4"

# === LinkedIn ===
echo "[7/8] LinkedIn..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 22 -preset medium \
  -vf "scale=-2:1080" \
  -c:a aac -b:a 192k \
  -movflags +faststart \
  -t 600 \
  "exports/${BASENAME}_linkedin.mp4"

# === Douyin (9:16) ===
echo "[8/8] Douyin 9:16..."
ffmpeg -y -i "$INPUT" \
  -c:v libx264 -crf 22 -preset medium \
  -vf "crop=ih*9/16:ih,scale=1080:1920" \
  -c:a aac -b:a 256k \
  "exports/${BASENAME}_douyin.mp4"

echo ""
echo "✅ All exports complete! Files in: exports/"
ls -lh exports/
```

### Template 3: Metadata Adaptation Matrix

```
## Metadata by Platform

### Title Adaptation
Platform   │ Style                    │ Max Length │ Example
───────────┼──────────────────────────┼────────────┼──────────────────
YouTube    │ SEO-optimized, keyword   │ 100 chars  │ "FFmpeg Tutorial: 10 Commands..."
TikTok     │ Hook + short, punchy     │ 150 chars  │ "Stop using this wrong FFmpeg command 🤯"
Instagram  │ Engaging, with emoji OK  │ 2200 chars │ "The FFmpeg trick nobody talks about 👀"
Bilibili   │ Chinese, descriptive     │ 80 chars   │ "FFmpeg从入门到精通：10个必备命令"
Twitter/X  │ Short, conversational    │ 280 chars  │ "Every video editor needs these FFmpeg commands"

### Description Adaptation
Platform   │ Length   │ Hashtags    │ Links        │ Timestamps
───────────┼──────────┼─────────────┼──────────────┼──────────
YouTube    │ 500+ words│ 3-5 above  │ Full links OK│ Yes (chapters)
TikTok     │ Short     │ 3-5        │ Bio link only│ No
Instagram  │ 100-300   │ 20-30      │ Bio link only│ No
Bilibili   │ 200+ words│ 2-3 tags   │ In bio only  │ Yes (timeline)
Twitter/X  │ 1-2 lines │ 1-3        │ Inline OK    │ No

### Hashtag Strategy
Platform   │ Hashtag Approach
───────────┼─────────────────────────────────────
YouTube    │ 3-5 in description, 0-3 in title
TikTok     │ 3-5 trending + niche, in caption
Instagram  │ Mix of big (1M+), medium (100K-1M), small (<100K)
Bilibili   │ 2-3 tags, use trending topic tags
Douyin     │ 3-5, include 1-2 trending challenges
```

### Template 4: Content Adaptation Strategy

```
## Adapting Content for Each Platform

### Long-Form → Short-Form (YouTube → TikTok/Reels)

1. Extract the best 30-60 seconds (hook + payoff)
2. Re-frame for vertical (9:16)
3. Add large burned-in subtitles (auto-cap style)
4. Speed up slightly (1.1x) for TikTok energy
5. Add a strong hook in first 1-2 seconds
6. End with a question or cliffhanger (drives comments)

### Short-Form → Long-Form (TikTok → YouTube)

1. Combine 5-10 related short-form clips
2. Add introduction (30s) and transitions
3. Add context/explanation between clips
4. Create a narrative arc
5. Add end screen with subscribe CTA

### Platform-Specific Hooks

#### YouTube (First 30 seconds)
- "In this video, you'll learn..."
- Start with the result/transformation
- Quick preview montage of what's coming

#### TikTok/Reels (First 2 seconds)
- Bold text overlay: "Stop scrolling!"
- Start mid-action (no build-up)
- Controversial or surprising statement

#### Bilibili (First 10 seconds)
- Greet the audience: "大家好，欢迎来到..."
- Preview what the video covers
- Jump to the most interesting part first

#### Douyin (First 3 seconds)
- Pattern interrupt (unexpected visual)
- Text overlay with key question
- Music-driven energy from frame 1
```

### Template 5: Upload Automation

```python
#!/usr/bin/env python3
"""
Batch Upload Helper
Helps organize exports and metadata for multi-platform publishing.
"""

import json
import os
from pathlib import Path

PLATFORMS = {
    "youtube": {
        "export_suffix": "_youtube_1080p.mp4",
        "title_max": 100,
        "desc_max": 5000,
        "hashtag_max": 15,
        "orientation": "landscape",
    },
    "tiktok": {
        "export_suffix": "_tiktok_reels.mp4",
        "title_max": 150,
        "desc_max": 2200,
        "hashtag_max": 5,
        "orientation": "portrait",
    },
    "instagram": {
        "export_suffix": "_instagram_4x5.mp4",
        "title_max": 2200,
        "desc_max": 2200,
        "hashtag_max": 30,
        "orientation": "portrait",
    },
    "bilibili": {
        "export_suffix": "_bilibili_1080p.mp4",
        "title_max": 80,
        "desc_max": 2000,
        "hashtag_max": 3,
        "orientation": "landscape",
    },
    "douyin": {
        "export_suffix": "_douyin.mp4",
        "title_max": 55,
        "desc_max": 1000,
        "hashtag_max": 5,
        "orientation": "portrait",
    },
}

def generate_upload_checklist(project_name: str, export_dir: str = "exports"):
    """Generate a platform-specific upload checklist."""
    checklist = {"project": project_name, "platforms": {}}
    
    for platform, specs in PLATFORMS.items():
        export_file = os.path.join(export_dir, f"{project_name}{specs['export_suffix']}")
        exists = os.path.exists(export_file)
        
        checklist["platforms"][platform] = {
            "export_ready": exists,
            "export_path": export_file,
            "title": "",
            "description": "",
            "hashtags": [],
            "thumbnail_ready": False,
            "scheduled_time": "",
            "uploaded": False,
            "specs": specs,
        }
    
    return checklist

def save_checklist(checklist: dict, output_path: str = "upload_checklist.json"):
    with open(output_path, 'w', encoding='utf-8') as f:
        json.dump(checklist, f, ensure_ascii=False, indent=2)
    print(f"Checklist saved to {output_path}")

if __name__ == "__main__":
    checklist = generate_upload_checklist("my_video")
    save_checklist(checklist)
    
    # Print summary
    print("\n📦 Upload Status:")
    for platform, info in checklist["platforms"].items():
        status = "✅" if info["export_ready"] else "❌"
        print(f"  {status} {platform}: {info['export_path']}")
```

## Common Patterns

### Content Repurposing Pipeline

```
## One Video → 10+ Pieces of Content

Source: 15-minute YouTube tutorial

1. YouTube video (full, 16:9)
2. YouTube Short (best 60s, 9:16)
3. TikTok (re-cut for 9:16, faster pace)
4. Instagram Reel (9:16, add trendy music)
5. Instagram Feed post (key screenshot + caption)
6. Twitter/X thread (key points as text thread)
7. Bilibili video (Chinese metadata, same video)
8. Douyin (re-cut for 9:16, Chinese captions)
9. LinkedIn post (professional angle, link to video)
10. Blog post (transcript → article)
11. Podcast episode (audio-only version)
12. Email newsletter (summary + link)
```

### Scheduling Strategy

```
## Multi-Platform Schedule

### Day 0 (Publish Day)
- YouTube: Upload full video, scheduled for peak time
- Bilibili: Upload same day (different audience)
- Community posts on both platforms

### Day 1
- TikTok: First short-form clip
- Douyin: First short-form clip
- Twitter/X: Link + engaging hook

### Day 2-3
- Instagram Reel: Different angle or highlight
- LinkedIn: Professional angle + link

### Day 4-7
- TikTok: Second clip (different highlight)
- Instagram Story: Behind-the-scenes or Q&A
- Community: Respond to all comments

### Ongoing
- Repurpose best-performing clips every 2-4 weeks
- Update descriptions with new links
```

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| Uploading same file everywhere | Each platform has different optimal specs | Export platform-specific versions |
| Using YouTube link on TikTok/Instagram | Platforms deprioritize external links | Use platform-native content, mention links in bio |
| Same caption/hashtags everywhere | Looks automated, hurts engagement | Adapt tone and hashtags per platform |
| Not adding burned-in subtitles for short-form | 80% of social video is watched on mute | Always burn subtitles into TikTok/Reels/Shorts |
| Uploading horizontal video to vertical platforms | Black bars or awkward cropping | Re-frame for vertical with intentional composition |
| Ignoring platform-specific features | Missing algorithm boost from native features | Use polls (IG), duets (TikTok), danmaku (Bilibili) |
| Same thumbnail for all platforms | Each platform has different crop/size rules | Create platform-specific thumbnails |
| Posting at the same time everywhere | Different audiences peak at different times | Check per-platform analytics for optimal times |
