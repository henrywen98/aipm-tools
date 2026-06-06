# grill-me-only

> 把方案问透，再开干。

一个**只负责拷问**的 skill：你抛一个想法 / 设计 / 方案 / 决策给它，它沿着决策树深度优先地、一题一题问你，每个问题都附带**推荐答案 + 一句为什么**，并在你回答时自动处理依赖（上游答案变了就重画下游分支）。所有问题穷尽后，输出一份结构化的 Decision Record。

**它不写文档、不写代码、不画图、不实现任何东西。** 只 grill。

## 为什么需要它

大多数"帮我想清楚"的对话最后都变成 AI 直接给方案，跳过了真正该和人对齐的决策点。`grill-me-only` 反过来：把每个决策摊开来问你，并且每个问题都先给出推荐答案——你只要说"按推荐"就能往下走，不想按推荐就当面 push back。等于强迫一次彻底的设计 review，但成本是几条对话。

## 触发方式

直接说出以下任意一种（中英文都行）：

- `grill me` / `grill me on this`
- `interview me` / `interview me relentlessly`
- `walk me through every decision`
- `审问我` / `拷问我` / `盘问我`
- `把我问清楚` / `把方案问清楚再开干`
- `穷尽设计空间` / `决策树访谈`
- `逐项问我` / `一项一项问我`
- `帮我把这个想透`

或者直接 `/grill-me-only`（如果作为 skill 被 Claude Code 自动注册）。

## 工作流程

```
Phase 0  框定主题 (Subject / Goal / Constraints / 已有材料)
Phase 1  画出 3-7 个顶层分支决策树，让你确认
Phase 2  深度优先 + 依赖优先地走每个叶子决策
         每题一句问 + Recommended + Why + 2-4 个选项
         你的答案重塑下游 → 自动重画
         冲突立刻挑出来要你裁决
Phase 3  全部 RESOLVED 或 DEFERRED → 终止
         (你也可以随时 stop / enough / 够了)
Phase 4  输出 Decision Record（决策 + 推迟项 + 隐含影响 + 冲突）
```

## 安装

```
/plugins install grill-me-only@aipm-tools
```

## 使用示例

```
你：我在想要不要把后台从 monorepo 拆成多 repo, grill me

→ Skill 启动 Phase 0：先确认 Subject = "后台拆分决策"，Goal、Constraints、
  现状各一句话。
→ Phase 1 画出顶层分支：[拆分动机 / 边界依据 / 共享代码策略 /
  CI 与发布 / 团队协作 / 回滚成本]，让你确认。
→ Phase 2 一题一题走，每题都带推荐答案：
   Q1.1 拆分的真实驱动是什么？
   - A) 团队规模冲突   - B) 部署独立性   - C) 编译速度
   Recommended: A   Why: 你提到团队从 6 人涨到 18 人, 编译/部署还行
→ ……
→ Phase 4 输出 Decision Record，列出全部决策、推迟项、隐含影响。
```

## 它**不**做的事

| 想要的 | 用这个 skill |
|--------|--------------|
| 写 PRD | `write-prd` / `create-prd` |
| 从样本反推规则 | `ssot-prompt-engineer` |
| 审已有计划 | `plan-reflection` |
| 拆 sprint | `sprint-plan` / `sprint` |
| 写代码 | 直接让 Claude Code 写 |

`grill-me-only` 永远只产出 Decision Record。要继续往下推进，把这份记录喂给上面的对应 skill 即可。

## 设计原则（写给好奇怎么改它的人）

1. **One question per turn** — 每回合只问一个问题，复合问题立刻拆。
2. **Always recommend** — 没法推荐 = 没问明白，先 reframe。
3. **Dependency-first** — A 决定 B 时，B 不许先问。
4. **Reshape on answer** — 上游答案改了 → 下游子树重画 → 用户确认 → 再走。
5. **Grill only** — 不写、不画、不实现，只问 + 只记。
6. **User can stop anytime** — `stop` / `够了` / `enough` 立刻跳到 Phase 4。

## 版本

- v0.1.0 (2026-05-08) — 首个版本
