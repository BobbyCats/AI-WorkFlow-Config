# Claude Code 使用技巧 (中文版)

> [!INFO] 说明
> 本文翻译自 [[Claude Code tips]]，原文由 Claude Code 的创建者 Boris 撰写，分享了开发团队内部的高效使用技巧。

我是 Boris，Claude Code 的创建者。我想快速分享一些来自 Claude Code 团队的直接建议。团队使用 Claude 的方式与我不同。请记住：使用 Claude Code 没有所谓的“唯一正确方式”——每个人的设置都不同。你应该多尝试，找到适合自己的工作流！

## 目录

**原版技巧（来自 Boris）**

1. [并行处理更多任务](#1-并行处理更多任务-do-more-in-parallel)
2. [复杂任务从"计划模式"开始](#2-复杂任务从计划模式开始-start-in-plan-mode)
3. [投资你的 CLAUDE.md](#3-投资你的-claudemd)
4. [创建并提交自定义技能](#4-创建并提交自定义技能-create-your-own-skills)
5. [Claude 能自己修复大多数 Bug](#5-claude-能自己修复大多数-bug-claude-fixes-most-bugs-by-itself)
6. [提升提示词水平](#6-提升提示词水平-level-up-your-prompting)
7. [终端与环境设置](#7-终端与环境设置)
8. [使用子智能体](#8-使用子智能体-use-subagents)
9. [用 Claude 做数据与分析](#9-用-claude-做数据与分析-use-claude-for-data--analytics)
10. [用 Claude 学习](#10-用-claude-学习)

**补充技巧（社区实践）** 11. [利用 /compact 压缩上下文](#11-利用-compact-压缩上下文) 12. [善用 @ 符号精确引用](#12-善用--符号精确引用) 13. [设置 .claudeignore 文件](#13-设置-claudeignore-文件) 14. ["思考"提示词模式](#14-思考提示词模式) 15. [利用 Vim 模式](#15-利用-vim-模式如果你是-vim-用户) 16. [多轮验证模式](#16-多轮验证模式) 17. [用 --print 模式快速获取答案](#17-用---print-模式快速获取答案)

---

## 1. 并行处理更多任务 (Do more in parallel)

同时启动 3-5 个 git worktrees，每个都在并行运行自己的 Claude 会话。这是提升生产力的最大解锁点，也是团队的首要建议。

- **个人习惯**：我个人使用多个 git checkouts，但大多数 Claude Code 团队成员更喜欢 worktrees——这也是 [@amorriscode](https://x.com/amorriscode) 在 Claude Desktop 应用中内置支持它的原因！
- **技巧**：有些人给 worktrees 命名并设置 shell 别名（如 `za`, `zb`, `zc`），以便一键切换。还有人设置专门的“分析”worktree，仅用于读取日志和运行 BigQuery。
- 参考：[官方文档 - Git Worktrees](https://code.claude.com/docs/en/common-workflows#run-parallel-claude-code-sessions-with-git-worktrees)

## 2. 复杂任务从“计划模式”开始 (Start in plan mode)

对于每个复杂的任务，先投入精力制定计划，这样 Claude 就能一次性成功实现（1-shot）。

- **团队做法**：有人让一个 Claude 写计划，然后启动第二个 Claude 作为“Staff Engineer”来审查它。
- **纠错**：一旦事情偏离轨道，立即切回计划模式重新规划，不要硬着头皮继续。
- **验证**：明确告诉 Claude 进入计划模式来执行验证步骤，而不仅仅是构建步骤。

## 3. 投资你的 `CLAUDE.md`

在每次修正错误后，以这句话结束："更新你的 `CLAUDE.md`，以免再犯同样的错误。"

- **效果**：Claude 非常擅长为自己制定规则。
- **迭代**：随着时间的推移，无情地编辑你的 `CLAUDE.md`。不断迭代，直到 Claude 的错误率显著下降。
- **案例**：一位工程师让 Claude 为每个任务/项目维护一个笔记目录，在每次 PR 后更新，并将 `CLAUDE.md` 指向该目录。

## 4. 创建并提交自定义技能 (Create your own skills)

将技能提交到 git，以便在不同项目中复用。

- **团队建议**：
  - 如果你某件事每天做超过一次，就把它变成技能或命令。
  - 构建一个 `/techdebt`（技术债）斜杠命令，在每次会话结束时运行，查找并消除重复代码。
  - 设置一个斜杠命令，将过去 7 天的 Slack、GDrive、Asana 和 GitHub 内容同步到一个上下文转储中。
  - 构建类似分析工程师的 Agent，用于编写 dbt 模型、审查代码并在开发环境中测试变更。
- 了解更多：[官方文档 - Skills](https://code.claude.com/docs/en/skills#extend-claude-with-skills)

## 5. Claude 能自己修复大多数 Bug (Claude fixes most bugs by itself)

以下是团队的做法：

- **做法**：启用 Slack MCP，将 Slack 上的 Bug 讨论帖粘贴给 Claude，然后只说“修复它 (fix)”。无需切换上下文。
- **CI 测试**：或者直接说“去修复失败的 CI 测试”。不要微观管理它怎么做。
- **分布式系统**：将 Claude 指向 Docker 日志来排查分布式系统问题——它在这方面能力惊人。

## 6. 提升提示词水平 (Level up your prompting)

- **a. 挑战 Claude**：说“严格拷问这些变更，在我通过你的测试之前不要提交 PR。”让 Claude 成为你的代码审查员。或者说“向我证明这能工作”，让 Claude 对比主分支和你功能分支的行为差异。
- **b. 重构**：在一次不太满意的修复之后，说："基于你现在知道的一切，废弃这个方案，实现那个优雅的解决方案。"
- **c. 减少歧义**：在移交工作前编写详细的规格说明。你越具体，输出越好。

## 7. 终端与环境设置

团队非常喜欢 **Ghostty**！许多人喜欢它的同步渲染、24位色彩和良好的 Unicode 支持。

- **状态栏**：为了更轻松地管理多个 Claude，使用 `/statusline` 自定义状态栏，始终显示上下文使用量和当前 git 分支。
- **组织**：许多人会对终端标签页进行颜色编码和命名，有时使用 tmux——每个任务/worktree 一个标签页。
- **语音输入**：使用语音听写。你说话的速度比打字快 3 倍，这会让你的提示词变得更加详细。（macOS 上按两下 fn 键）。
- 更多技巧：[官方文档 - Terminal Config](https://code.claude.com/docs/en/terminal-config)

## 8. 使用子智能体 (Use subagents)

- **a. 增加算力**：在任何你希望 Claude 投入更多算力的问题后加上“使用子智能体 (use subagents)”。
- **b. 任务分流**：将独立任务分流给子智能体，以保持主智能体的上下文窗口干净专注。
- **c. 权限管理**：通过 hook 将权限请求路由给 Opus 4.5——让它扫描攻击并自动批准安全的请求（见 [Hooks 文档](https://code.claude.com/docs/en/hooks#permissionrequest)）。

## 9. 用 Claude 做数据与分析 (Use Claude for data & analytics)

让 Claude Code 使用 `bq` CLI 实时拉取和分析指标。

- **案例**：我们在代码库中签入了一个 BigQuery skill，团队每个人都直接在 Claude Code 中使用它进行分析查询。我个人已经 6 个多月没写过一行 SQL 了。
- **适用性**：这适用于任何拥有 CLI、MCP 或 API 的数据库。

## 10. 用 Claude 学习

团队使用 Claude Code 进行学习的一些技巧：

- **a. 解释**：在 `/config` 中启用“Explanatory”（解释性）或“Learning”（学习）输出风格，让 Claude 解释变更背后的*原因*。
- **b. 可视化**：让 Claude 生成解释陌生代码的 HTML 演示文稿。它做的幻灯片出奇地好！
- **c. 图表**：让 Claude 绘制新协议和代码库的 ASCII 图表，帮助你理解它们。
- **d. 间隔重复**：构建一个间隔重复学习技能：你解释你的理解，Claude 提出后续问题填补空白，并存储结果。

---

## 补充技巧（社区实践）

> [!NOTE] 说明
> 以下技巧来自社区实践和使用经验总结，作为原文 10 条技巧的补充。

### 11. 利用 `/compact` 压缩上下文

当对话变长时，使用 `/compact` 命令让 Claude 自动总结历史对话，释放上下文窗口空间。适合长时间调试或迭代的场景。

### 12. 善用 `@` 符号精确引用

- `@文件名` 直接引用文件
- `@符号名` 引用代码中的函数/类
- 比手动复制粘贴代码更高效，且保持引用关系

### 13. 设置 `.claudeignore` 文件

类似 `.gitignore`，排除不想让 Claude 索引的文件夹（如 `node_modules`、`dist`、日志文件等），减少噪音、加快响应。

### 14. "思考"提示词模式

对于复杂问题，明确要求 Claude 先思考再行动：

> "在写代码之前，先列出你的思路和可能的陷阱。"

这会显著提高一次成功率。

### 15. 利用 Vim 模式（如果你是 Vim 用户）

Claude Code 支持 Vim 键位绑定，可以在 `/config` 中启用，提升终端内操作效率。

### 16. 多轮验证模式

对于关键变更，要求 Claude 做"三连验证"：

> "实现后，运行测试并告诉我结果。如果失败，自行修复。直到所有测试通过。"

这让 Claude 形成自动迭代闭环。

### 17. 用 `--print` 模式快速获取答案

如果只需要一个快速回答（不需要交互式会话）：

```bash
claude --print "这段代码有什么问题？" < file.py
```

适合嵌入到 CI/CD 或自动化脚本中。
