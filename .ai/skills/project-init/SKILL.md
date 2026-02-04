---
description: 新项目初始化 AI 开发环境
---

# 项目初始化技能 (Project Init Skill)

快速为新项目配置 AI 辅助开发环境。

## 触发时机

- 创建新项目时
- 为现有项目添加 AI 配置时
- 用户说"初始化 AI 环境"或类似指令

## 初始化步骤

### 1. 创建目录结构

```
项目根目录/
├── .ai/
│   ├── CONTEXT.md      # 项目上下文
│   ├── RULES.md        # 规则与约束
│   ├── skills/         # 技能目录
│   ├── prompts/        # 提示词模板
│   └── errors/         # 错误记录
├── CLAUDE.md           # Claude 专用配置
├── .cursorrules        # Cursor 编辑器规则
└── .aiignore           # AI 忽略文件
```

### 2. 填写项目信息

引导用户填写 `.ai/CONTEXT.md`：

```markdown
# 项目上下文

## 项目概述

**项目名称**: [填写]
**项目定位**: [填写]
**技术栈**: [填写]

## 目录结构

[描述主要目录]

## 核心约定

[列出项目特有的约定]
```

### 3. 配置 AI 工具

根据用户使用的 AI 工具，创建对应配置：

- Claude Code → CLAUDE.md
- Cursor → .cursorrules
- GitHub Copilot → .github/copilot-instructions.md

### 4. 设置忽略规则

根据技术栈更新 `.aiignore`。

## 模板来源

可以从 Aitips 项目复制模板：`d:\Aitips\.ai\`
