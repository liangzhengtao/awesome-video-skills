# Contributing to Awesome Video Skills

Thank you for your interest in contributing! This guide will help you add new video skills or improve existing ones.

**[English](#english)** | **[中文](#中文)**

---

## English

### How to Contribute

#### 1. Submit a New Skill

1. Fork this repository
2. Create a new branch: `git checkout -b add-skill/your-skill-name`
3. Add your skill file in the appropriate category under `skills/`
4. Update the README.md skills table
5. Submit a Pull Request

#### 2. Improve an Existing Skill

1. Fork this repository
2. Create a branch: `git checkout -b improve/ffmpeg-master`
3. Make your changes
4. Submit a Pull Request with a clear description of what you changed and why

#### 3. Report Issues

- Use the [Issue Template](.github/ISSUE_TEMPLATE/request_skill.md) to request new skills
- Search existing issues before creating a new one

### Skill File Template

Every skill file must follow this structure:

```markdown
# Skill Name

> One-line description of what this skill does.

## When to Use

- Bullet list of specific trigger scenarios

## Instructions for AI Assistant

Guidelines for how the AI should use this skill.

## Templates

### Template 1: Name
Code blocks with practical, copy-paste-ready examples.

### Template 2: Name
...

## Common Patterns

Reusable workflows and proven patterns.

## Pitfalls to Avoid

| Pitfall | Why It's Bad | Solution |
|---------|-------------|----------|
| ... | ... | ... |
```

### Requirements

- **Minimum 100 lines** per skill file
- **Must include**: When to Use, Instructions for AI Assistant, Templates, Common Patterns, Pitfalls to Avoid
- **Practical examples**: Every template must have working code or commands
- **Language**: Write in English; Chinese translations welcome as a bonus
- **No secrets**: Never include API keys, passwords, or credentials
- **Original content**: Don't copy copyrighted material verbatim

### Category Guidelines

| Category | Description | File Path |
|----------|-------------|-----------|
| 视频剪辑 | Video editing tools and workflows | `skills/视频剪辑/` |
| 特效制作 | Visual effects and motion graphics | `skills/特效制作/` |
| 字幕处理 | Subtitle generation and translation | `skills/字幕处理/` |
| 音频处理 | Audio processing and mixing | `skills/音频处理/` |
| 发布优化 | Publishing, SEO, and distribution | `skills/发布优化/` |

To propose a new category, open an issue first to discuss.

### Style Guide

- Use Markdown headers (`##`, `###`) for structure
- Use code blocks with language tags for all commands and scripts
- Use tables for structured comparisons
- Keep line length reasonable (no hard limit, but avoid 300+ character lines)
- Use emoji sparingly in headers for visual scanning

### Code of Conduct

Please read our [Code of Conduct](CODE_OF_CONDUCT.md). We expect all contributors to follow it.

---

## 中文

### 如何贡献

#### 1. 提交新技能

1. Fork 本仓库
2. 创建分支：`git checkout -b add-skill/你的技能名`
3. 在 `skills/` 下对应分类中添加技能文件
4. 更新 README.md 技能表格
5. 提交 Pull Request

#### 2. 改进现有技能

1. Fork 本仓库
2. 创建分支：`git checkout -b improve/ffmpeg-master`
3. 进行修改
4. 提交 Pull Request，说明改了什么以及为什么

#### 3. 报告问题

- 使用 [Issue 模板](.github/ISSUE_TEMPLATE/request_skill.md) 请求新技能
- 创建新 issue 前先搜索已有 issue

### 技能文件模板

每个技能文件必须遵循以下结构：

```markdown
# 技能名称

> 一句话描述此技能的功能。

## 使用场景

- 列出具体的触发场景

## AI 助手指令

指导 AI 如何使用此技能。

## 模板

### 模板 1：名称
实用的、可直接复制粘贴的代码示例。

### 模板 2：名称
...

## 常见模式

可复用的工作流和最佳实践。

## 常见陷阱

| 陷阱 | 为什么有问题 | 解决方案 |
|------|-------------|---------|
| ... | ... | ... |
```

### 要求

- 每个技能文件**最少 100 行**
- **必须包含**：使用场景、AI 助手指令、模板、常见模式、常见陷阱
- **实用示例**：每个模板必须有可运行的代码或命令
- **语言**：中文撰写，欢迎英文翻译
- **安全**：不要包含 API 密钥、密码或凭据

### 行为准则

请阅读我们的[行为准则](CODE_OF_CONDUCT.md)。我们期望所有贡献者遵守。
