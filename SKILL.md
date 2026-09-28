---
name: project-pickup-docs
description: >
  Use when writing or updating project pickup docs, 项目入口, 项目记忆, 项目历史,
  续接说明, 路线图, 技术债, RESUME.md, AGENTS.md; when the user wants docs another
  AI (Grok, Claude, Codex) can import; or says 更新文档便于下次拉起, 做成skill,
  导出给其他AI, 项目记忆, 续接说明.
---

# 项目拉起文档

给下一个窗口（任意 AI）用。权威治理仍以 Notes `10-项目/个人项目/项目管理规则.md` 为准。本技能只规定**要写出哪些文件、每份写什么、什么不能进 Git**。

## 先读再写

1. Notes 入口：`/Volumes/notes/10-项目/个人项目/<项目>/00-项目入口.md`（未挂载就说一声，改用仓库文档）。
2. 仓库：`docs/RESUME.md`、`AGENTS.md`、`docs/notes/`（快照，不是权威）。
3. 已有文件就改，不要另开平行的「总结.md」「handoff.md」「给Claude.txt」。

## 权威一张表

| 问题 | 只写这里 | 行为 |
|---|---|---|
| 现在是什么、唯一下一步 | `管理/项目记忆.md` | 整段替换，不当日记 |
| 已经发生并验证的事 | `管理/项目历史.md` | 只追加，不改写旧段 |
| 以后做、还没做 | `规划/路线图.md` | checkbox |
| 已知但先不做 | `管理/技术债.md` | 不是路线图 |
| 下次怎么接上 | `管理/续接说明.md` | 导航卡，不抢记忆的权威 |
| 代码/Git/端口/同步 | `管理/代码与Git入口.md` | 不贴源码 |
| 新窗口 30 秒拉起 | 仓库 `docs/RESUME.md` | 可跑命令 + 不要做什么 |
| 目录怎么走 | `00-项目入口.md` | 只链，不复制状态 |

NAS/Notes 管记忆、资料、题包、私有配置。Git 管代码、schema、自撰 fixture、工程文档、`docs/notes/` 快照。两边不要做成镜像。

## 目录（成熟项目）

```text
<项目名>/                          # Notes：/Volumes/notes/10-项目/个人项目/<项目名>/
├── 00-项目入口.md
├── 管理/
│   ├── 续接说明.md
│   ├── 项目记忆.md
│   ├── 项目历史.md
│   ├── 技术债.md
│   └── 代码与Git入口.md
├── 规划/路线图.md
├── 测试与验收/
├── 项目数据/
├── 私有配置/00-私有配置说明.md
├── 原始资料/                      # 可选
└── 归档/

<repo>/
├── AGENTS.md
├── docs/RESUME.md
└── docs/notes/                    # 推送前从 Notes 管理文档快照；不是权威
```

没有内容的目录不要空建。旧命名 `项目名-项目记忆.md` 若已存在，继续用，不要并列一份 `管理/项目记忆.md`。

## 输出规则

- 中文正文。路径、命令、仓库名保持原样。
- Obsidian：`[[wikilink]]`，警告用 `> [!warning]`。
- 每份管理文档带 YAML。`updated` 用当天日期。
- **项目记忆**必须有「当前事实 / 当前目标 / 唯一下一步 / 明确不做」。
- **续接说明**必须有「下次可以直接说」的一句口令。
- **RESUME.md**必须有：30 秒检查、能跑的命令、端口、不要做什么、当前事实、唯一下一步。
- 写完后列出：改了哪些路径、权威在哪、下一窗口先读哪一份。

## 禁止

- 密钥、Token、`.env` 真值、试卷 PDF/Word、真实题库 JSON、学习库、数据库进 Git 或聊天。
- 把聊天记录整段贴进文档。
- 发明第二套入口文件。
- 把「计划」写成「已完成」，或把技术债写进路线图当进度。
- 未请就 `git push` / 建 GitHub 仓。

## 交给其他 AI

对方能装 skill，从 GitHub 克隆：

- Grok：`git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.grok/skills/project-pickup-docs`
- Claude Code：`git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.claude/skills/project-pickup-docs`
- Codex：`git clone https://github.com/fgyg007/project-pickup-docs-skill.git ~/.codex/skills/project-pickup-docs`

对方只能聊天：把 `PASTE.md` 全文贴进对话，再说「按这个写/更新拉起文档」。

机器校验字段见 `references/doc-types.json`。
