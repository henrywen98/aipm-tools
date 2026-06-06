# AIPM Tools Marketplace

> Version: v0.19.0 (2026-06-06)

Personal Claude Code plugin marketplace (`henrywen98/aipm-tools`).

## Project Structure

```
aipm-tools/
├── .claude-plugin/marketplace.json   # Marketplace registry (plugin list)
├── plugins/<name>/                   # Each plugin is self-contained
│   ├── .claude-plugin/plugin.json    # Plugin manifest
│   ├── README.md                     # Chinese documentation
│   ├── skills/                       # Auto-discovered skills
│   ├── commands/                     # Auto-discovered commands
│   ├── agents/                       # Auto-discovered agents
│   └── hooks/                        # Auto-discovered hooks
├── docs/plans/                       # Design & implementation docs
└── README.md                         # Marketplace overview (Chinese)
```

## Plugin Manifest Rules (plugin.json)

**Critical:** All plugins use **auto-discovery** for components. Do NOT add explicit path arrays like `"skills": [...]` or `"commands": [...]` to plugin.json — this causes validation errors (e.g. `skills: Invalid input`).

Correct plugin.json format:
```json
{
  "name": "plugin-name",
  "version": "1.0.0",
  "description": "Plugin description"
}
```

Optional fields: `author`, `homepage`, `repository`, `license`, `keywords`.

Auto-discovery scans these directories automatically:
- `skills/` — Skill .md files
- `commands/` — Command .md files
- `agents/` — Agent .md files
- `hooks/` — hooks.json

## Known Issues

None currently.

## Adding a New Plugin

1. Create `plugins/<name>/` directory
2. Create `plugins/<name>/.claude-plugin/plugin.json` with name, version, description only
3. Place components in standard directories (`skills/`, `commands/`, etc.)
4. Create `plugins/<name>/README.md` in Chinese
5. Add entry to `.claude-plugin/marketplace.json` plugins array
6. Update root `README.md` plugin table

## Skill File Conventions

All plugins use the **nested pattern**: `skills/<name>/SKILL.md`

Auto-discovery only scans this pattern. Do NOT use flat files like `skills/<name>.md` — they won't be discovered.

## Plugin Categories

Categories are recorded as the `category` field on each plugin in `.claude-plugin/marketplace.json` (English keys; SSOT). Root `README.md` section titles mirror these keys 1:1. 17 plugins / 7 categories:

| Category (key) | README 中文标题 | Plugins |
|----------------|-----------------|---------|
| Requirements & Workflow | 需求与文档工作流 | ai-pm-feedback-collector, code-to-prd, req-to-issues, doc-feature-extractor |
| Document Processing | 写作与文稿处理 | read-digest, fair-copy |
| Efficiency | 效率工具 | meeting-prep, weekly-report |
| Visualization | 可视化 | drawio-diagram |
| Dev Tools | 开发工具 | ssot-prompt-engineer, plan-reflection, docker-dev, cicd-dev, vue-form-to-json, grill-me-only |
| HR | 招聘与 HR | interviewer-assistant |
| Infra | 部署运维 | vpn-deploy |

When adding a plugin, set its `category` to one of these keys (or introduce a new one consistently across marketplace.json + README + this table).

## Versioning

使用 semver (`vMAJOR.MINOR.PATCH`)，每次 push 后更新 CLAUDE.md 顶部的 Version 行：
- **PATCH**: bug fix, docs update
- **MINOR**: 新增插件、新功能
- **MAJOR**: 破坏性变更（marketplace 结构调整等）

格式：`> Version: vX.Y.Z (YYYY-MM-DD)`

## Conventions

- All plugin README.md files are in **Chinese**
- Plugin names use **kebab-case**
- Marketplace registry: `.claude-plugin/marketplace.json`
- Each plugin is self-contained and independently installable
- Do not put `owner` info in individual plugin.json, only in marketplace.json
