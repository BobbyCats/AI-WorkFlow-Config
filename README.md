# AI Tips - 通用 AI 辅助开发环境配置

一套适用于多种 AI 模型（Claude、GPT、Gemini、Qwen 等）的开发环境配置模板。

## 这是什么？

基于 [Claude Code Tips](https://code.claude.com) 官方最佳实践，整合了一套**通用的 AI 辅助开发环境配置**，让你在任何项目中都能高效使用 AI 工具。

### 核心特性

- **多 AI 兼容**: 适用于 Claude Code、Cursor、GitHub Copilot、ChatGPT、Gemini 等
- **按需加载**: 使用 Skills 机制，只加载需要的规则，节省 Token
- **错误记录**: 自动提醒记录开发中的错误经验，避免重复踩坑
- **开箱即用**: 复制到项目即可使用

## 快速开始

### 1. 克隆或下载

```bash
git clone https://github.com/你的用户名/aitips.git
```

### 2. 复制到你的项目

将以下文件复制到你的项目根目录：

```
.ai/           # AI 通用配置目录
CLAUDE.md      # Claude 专用配置
.cursorrules   # Cursor 编辑器配置
.aiignore      # AI 忽略文件
```

### 3. 修改项目信息

编辑 `.ai/CONTEXT.md`，填入你项目的具体信息：

- 项目名称和定位
- 技术栈
- 目录结构
- 核心约定

### 4. 开始使用

现在你的 AI 工具就能自动读取这些配置了！

## 目录结构

```
.
├── .ai/                              # AI 通用配置
│   ├── CONTEXT.md                    # 项目上下文
│   ├── RULES.md                      # 规则与约束
│   ├── skills/                       # 技能目录
│   │   ├── error-learning/           # 错误记录技能
│   │   ├── project-init/             # 项目初始化技能
│   │   └── translation/              # 翻译技能
│   ├── prompts/                      # 提示词模板
│   │   ├── review.md                 # 审查模板
│   │   ├── refactor.md               # 重构模板
│   │   └── debug.md                  # 调试模板
│   └── errors/                       # 错误记录存放
├── .github/
│   └── copilot-instructions.md       # GitHub Copilot 配置
├── docs/
│   ├── ai-workflow.md                # 工作流指南
│   └── command-reference.md          # 指令速查表
├── CLAUDE.md                         # Claude 专用配置
├── .cursorrules                      # Cursor 编辑器配置
├── .aiignore                         # AI 忽略文件
└── README.md                         # 本文档
```

## 各文件用途

| 文件/目录                         | 用途                 | 适用工具             |
| --------------------------------- | -------------------- | -------------------- |
| `.ai/CONTEXT.md`                  | 项目上下文           | 所有 AI              |
| `.ai/RULES.md`                    | 规则与约束           | 所有 AI              |
| `.ai/skills/`                     | 技能目录（按需加载） | Claude Code          |
| `.ai/prompts/`                    | 提示词模板           | 所有 AI              |
| `.ai/errors/`                     | 错误记录             | 所有 AI              |
| `CLAUDE.md`                       | Claude 专用配置      | Claude Code / Cursor |
| `.cursorrules`                    | Cursor 配置          | Cursor IDE           |
| `.github/copilot-instructions.md` | Copilot 配置         | GitHub Copilot       |
| `.aiignore`                       | 忽略文件             | 所有 AI              |

## 工具配置对照表

| AI 工具        | 自动读取                    | 手动引用                           |
| -------------- | --------------------------- | ---------------------------------- |
| Claude Code    | `CLAUDE.md` ✓               | -                                  |
| Cursor         | `.cursorrules` ✓            | -                                  |
| GitHub Copilot | `copilot-instructions.md` ✓ | -                                  |
| ChatGPT        | -                           | 复制 `.ai/CONTEXT.md` + `RULES.md` |
| Gemini         | -                           | 复制 `.ai/CONTEXT.md` + `RULES.md` |
| Qwen           | -                           | 复制 `.ai/CONTEXT.md` + `RULES.md` |

## 来源与致谢

本项目配置方案基于以下来源整理：

- **Claude Code Tips** - 由 Claude Code 创建者 Boris 分享的官方最佳实践
- **社区实践** - 来自开发者社区的高效使用技巧

详见 [Claude Code tips (中文版).md](<./Claude%20Code%20tips%20(中文版).md>)

## 贡献

欢迎提交 Issue 和 PR！

- 发现好用的技巧？请添加到文档
- 发现问题？请提 Issue
- 有改进建议？欢迎 PR

## License

MIT License
