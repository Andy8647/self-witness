# self-witness

> **A structured self-understanding system, as a Claude Code skill.**
> 结构化自我理解系统 — 以 Claude Code skill 形式提供。

**Status**: `v0.1` — 开源、早期、作者本人已完整跑过一轮 onboarding 并在用。欢迎试用、提 Issue、反馈、fork。

---

## What this is / 它是什么

**不是** AI life coach。**不是** journal app。**不是** PKM / Obsidian 模板。

**是一个**:
- 用**真实事件**支撑的**个人画像档案**(不是抽象口号)
- 用**反附和的镜子**代替温情滤镜,主动**批判和挑战**用户的 narrative
- 长期追踪**反复出现的决策模式 / 盲点 / 坑**,当它们在新情境重演时**主动指出**
- 用**你自己的产出 (portfolio)** 校准 narrative vs 现实的漂移 — 不论你的产出是什么形式

"产出 / 作品集"不只是代码:

| 身份 | 你的 evidence sources 可能是 |
|---|---|
| 工程师 | git repo / package 发布 / 部署记录 |
| 写作者 | 草稿 / 发表的文章 / 读者数据 |
| 设计师 | 设计稿 / 公开 portfolio / 客户作品 |
| 创作者 | 视频 / 平台数据(B 站 / YouTube / 小红书) |
| 研究者 | 论文 / 引用数 / 协作网络 |
| 商人 / 创业者 | BP / 融资记录 / 客户名单 |
| 每个人 | 公开账号的发帖数据 / 日历 / 邮件 |

`/compile-me` 命令**默认扫代码仓库**(开发者方便),但你可以在自己的 CLAUDE.md 里配置扫描路径,让它工作在任何产出形式上。

核心差异点:**它把"第三方观察者"这个角色做成一个长期、结构化、反附和的系统**,不是"陪你聊天"。

---

## Why it exists / 为什么需要它

大多数 AI 对话工具有两个缺陷:
1. **附和倾向**:大语言模型默认迎合用户的 narrative,即使那个 narrative 是自欺
2. **无长期记忆 / 无校准机制**:你今天说的和一年前说的矛盾,AI 不会指出;你说的"我不敢 marketing"和代码里 10 篇小红书帖冲突,AI 不会知道

`self-witness` 用**文件系统 + 严格的记录规则**解决这两个问题:
- 一切记忆是文件(`profile/`、`journal/`、`patterns.md`),人类可读可改
- 规则写死在 `CLAUDE.md` 里,强制 Claude 反附和 / 追问 / 校准

---

## The 7 core principles / 7 条核心原则

完整方法论见 [`docs/methodology.md`](./docs/methodology.md)。简版:

1. **事实 / 感受 / 叙事 三层强制分离**
2. **Values 必须有真实事件作证据**,不记抽象口号
3. **Patterns 需 ≥2 独立证据**才算模式,1 次是轶事
4. **Pattern 有层级**(根因 vs 下游症状)
5. **反附和** — AI 被明确要求批判,不走温情滤镜
6. **Narrative 必须被 ground truth 校准**(`/compile-me` 命令)
7. **观察 → 自我识别的闭环** — 最终目标是用户自己识别 pattern

---

## Quick start / 快速开始

```sh
# 1. clone 或复制 template/ 到你自己的个人 OS 目录
cp -r template ~/Projects/my-self/   # 或任何你喜欢的名字

# 2. 打开 Claude Code,cd 进去
cd ~/Projects/my-self

# 3. 触发 onboarding
/onboard-me
```

初次 onboard 大概需要 60-120 分钟。完整体验见 [`docs/onboarding-playbook.md`](./docs/onboarding-playbook.md)。

---

## Status

`v0.1` — scaffold 阶段。**作者本人已完整跑过一轮 onboarding 并开始常态使用**。产品形态仍在验证。

欢迎任何人:
- **试用**(clone 或 copy `template/` 到自己目录)
- **提 Issue**([bug / 不够泛化的地方 / 功能请求 / 困惑的地方](https://github.com/Andy8647/self-witness/issues))
- **Fork 和改**(MIT,随意)

---

## License

MIT — see [`LICENSE`](./LICENSE)

## 作者

[@Andy8647](https://github.com/Andy8647)) / XHS: [@麻辣羊蹄](https://www.xiaohongshu.com/user/profile/631fa3b200000000230260a9)
