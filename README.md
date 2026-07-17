# AIPM Tools

Henry 的个人 Claude Code 插件市场，统一管理自建 skills 和常用插件，支持按需安装和团队共享。

## 快速开始

### 订阅 Marketplace

在 Claude Code 中执行：

```
/plugins → Discover → Add marketplace → github:henrywen98/aipm-tools
```

### 按需安装插件

```
/plugins install <插件名>@aipm-tools
```

## 插件列表

> 共 17 个插件，分 7 类。`category` 字段记录在 `.claude-plugin/marketplace.json`，以下小标题与之一一对应。

### 需求与文档工作流（Requirements & Workflow）

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| ai-pm-feedback-collector | PM碎片信息收集与洞察整理（JTBD + Opportunity Score + 情感分析） | `/plugins install ai-pm-feedback-collector@aipm-tools` |
| code-to-prd | 从现有代码库逆向生成 PRD：扫描路由/组件/API/交互，产出每页每接口的业务文档（支持 React/Vue/Angular/Next.js、NestJS/Django/Express/FastAPI 及全栈）。移植自 alirezarezvani/claude-skills (MIT) | `/plugins install code-to-prd@aipm-tools` |
| doc-feature-extractor | 异构业务文档（PRD .docx / 解决方案 .docx / 报价 .xlsx）抽功能模块到带样式的 Excel：3 种输入模式 + 重跑保留橙色评估手填列（复用度 / 成熟度 / 已应用项目 / 维护责任人 / 备注） | `/plugins install doc-feature-extractor@aipm-tools` |

### 写作与文稿处理（Document Processing）

> 两件互补的处理，一条分界：**input 侧 vs output 侧**。read-digest 管 input（读懂别人/AI 丢来的臃肿稿）；humanizer 管 output（把自己手上、尤其 AI 写的稿，清成人能读懂的成品）。原 fair-copy 已并入 humanizer——本质上「去 AI 味 / 去翻译腔 / 清成交付版」是同一件事。

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| read-digest | 把别人或 AI 丢来、读着臃肿的稿先抽成「一句话一段」的反向大纲骨架，让重复 / 跑题 / 断层 / 头重脚轻等结构病现形；再按需读懂即停、逐段下具体指令、或照骨架重写干净精简稿（引擎是 reverse outline，区别于 summary） | `/plugins install read-digest@aipm-tools` |
| humanizer | 把 AI 写的、一读就不像人写的文字，改成真人为读者写的、一读就懂的稿。三层：① 机器发声（去 AI 味 + 去翻译腔：拔高升华 / 三段排比 / 黑话 / 破折号滥用 / 名词化 / 长句 / 一句三个「的」/ 套话词）② 读者读不懂（行话换白话 / 说清指代 / 术语统一 / 结构摆顺）③ 过程噪音（修订史 / 批注 / 备选）。判准是冷读测试，靠 cluster 判断不见词就改，去味之余保人味。v2.0 并入原 fair-copy。译改自 blader/humanizer (MIT) | `/plugins install humanizer@aipm-tools` |
| ~~fair-copy~~ | **已并入 humanizer（2026-07-17）**，仅保留作重定向 | — |

### 效率工具（Efficiency）

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| meeting-prep | 会议准备工具，6 问生成完整会前文档 | `/plugins install meeting-prep@aipm-tools` |
| weekly-report | 周报生成工具，从聊天记录自动生成会议周报 | `/plugins install weekly-report@aipm-tools` |

### 可视化（Visualization）

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| drawio-diagram | Draw.io 图表生成器：流程图、架构图、系统拓扑图、业务流程全景图 | `/plugins install drawio-diagram@aipm-tools` |

### 开发工具（Dev Tools）

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| ssot-prompt-engineer | SSOT 规则提取器：从成品文档反向提取生成规则，输出 Skill Blueprint 供 skill-creator 消费 | `/plugins install ssot-prompt-engineer@aipm-tools` |
| plan-reflection | 多 Agent 计划反思循环：独立 Reviewer 找 blocking issues + 独立 Corrector 修正，最多 3 轮 | `/plugins install plan-reflection@aipm-tools` |
| docker-dev | Docker 开发助手：Dockerfile 优化、compose 编排、多阶段构建、容器安全审计 | `/plugins install docker-dev@aipm-tools` |
| cicd-dev | CI/CD 流水线生成器：自动检测技术栈并生成 GitHub Actions / GitLab CI 流水线 | `/plugins install cicd-dev@aipm-tools` |
| vue-form-to-json | Vue 2 + Element UI 表单提取为 JSON 动态配置数组 | `/plugins install vue-form-to-json@aipm-tools` |
| grill-me-only | 决策树拷问 skill：把方案/设计/决策按分支深度优先一题一题问你，附推荐答案 + 一句 why，自动处理依赖，最终输出 Decision Record。只 grill，不写文档/代码/图 | `/plugins install grill-me-only@aipm-tools` |

### 招聘与 HR（HR）

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| interviewer-assistant | 面试官助手：pre-interview 从简历生成针对性面试题 + 识别包装痕迹；post-interview 对照会议纪要做四维评估 | `/plugins install interviewer-assistant@aipm-tools` |

### 部署运维（Infra）

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| vpn-deploy | AI 一键部署自建 VPN（VLESS + XHTTP + TLS + Cloudflare CDN）：VPS 上自动化搭建 3X-UI + Xray + Nginx + 伪装站，附故障诊断 / 加用户 / 证书续期等运维能力 | `/plugins install vpn-deploy@aipm-tools` |

## 说明

- 大部分插件为自建 skills
- 每个插件目录下都有中文 README.md，详细说明用途和使用方式
- 欢迎团队成员订阅使用
