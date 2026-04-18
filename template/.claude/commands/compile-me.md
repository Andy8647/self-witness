---
description: Compile the user's portfolio (evidence sources) + ideas into index/ so future sessions have ground-truth context beyond narrative
---

# /compile-me

索引用户的 **portfolio / 作品集 / evidence sources**,让后续 session 有外部 ground truth,而不是只依赖口述 narrative(narrative 常常会遗漏 / 淡化 / 误标)。

## "Portfolio"不等于代码

每个用户的 evidence sources 形式不同。默认扫代码仓库(工程师用户多),但**可以并且应该**配置成用户实际产出的形式:

- 工程师:`~/Projects/*` + git history + 发布 package
- 写作者:`~/Writing/drafts/` + `~/Writing/published/`
- 设计师:`~/Design/portfolio/` + Figma / Framer export
- 创作者:XHS / B 站 / YouTube API + 本地素材库
- 研究者:论文目录 + Zotero / Scholar API
- 商人:`~/Business/` + 邮件元数据

**用户需要在自己的 instance 的 `CLAUDE.md` 里定义 `## 我的 Evidence Sources` 节**(template CLAUDE.md 里有示范格式)。

## 默认扫描(若用户未配置)

**扫**:
- `~/Projects/*`(排除**本 self-witness instance 自身** + 任何用户手动标记的 `🔴 排除` 目录)
- 如果用户有 Obsidian Vault 且提及 `Ideas/`:`<vault>/Ideas/*`(**pointer-only,不复制内容**)

**不扫**(永远排除):
- `~/Downloads/*`(易变,不代表长期画像)
- 任何 `.env*` / 凭证 / gitignored 内容
- `.git/` / `node_modules/` / `.venv/` / `dist/`
- 客户 / 他人私密数据目录

用户可以在本命令运行时临时指定 `include:` 和 `exclude:` 覆盖默认。

## 执行方式

并行派 Explore agent(避免污染主 context),按用户配置的 evidence sources 数量:
- **默认(代码)**:1 个 agent 扫 `~/Projects/*`,按 schema 生成逐项目摘要 + discovery 观察
- **如有 ideation library**(Vault/Ideas 或等价):1 个 agent pointer-only 扫
- **如有其他 source**(写作 / 设计 / 创作者 API 等):每个 source 1 个 agent

主 Claude 收到报告后,写入:
- `index/portfolio.md`(master + 所有 evidence items)
- `index/ideas.md`(ideation pointer 索引,如有)
- `index/<其他 source>.md`(根据用户配置扩展)

## 墙状态 (wall status) — 必须诚实

- 🟢 **穿墙**:有 commits + 外部可见(部署 / 发布 / 用户 / 下载)
- 🟡 **墙前**:有代码 / 文档 / BP,但**没暴露给外人**
- ⚪ **前墙期**:仅调研 / ideation
- 🔴 **排除**:非用户原创 / 已弃 / 不是项目

**重要**:`.git init` 但 0 commits **≠ 穿墙**。要看实际 external reach。

## Evidence item schema(每个 portfolio item ≤ 12 行)

```
### <slug / 作品名>

- **目的 / 主题 (one line)**
- **墙状态**: emoji + label
- **媒介 / Tech stack**: 代码语言 / 写作主题 / 设计工具 / 视频平台 / 等等
- **最近活动**: 最后修改 / 发布日期 + 数量信号(commits / 字数 / 稿数 / views)
- **外部可见产物**: URL / 发表处 / 平台数据 / 用户反馈
- **3 个 nugget**: 具体事实,不空话
```

## Idea schema(pointer-only)

```
### <title>

- **一句话**: Claude 读后写的 summary,**不复制内容**
- **Size**: notes / structured / scattered
- **执行状态**: 📦 Vault-only / 🟡 已迁 Projects 墙前 / 🟢 已迁 Projects 穿墙 / 🗑️ 看起来已弃
- **执行 project**: `~/Projects/<name>/`(如有)
- **最后改动**: YYYY-MM-DD
- **Vault 路径**
```

## 编译后:Discovery Report

给用户一个**对照报告**,专门找 **narrative vs code 的漂移**:

1. 他口述没提但代码里存在的项目
2. 代码显示比 narrative 严重的项目(他低估自己)
3. 代码显示比 narrative 夸张的项目(他高估自己)
4. 只能从代码看到的 pattern(例如:N of M 项目有 README + `git init` + 0 commits)

**这一层对比是 compile 的核心价值** —— 不只是索引,是镜子校准。

## 何时重跑

- 用户开了新项目 / 弃了老项目
- Vault/Ideas 里新加了 idea
- 某个 idea 从 Vault 迁到 Projects
- **默认节奏**:每季度一次,或觉得 narrative 漂移了就跑

## 禁止事项

- 不要自动注入 index 到每个 session — 按需 Read
- 不要把 Vault idea 全文复制进 self-witness instance(single source of truth = Vault)
- 不要把墙状态写得比实际好看("鼓励"不是这个系统的任务)
