[English](README.md) | [中文](README.zh.md) | [日本語](README.ja.md) | [Français](README.fr.md) | [Español](README.es.md)

<div align="center">

<img src=".banner.svg" width="100%" alt="banner">

</div>


# 🎬 Awesome Video Skills

> FFmpeg コマンドを毎回ググるのはもうやめましょう。スキルを一度書けば、AI がずっと動画を編集してくれます。

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Skills](https://img.shields.io/badge/skills-10-blueviolet)](#スキル)

</div>

---



## 問題

プロジェクトのたびに **何時間も** FFmpeg のフラグをググり、DaVinci Resolve のショートカットを探し、同じ字幕スクリプトを書き直しています。AI アシスタントはあなたのワークフロー、プリセット、好みを知りません。

## 解決策

動画編集の知識を **AI スキル** として一度だけ書きましょう。AI アシスタントがそのスキルを読み取り、毎回ぴったりのパイプライン、プリセット、スクリプトを生成してくれます。

<div align="center">

| ❌ スキルなし | ✅ スキルあり |
|:---:|:---:|
| 30 分かけて FFmpeg フラグをググる | 「YouTube 用に圧縮して」→ 完璧なコマンド |
| 5 プラットフォーム分を手動でリサイズ | 全プラットフォーム一括書き出し |
| 字幕スクリプトを毎回書き直す | 希望通りの Whisper パイプラインを AI が生成 |
| YouTube SEO を推測 | 構造化されたタイトル/説明/タグ最適化 |

</div>

---

## スキル

### 動画編集

| スキル | 説明 | ファイル |
|--------|------|---------|
| 🎥 FFmpeg Master | カット、結合、変換、圧縮 — FFmpeg パイプラインの完全自動化 | [`skills/视频剪辑/ffmpeg-master.md`](skills/视频剪辑/ffmpeg-master.md) |
| 🎨 DaVinci Resolve | カラーグレーディング、Fusion VFX、Fairlight オーディオ、デリバリー設定 | [`skills/视频剪辑/davinci-resolve.md`](skills/视频剪辑/davinci-resolve.md) |
| 🎬 Premiere Pro | シーケンス設定、エクスプリセット、Dynamic Link、Essential Graphics | [`skills/视频剪辑/premiere-pro.md`](skills/视频剪辑/premiere-pro.md) |

### 特效制作

| スキル | 説明 | ファイル |
|--------|------|---------|
| ✨ Motion Graphics | After Effects 式、CSS アニメーション、Lottie テンプレート | [`skills/特效制作/motion-graphics.md`](skills/特效制作/motion-graphics.md) |
| 🤖 AI 動画生成 | Runway、Pika、Sora のプロンプトエンジニアリングとポストプロセス | [`skills/特效制作/ai-video-generation.md`](skills/特效制作/ai-video-generation.md) |

### 字幕処理

| スキル | 説明 | ファイル |
|--------|------|---------|
| 📝 字幕生成 | Whisper 転写、SRT/ASS フォーマット、字幕焼き付け | [`skills/字幕处理/subtitle-generation.md`](skills/字幕处理/subtitle-generation.md) |
| 🌐 翻訳字幕 | 多言語字幕パイプライン、二重字幕、QA | [`skills/字幕处理/translation-subtitles.md`](skills/字幕处理/translation-subtitles.md) |

### オーディオ処理

| スキル | 説明 | ファイル |
|--------|------|---------|
| 🎵 オーディオミキシング | ノイズ除去、EQ、コンプレッション、正規化、BGM ミキシング | [`skills/音频处理/audio-mixing.md`](skills/音频处理/audio-mixing.md) |

### 公開最適化

| スキル | 説明 | ファイル |
|--------|------|---------|
| 📈 YouTube 最適化 | SEO タイトル、サムネイルデザイン、タグ、分析、アップロードスケジュール | [`skills/发布优化/youtube-optimization.md`](skills/发布优化/youtube-optimization.md) |
| 🌍 マルチプラットフォーム公開 | YouTube、TikTok、Bilibili、Instagram — スペック、一括書き出し、自動化 | [`skills/发布优化/multi-platform-publish.md`](skills/发布优化/multi-platform-publish.md) |

---

## クイックスタート

### Cursor

任意のスキルファイルをプロジェクトの `.cursorrules` または `.cursor/rules/` ディレクトリにコピーします：

```bash
cp skills/视频剪辑/ffmpeg-master.md .cursor/rules/ffmpeg.md
```

複数のスキルを参照する場合：

```bash
mkdir -p .cursor/rules
cp skills/**/*.md .cursor/rules/
```

### Claude Code

スキルを `CLAUDE.md` にプロジェクトコンテキストとして追加：

```markdown
## Video Skills
- @skills/视频剪辑/ffmpeg-master.md
- @skills/字幕处理/subtitle-generation.md
```

### Kimi Code

スキルファイルをプロジェクトルートまたは `.kimi/` ディレクトリにコピー：

```bash
mkdir -p .kimi/skills
cp skills/**/*.md .kimi/skills/
```

### スキルの使い方

インストール後は、AI アシスタントに自然な言葉で依頼するだけです：

```
"Compress this video to under 50MB for email"
"Generate Chinese subtitles for this interview"
"Create a TikTok version of my YouTube video"
"Optimize my YouTube title and description for SEO"
"Mix background music under this voiceover at -18dB"
```

---

## コントリビューション

新しい動画スキルを歓迎します！詳細は [CONTRIBUTING.md](CONTRIBUTING.md) をご覧ください。

コントリビューションの手順：
1. このリポジトリをフォーク
2. `skills/` の適切なカテゴリにスキルを追加
3. スキルテンプレートフォーマット（使用場面、手順、テンプレート、注意点）に従う
4. PR を送信

---

## 関連リンク

- [awesome-skills](https://github.com/liangzhengtao/awesome-skills) — 各分野の AI スキル精选コレクション
- [awesome-ai-rules](https://github.com/liangzhengtao/awesome-ai-rules) — AI コーディングアシスタントのルールと設定
- [vibe-check](https://github.com/liangzhengtao/vibe-check) — AI スキルの品質検証・テストツール
- [commit-ai](https://github.com/liangzhengtao/commit-ai) — AI 駆動の Git コミットメッセージ生成
- [awesome-mcp-servers](https://github.com/liangzhengtao/awesome-mcp-servers) — AI ツール向け Model Context Protocol サーバー

---

## ライセンス

[MIT](LICENSE) © [liangzhengtao](https://github.com/liangzhengtao)

---
