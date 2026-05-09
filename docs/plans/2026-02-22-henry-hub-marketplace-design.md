# AIPM Tools Marketplace 设计文档

## 概述

创建一个个人 Claude Code 插件 marketplace（`henrywen98/aipm-tools`），将分散在多个位置的自建 skills 和插件统一管理，支持按需安装和团队共享。

## 仓库信息

- GitHub: `henrywen98/aipm-tools`
- 用途: 个人 + 团队共享的 Claude Code 插件市场

## 插件清单（15个）

| # | 插件名 | 来源 | 类型 |
|---|--------|------|------|
| 1 | doc-coauthoring | `~/.claude/skills/` | skill |
| 2 | docx | `~/.claude/skills/` | skill + 脚本 + schema |
| 3 | pdf | `~/.claude/skills/` | skill + 脚本 |
| 4 | pptx | `~/.claude/skills/` | skill + schema |
| 5 | ssot-prompt-engineer | `~/.claude/skills/` | skill |
| 6 | xlsx | `~/.claude/skills/` | skill |
| 7 | batch-commit | `~/.claude/plugins/` | commands + refs |
| 8 | test-case-generator | `~/.claude/plugins/` | skill + 脚本 |
| 9 | comprehensive-test-generation | `~/dev/skills-marketplace/` | skill + examples + refs |
| 10 | prd-workflow | `~/dev/skills-marketplace/` zip | commands + scripts |
| 11 | gen-requirement-doc | `~/dev/skills-marketplace/` zip | skill |
| 12 | ai-pm-feedback-collector | SSH henry OpenClaw | skill |
| 13 | github-issue-generator | SSH henry OpenClaw | skill |
| 14 | code-simplifier | 官方 fork | agent |
| 15 | superpowers | 官方 fork | 完整插件 |

## 仓库结构

```
aipm-tools/
├── .claude-plugin/
│   └── marketplace.json
├── plugins/
│   ├── doc-coauthoring/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md              # 中文说明
│   │   └── skills/doc-coauthoring/SKILL.md
│   ├── docx/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/docx/          # SKILL.md + ooxml/ + scripts/
│   ├── pdf/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/pdf/           # SKILL.md + scripts/
│   ├── pptx/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/pptx/          # SKILL.md + ooxml/
│   ├── ssot-prompt-engineer/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/ssot-prompt-engineer/SKILL.md
│   ├── xlsx/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/xlsx/
│   ├── batch-commit/
│   │   ├── .claude-plugin/plugin.json  # 从 plugin.json 移入
│   │   ├── README.md
│   │   ├── commands/
│   │   └── references/
│   ├── test-case-generator/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   ├── skills/
│   │   ├── convert_to_xlsx.py
│   │   └── requirements.txt
│   ├── comprehensive-test-generation/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   ├── skills/comprehensive-test-generation/SKILL.md
│   │   ├── examples/
│   │   └── references/
│   ├── prd-workflow/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   ├── commands/             # prd.create.md, prd.clarify.md
│   │   ├── scripts/
│   │   └── templates/
│   ├── gen-requirement-doc/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/gen-requirement-doc/SKILL.md
│   ├── ai-pm-feedback-collector/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/ai-pm-feedback-collector/SKILL.md
│   ├── github-issue-generator/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── skills/github-issue-generator/SKILL.md
│   ├── code-simplifier/
│   │   ├── .claude-plugin/plugin.json
│   │   ├── README.md
│   │   └── agents/code-simplifier.md
│   └── superpowers/
│       ├── .claude-plugin/plugin.json
│       ├── README.md
│       ├── skills/               # 15 个 skills
│       ├── agents/
│       ├── commands/
│       ├── hooks/
│       └── ...
└── README.md                     # 仓库总说明（中文）
```

## 每个插件的 README.md 规范

每个插件目录下的中文 README.md 包含：
- 插件名称和简介
- 触发方式 / 使用场景
- 安装方式
- 使用示例

## 实施步骤

1. 在 `/Users/henry/dev/henry-marketplace` 初始化 git 仓库
2. 创建 marketplace.json
3. 逐个迁移 15 个插件（拷贝文件 + 调整目录结构）
4. 为每个插件生成中文 README.md
5. 创建仓库根 README.md
6. 提交并推送到 GitHub

## 不迁移的内容

- obsidian-notes: 个人专用
- x-ui-vpn-skill: 个人专用
- `~/.claude/skills/frontend-design`: 用户排除
