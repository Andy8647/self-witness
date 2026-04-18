# self-witness

> **A structured self-understanding system, as a Claude Code skill.**
> 结构化自我理解系统 — 以 Claude Code skill 形式提供。

**Status**: `v0.1` — 作者本人 dogfood 中。**尚未邀请外部用户**。

---

## What this is / 它是什么

**不是** AI life coach。**不是** journal app。**不是** PKM / Obsidian 模板。

**是一个**:
- 用**证据**(真实事件 + 代码 + 数据)支撑的**个人画像档案**
- 用**反附和的镜子**代替温情滤镜,主动**批判和挑战**用户的 narrative
- 长期追踪**反复出现的决策模式 / 盲点 / 坑**,当它们在新情境重演时**主动指出**
- 用**代码侧 ground truth**(扫 `~/Projects/` / git history / 实际发布渠道)**校准** narrative vs 现实的漂移

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

## Roadmap

- [x] v0.1 — 骨架 + 方法论 docs + `/compile-me` 命令
- [ ] v0.2 — `/onboard-me` 完善 + `/journal` + `/retrospective` 命令
- [ ] v0.3 — 封装成标准 Claude Code skill(SKILL.md marketplace 级别)
- [ ] v0.4 — 开放给 3-5 个 dogfood 用户,收反馈
- [ ] v1.0 — 正式对外 + 考虑 B2P positioning(给心理咨询师 / 教练用的 client tool)

---

## License

MIT — see [`LICENSE`](./LICENSE)

## 作者

[@Andy8647](https://github.com/Andy8647)) / XHS: [@麻辣羊蹄](https://www.xiaohongshu.com/user/profile/631fa3b200000000230260a9)
