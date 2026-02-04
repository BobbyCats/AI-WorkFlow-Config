# 项目上下文 (Project Context)

> 本文件供所有 AI 模型阅读，用于快速理解项目背景。
> 在新对话开始时，可以让 AI 先阅读此文件建立上下文。

## 项目概述

**项目名称**: Aitips  
**项目定位**: AI 使用技巧知识库  
**主要内容**: 收集和整理各种 AI 工具的高效使用方法和最佳实践

## 目录结构

```
Aitips/
├── .ai/                    # AI 通用配置
│   ├── CONTEXT.md          # 项目上下文（本文件）
│   ├── RULES.md            # 规则与约束
│   └── prompts/            # 常用提示词模板
├── CLAUDE.md               # Claude 专用配置
├── .cursorrules            # Cursor 编辑器规则
├── .aiignore               # AI 忽略文件
└── docs/                   # 文档目录
```

## 技术栈

- **文档格式**: Markdown
- **主要语言**: 中文（部分英文原文）
- **编辑工具**: VS Code / Cursor / 任意 Markdown 编辑器

## 内容约定

1. 所有文档使用 Markdown 格式
2. 文件命名使用 kebab-case（如 `claude-code-tips.md`）
3. 中文文档标题后可附加 `(中文版)` 标识翻译内容
4. 代码示例使用围栏代码块并标注语言

## 如何使用本知识库

1. **查阅技巧**: 直接阅读对应 AI 工具的 tips 文档
2. **贡献内容**: 按现有格式添加新的技巧文档
3. **AI 协作**: 让 AI 先阅读 `.ai/CONTEXT.md` 建立上下文
