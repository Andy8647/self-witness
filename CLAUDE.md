# self-witness — contributor-side instructions

**这不是用户使用 self-witness 的 CLAUDE.md**(那个在 `template/CLAUDE.md`)。
**这是给帮忙开发 self-witness 项目本身的 Claude 看的。**

## Project purpose

`self-witness` 是一个 Claude Code skill + 文件模板系统,目的是提供结构化的自我理解体系。不是 chat companion,不是 life coach,是"反附和的外部观察者"角色。

## Repo layout

```
self-witness/
├── README.md         # 对外的 pitch
├── SKILL.md          # 给 Claude Code skill 系统读的
├── CLAUDE.md         # (本文件) 给开发者侧的 Claude 看
├── LICENSE           # MIT
├── docs/             # 方法论 + 运行手册
│   ├── methodology.md
│   └── onboarding-playbook.md
└── template/         # 用户 clone 或 copy 到自己 personal OS 目录的模板
    ├── CLAUDE.md     # 模板用户那端的 instance rules
    ├── profile/
    ├── journal/
    ├── reviews/
    ├── index/
    └── .claude/commands/
```

## Design principles (for anyone contributing)

1. **模板要 evidence-prompting**:每个 profile 文件要显式要求用户填**具体事件** / **日期** / **数字**,不能让用户填抽象口号。
2. **Skill 规则要可机器检查**:反附和 / fact-vs-narrative / pattern 证据数 等规则写成 Claude 能触发检查的条目,不是长篇 prose。
3. **保留 opinionated 立场**:不为了"大众化"而稀释方法论。如果一个用户不接受"反附和"的前提,他们不是 target user。
4. **Don't leak author data**:`template/` 下的任何文件不能含有作者(Andy)的个人数据。引用例子时用匿名 `<用户>` / `_(示例)_`。

## Naming conventions

- `self-witness` = 项目 / skill 名
- `self-witness instance` = 用户克隆 template 后的他们自己的目录(e.g., `~/Projects/my-self/`)
- **不要**在文案里把 Claude 称为 "mentor" / "coach" / "therapist" — 永远是 "external observer" 或 "镜子" 或 "见证者"

## Status

v0.1 — 开源早期。作者本人已完整使用一轮并在常态使用。欢迎贡献。
