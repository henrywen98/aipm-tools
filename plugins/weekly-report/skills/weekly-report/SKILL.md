---
name: weekly-report
description: 周报生成。本插件已并入 claude-memory skill (用户级)，触发周报生成时请使用 claude-memory。本 skill 保留作为兼容入口：当用户说"周报"、"weekly report"、"上周/本周报告"时，引导到 claude-memory 的周报渲染流程。
---

# Weekly Report — 已迁移至 claude-memory

本 skill 的功能（从 Claude Code 历史生成中文周报）已迁移到 **`claude-memory`** 用户级 skill 的"周报渲染"流程。新版改进：

- **持久化分析层**：每个 session 分析一次，多次报告复用，准确度可控（业务描述、项目去重、不漏小项目）
- **统一数据底座**：周/月/季报、简历、项目深挖共用同一套 per-session JSON
- **借鉴 /insights 设计**：`outcome` / `friction` / `big_wins` 等结构化字段
- **mirror 兜底**：跑历史区间不再因 Claude Code cleanup 漏 session

## 触发时如何处理

如果用户调用了本 skill（例如说"周报"、"weekly report"），转交给 `claude-memory`：

> 周报生成功能已并入 `claude-memory` skill（数据布局更清晰、分析持久化、可复用到月报/简历）。我现在用 claude-memory 来生成周报。

然后调用 `claude-memory` skill，按其 SKILL.md 中 "Decision tree → B) Weekly / monthly / quarterly report" 的流程走：

1. 解析时间范围
2. `list_pending.py --since X --until Y` 检查分析层是否齐全
3. 如有 pending，dispatch subagents 跑分析
4. `aggregate.py week <key>` 生成周聚合
5. 主 Claude 跑 dedup / big_wins / friction_patterns 提取
6. 按 `references/render-weekly.md` 模板生成 md，写到 `~/Documents/2_Area/000000_claude_brain/artifacts/weekly/`

详细路径：`~/.claude/skills/claude-memory/SKILL.md`

## 历史输出位置

旧版周报存档迁移到了：
```
~/Documents/2_Area/000000_claude_brain/artifacts/weekly/
├── 周报_2026-03-23_2026-03-29.md
├── 周报_2026-03-30_2026-04-07.md
└── _intermediate/   (Wave 3 中间产物)
```

旧的 `~/Documents/2_Area/000001_weekly_report/` 已变成 symlink，指向上面的 `artifacts/weekly/`，老引用不会断。

## 为什么废弃这个插件？

旧 weekly-report 用三波多 Agent 现场分析，重复了 claude-memory 的索引能力，且：
- 业务描述拼凑（每次 Agent 现场猜，不一致）
- 项目去重错（无稳定 canonical_id 映射）
- 漏小项目（Agent 倾向忽略 message 数少的 session）
- 读不到 30 天前的 session（直接读 `~/.claude/projects/`，不走 mirror）

新架构都解决了。本插件保留是为了让"`/weekly-report`"老命令还能触发到正确的入口。
