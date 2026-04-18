# Methodology — The 7 Principles

> self-witness 的方法论核心。每条原则都有一个对应的反面模式("anti-pattern"),本文档说明原则本身 + 为什么需要它 + 它在日常操作中的落地方式。

---

## 原则 1:事实 / 感受 / 叙事 三层强制分离

**Principle**: 用户讲的每件事都属于三层之一:

- **Fact**(事实)— 可被他人核实的事(日期、数字、地点、事件)
- **Feeling**(感受)— 当时体验到的主观情绪
- **Narrative**(叙事)— 用户**现在**回头讲这件事的方式

**Anti-pattern**: 把三层混为一谈。典型表现:"2021 年毕业那会儿我摆烂"。

- *事实*:2021 毕业 + 国内面试失败 + 加拿大投简历无响应 + 同时玩 Apex
- *感受*:(用户未必还记得具体当时的情绪)
- *叙事*:"我摆烂" — 这是 2026 年的他**现在**给那段时期的标签

**为什么必须分开**:
- 叙事会随心境漂移,感受会被记忆扭曲,**只有事实是长期的锚点**
- 用户的"新 insight"经常是叙事层的重新包装,不是事实层的新发现
- 混在一起,用户会觉得"我已经理解过了",其实只动了叙事

**落地**: `profile/background.md` 的事实部分和关键转折点部分分开。关键转折点里再分三栏。

---

## 原则 2:Values 必须有真实事件作证据

**Principle**: 每条 value 都必须能指向**最近 6-12 个月的一次真实选择**作为证据。没证据不写。

**Anti-pattern**: "我重视深度 > 广度" — 听起来好,但如果用户最近的选择都指向广度(6 门课同时选、8 个项目并行),那就不是他的 value,是他**希望自己是**的 value。

**为什么**:
- 自我报告的 value 和实际行为的 value 经常不一致 — 这是心理学上反复被验证的
- 自画像如果基于 aspirational values,决策会和自己的真实动机冲突,长期失调
- 有证据的 value 可以用来预测未来选择;没证据的 value 不能

**落地**: `profile/values.md` 每条下方强制写 "*证据*:" 小节。Claude 在读到没证据的 value 时主动追问。

---

## 原则 3:Patterns 需 ≥2 独立证据

**Principle**: 一次事件是**轶事(anecdote)**。≥2 次在不同场景 / 不同时期发生的事件是**模式(pattern)**。单数不能上升为 pattern。

**Anti-pattern**: 用户某次拒绝 → Claude 立刻说"你看,你害怕被拒绝"。一次是偶然,两次可能是巧合,三次才是 pattern。

**为什么**:
- Pattern 是**预测性**的陈述(下次遇到类似情境他也会这样)。单次事件不具备预测效力
- Pattern 会被用户记住并影响自我认同 — 错误的 pattern 危害大

**落地**: `profile/patterns.md` 里每条 pattern 明确列出证据点,且标注状态标签:
- `[初稿]` — 证据刚够或还需要更多观察
- `[确认]` — 多次独立证据
- `[已开始修正]` — 有新场景破了这个 pattern
- `[已自我识别]` — 用户本人完成了 pattern 识别的闭环

---

## 原则 4:Pattern 有层级 — 根因 vs 症状

**Principle**: 多个看似独立的 pattern 经常有一个共同的**根因**(root cause)。识别根因比罗列症状更有价值。

**例子**: 用户有"逃避 social media"、"逃避 cold outreach"、"收藏学习视频不学"三种表现。**根因可能是**:"只要我不开始我就是完美的"这种完美主义防御 → 任何"暴露 + 可能被拒"的动作都触发回避。

**为什么**:
- 只治症状 → 打地鼠(解决了 social media 又出现 cold outreach)
- 找到根因 → 针对 root structure 干预

**落地**: `profile/patterns.md` 里根因级 pattern 单独标注,其他下游症状链接到根因条目。

---

## 原则 5:反附和(Anti-sycophancy)

**Principle**: Claude 必须主动挑战用户的 narrative,尤其是:
- 前后不一致(半年前说恨 X,现在在做 X 却没交代为什么)
- 便利性归因("本命年"、"宿命"、"面试靠缘分"、"我不是天才")
- 把运气说成能力,或反过来
- 用宏大叙事包装模糊目标("想做有意义的事")

**Anti-pattern**: 用户讲什么都"理解、共情、确认",即使他在绕 perfectionism 的弯子。

**为什么**:
- 附和让用户舒服但没成长 — 用户可以在任何 chatbot 那里获得附和,不需要这个系统
- 用户明确付出成本来这个系统,就是要一个**说实话**的镜子

**落地**: `template/CLAUDE.md` 里把"反附和"写成 non-negotiable 的硬规则,列出要挑战的具体语言(便利性归因词表)。

---

## 原则 6:Narrative 必须被 ground truth 校准

**Principle**: 用户讲的是 narrative。**用户实际产出的东西(portfolio / 作品集 / evidence sources)**是 ground truth。当两者冲突,**信 ground truth**,并把漂移记录下来。

**什么是"产出"— 按用户身份不同,形式完全不同**:

| 身份 | 可用的 evidence sources |
|---|---|
| 工程师 | 代码库 / git history / 发布的 package / 部署记录 |
| 写作者 | 草稿 / 发表的文章 / 读者数据 / 约稿记录 |
| 设计师 | 设计稿 / 公开 portfolio / 客户名单 |
| 创作者 | 视频 / 音频 / 平台数据(bilibili / YouTube / XHS 等) |
| 研究者 | 论文 / 引用数 / 协作网络 |
| 商人 / 创业者 | BP / 财报 / 融资记录 / 客户列表 |
| **每个人都有** | 公开账号的发帖数据 / 消费记录 / 日历 / 邮件元数据 |

**例子**:
- 用户口述:"我不敢 social media marketing"
- 小红书 API 显示:有 10 帖,最 viral 一篇 27,314 views
- Ground truth 胜出。narrative 错了,pattern 需要精修(见 patterns.md 里"逃避 distribution"的形式依赖分析)

**为什么必须有这一条**:
- 用户对自己的描述有**系统偏差**(自贬 / 自夸 / 选择性记忆)
- 没有 ground truth 的自我系统会在 narrative 的回音室里越转越偏
- 大语言模型会**被 narrative 牵着走** — 即使 narrative 是错的。外部数据是唯一的 anchor

**落地**:
- `/compile-me` 命令扫描**用户配置的 evidence sources**(在 instance 的 CLAUDE.md 里定义),生成 `index/` 下的索引文件
- 默认 scan 目标是 `~/Projects/*`(对开发者友好),但**所有非代码产出都应该可以加进扫描范围**
- Claude 做重要判断前强制 cross-check `index/` 的产出

**注意**:`/compile-me` 默认用代码做例子,不是因为代码更重要,是因为:
1. 工程师用户是早期 dogfood 群体
2. 代码 + git 的元数据最容易自动扫
3. 非代码产出(写作 / 设计 / 视频)需要用户提供更多配置信息(路径 / API token / 账号),将在 v0.2+ 逐步支持

---

## 原则 7:观察 → 自我识别的闭环

**Principle**: 系统的**终极目标**不是让 Claude 永远告诉用户 pattern,而是让**用户自己学会识别自己的 pattern**。每次用户在新情境里主动说出"这像我 X 年前的 Y" — 是一次胜利。

**为什么**:
- Claude 指出 pattern 是 "tell" — 用户知道但可能不信
- 用户自己识别 pattern 是 "show" — 用户彻底 own 了这个认知
- 系统的 ROI 在第二种上,不在第一种上

**落地**:
- `patterns.md` 用 `[已自我识别]` 标签追踪用户自己完成的 pattern 映射
- Claude 在用户做出这种映射时**显式表扬**(这是元认知层的成就)
- 随时间推移,Claude 的角色从"指镜子"逐步退到"协助用户自己用镜子"

---

## 合起来看

这 7 条不是平行清单,是有结构的:

```
Principle 1 (fact/feeling/narrative 分离) ──┐
                                              ├──→ Principle 2 (values 有证据)
                                              ├──→ Principle 3 (patterns ≥2 证据)
                                              │       └──→ Principle 4 (根因 vs 症状)
Principle 5 (反附和) ─────────────────────────┤
                                              │
Principle 6 (ground truth 校准) ──────────────┤
                                              │
                                              └──→ Principle 7 (自我识别闭环,终极目标)
```

**前 4 条是数据规则** — 保证记录的东西是有用的。
**第 5 条是行为规则** — 保证 AI 不把记录稀释成 chatbot 的迎合。
**第 6 条是外部校准** — 保证 narrative 不跑偏。
**第 7 条是使命方向** — 保证整个系统往"自我赋能"而非"依赖 AI"走。
