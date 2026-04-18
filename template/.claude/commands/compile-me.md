---
description: Compile ~/Projects/ and Vault/Ideas/ into index/ so future sessions have ground-truth context beyond narrative
---

# /compile-me

索引用户的项目和 ideas,让后续 session 有代码侧的 ground truth,而不是只依赖口述 narrative(narrative 常常会遗漏 / 淡化 / 误标)。

## 默认扫描范围

**扫**:
- `~/Projects/*`(排除**本 self-witness instance 自身** + 任何用户手动标记的 `🔴 排除` 目录)
- 如果用户有 Obsidian Vault:`<vault>/Ideas/*`(**pointer-only,不复制内容**)

**不扫**:
- `~/Downloads/*`
- 任何 `.env*` / 凭证 / gitignored 内容
- `.git/` / `node_modules/` / `.venv/` / `dist/`

用户可以在本命令运行时临时指定 `include:` 和 `exclude:` 覆盖默认。

## 执行方式

并行派两个 Explore agent(避免污染主 context):
- **Agent 1**:扫 `~/Projects/*`,按 schema 生成逐项目摘要 + discovery 观察
- **Agent 2**:扫 `Vault/Ideas/*`(如果存在),生成 pointer-only 索引

主 Claude 收到两份报告后,写入:
- `index/projects.md`(master + 所有项目)
- `index/ideas.md`(Ideas pointer 索引,如有)

## 墙状态 (wall status) — 必须诚实

- 🟢 **穿墙**:有 commits + 外部可见(部署 / 发布 / 用户 / 下载)
- 🟡 **墙前**:有代码 / 文档 / BP,但**没暴露给外人**
- ⚪ **前墙期**:仅调研 / ideation
- 🔴 **排除**:非用户原创 / 已弃 / 不是项目

**重要**:`.git init` 但 0 commits **≠ 穿墙**。要看实际 external reach。

## Project schema(每项目 ≤ 12 行)

```
### <slug>

- **目的 (one line)**
- **墙状态**: emoji + label
- **Tech stack**
- **最近活动**: 最后 commit / 文件改动 + commits 数
- **可见产物**: 部署地址 / npm / PyPI / etc.
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
