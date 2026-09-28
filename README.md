# 项目拉起文档 / Project Pickup Docs

一份给 **Grok、Claude Code、Codex** 用的 skill：按固定格式写项目拉起文档，换窗口、换模型也能直接接上。

[English](#english)

## 用途

解决的不是「文档写得漂不漂亮」，而是换一个 AI 还要重新讲一遍项目。

它规定下一扇窗口先读哪些文件、每类信息只写在哪、什么不能进 Git。

适合这些话：

- 更新文档，便于下次直接拉起
- 写成 skill / 导出给其他 AI
- 更新项目记忆、续接说明、RESUME.md
- 新开一个项目，按现有 Notes 结构建文档

它**不是**仓库整理器。全面审计、去重、备份请用 [organize-project-knowledge](https://github.com/fgyg007/organize-project-knowledge-skill)。

## 每类信息只写一个地方

| 问题 | 文件 | 怎么改 |
|---|---|---|
| 现在是什么、下一步 | `管理/项目记忆.md` | 整段替换 |
| 已经发生并验证 | `管理/项目历史.md` | 只追加 |
| 以后做 | `规划/路线图.md` | checkbox |
| 先不做 | `管理/技术债.md` | 不是路线图 |
| 下次怎么接 | `管理/续接说明.md` | 导航卡 |
| 代码 / Git / 端口 | `管理/代码与Git入口.md` | 不贴源码 |
| 新窗口 30 秒拉起 | 仓库 `docs/RESUME.md` | 命令 + 不要做什么 |
| 目录怎么走 | `00-项目入口.md` | 只链，不抄状态 |

Notes 管记忆、资料、私有配置。Git 管代码和工程文档。两边不要做成镜像。

## 安装

### Grok Build

```bash
git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.grok/skills/project-pickup-docs
```

### Claude Code

```bash
git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.claude/skills/project-pickup-docs
```

### Codex

```bash
git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.codex/skills/project-pickup-docs
```

安装后开一个新会话。更新：

```bash
git -C ~/.grok/skills/project-pickup-docs pull --ff-only
```

### 网页聊天（Claude / ChatGPT 等）

把 [PASTE.md](PASTE.md) 全文贴进对话，再说要写或更新哪个项目。

## 使用

```text
使用 $project-pickup-docs 更新这个项目的拉起文档，让下一个窗口可以直接接上。
```

```text
使用 $project-pickup-docs 按现有结构新建项目文档。先不要改代码。
```

## 仓库里有什么

```text
project-pickup-docs-skill/
├── SKILL.md                  # 给会装 skill 的 AI
├── PASTE.md                  # 给网页聊天，整份粘贴
├── agents/openai.yaml        # Codex 展示名
├── references/doc-types.json # 文档类型和必写章节
├── README.md
└── LICENSE
```

完整规则见 [SKILL.md](SKILL.md)。

## 许可

[MIT](LICENSE)

---

## English

A skill for **Grok, Claude Code, and Codex**. It tells the agent which pickup documents to write, where each kind of information belongs, and what must never go into Git — so the next window, on any of those tools, can resume without a recap.

It answers: *what is true now, what already happened, what to do next, and which file to open first.*

Use it when you say:

- update docs so the next session can pick up immediately
- turn this into a skill / export for another AI
- update project memory, handoff notes, or `RESUME.md`
- start a new project using the existing Notes layout

This is **not** a documentation auditor. For full-system cleanup, backups, and duplicate detection, use [organize-project-knowledge](https://github.com/fgyg007/organize-project-knowledge-skill).

### One home per fact

| Question | File | Edit rule |
|---|---|---|
| What is true now, and the next step | `管理/项目记忆.md` | Replace in place |
| What already happened and was verified | `管理/项目历史.md` | Append only |
| Work not started yet | `规划/路线图.md` | Checkboxes |
| Known issues to defer | `管理/技术债.md` | Not the roadmap |
| How the next session starts | `管理/续接说明.md` | Navigation card |
| Code / Git / ports | `管理/代码与Git入口.md` | No source dumps |
| 30-second boot | repo `docs/RESUME.md` | Commands + do-nots |
| How to navigate | `00-项目入口.md` | Links only |

Notes hold memory, assets, and private config. Git holds code and engineering docs. Do not mirror the two trees.

### Install

Grok:

```bash
git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.grok/skills/project-pickup-docs
```

Claude Code:

```bash
git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.claude/skills/project-pickup-docs
```

Codex:

```bash
git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.codex/skills/project-pickup-docs
```

Start a new session after install. For a browser chat, paste [PASTE.md](PASTE.md) in full, then name the project.

### Use

```text
Use $project-pickup-docs to update this project's pickup docs so the next window can resume.
```

### License

[MIT](LICENSE)
