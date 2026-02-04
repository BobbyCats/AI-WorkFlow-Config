# AI 协作工作流指南

本文档记录如何在 Aitips 项目中高效使用 AI 辅助开发。

## 快速开始

### 1. 建立上下文

新对话开始时，让 AI 先阅读项目上下文：

```
请先阅读 .ai/CONTEXT.md 和 .ai/RULES.md，了解项目背景。
```

### 2. 使用提示词模板

常用场景可直接复制 `.ai/prompts/` 中的模板：

| 场景          | 模板文件                  |
| ------------- | ------------------------- |
| 代码/翻译审查 | `.ai/prompts/review.md`   |
| 重构优化      | `.ai/prompts/refactor.md` |
| 问题调试      | `.ai/prompts/debug.md`    |

## 各 AI 工具配置

| 工具                    | 配置文件                          | 说明     |
| ----------------------- | --------------------------------- | -------- |
| Claude Code             | `CLAUDE.md`                       | 自动读取 |
| Cursor                  | `.cursorrules`                    | 自动读取 |
| GitHub Copilot          | `.github/copilot-instructions.md` | 自动读取 |
| ChatGPT / Gemini / Qwen | `.ai/CONTEXT.md` + `.ai/RULES.md` | 手动引用 |

## 最佳实践

### 复杂任务

1. **先计划**: 让 AI 先制定方案，审阅通过后再执行
2. **分步骤**: 大任务拆成小步骤，逐步验证
3. **记录学习**: 发现 AI 常犯的错误，更新 `CLAUDE.md` 或 `RULES.md`

### 翻译工作

1. 提供原文，要求对照翻译
2. 用 review 模板检查翻译质量
3. 翻译后添加来源说明

### 内容创作

1. 明确目标读者和用途
2. 要求 AI 给出大纲后再展开
3. 完成后用 review 模板自查

## 效率技巧

- **Claude Code**: 使用 `/compact` 压缩长对话
- **所有工具**: 用 `@` 引用文件比复制粘贴更精确
- **团队协作**: 将常用提示词添加到 `.ai/prompts/`
