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

### 需求与文档工作流

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| ai-pm-feedback-collector | PM碎片信息收集与洞察整理（JTBD + Opportunity Score + 情感分析） | `/plugins install ai-pm-feedback-collector@aipm-tools` |
| purvar-prd | 璞华PRD工作流：/purvar.prd 生成PRD、/purvar.confirm 生成需求确认单、/purvar.clarify 澄清PRD + confirm-to-docx 一键 md→Word | `/plugins install purvar-prd@aipm-tools` |
| purvar-hld | 璞华概要设计说明书：组装7章概设 + Markdown→Word 转换 | `/plugins install purvar-hld@aipm-tools` |
| doc-feature-extractor | 异构业务文档（PRD .docx / 解决方案 .docx / 报价 .xlsx）抽功能模块到带样式的 Excel：3 种输入模式 + 重跑保留橙色评估手填列（复用度 / 成熟度 / 已应用项目 / 维护责任人 / 备注） | `/plugins install doc-feature-extractor@aipm-tools` |

### 测试

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| test-case-generator | 从需求文档生成结构化测试用例 + Excel | `/plugins install test-case-generator@aipm-tools` |
| comprehensive-test-generation | 全面测试生成策略（E2E/API/Unit） | `/plugins install comprehensive-test-generation@aipm-tools` |

### 效率工具

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| meeting-prep | 会议准备工具，6 问生成完整会前文档 | `/plugins install meeting-prep@aipm-tools` |
| weekly-report | 周报生成工具，从聊天记录自动生成会议周报 | `/plugins install weekly-report@aipm-tools` |

### 可视化

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| drawio-diagram | Draw.io 图表生成器：流程图、架构图、系统拓扑图、业务流程全景图 | `/plugins install drawio-diagram@aipm-tools` |

### 开发工具

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| ssot-prompt-engineer | SSOT 规则提取器：从成品文档反向提取生成规则，输出 Skill Blueprint 供 skill-creator 消费 | `/plugins install ssot-prompt-engineer@aipm-tools` |
| req-to-issues | 需求分析拆解工具：将需求素材分析拆解为 GitHub/GitLab Issue 并批量上传 | `/plugins install req-to-issues@aipm-tools` |
| plan-reflection | 多 Agent 计划反思循环：独立 Reviewer 找 blocking issues + 独立 Corrector 修正，最多 3 轮 | `/plugins install plan-reflection@aipm-tools` |
| docker-dev | Docker 开发助手：Dockerfile 优化、compose 编排、多阶段构建、容器安全审计 | `/plugins install docker-dev@aipm-tools` |
| cicd-dev | CI/CD 流水线生成器：自动检测技术栈并生成 GitHub Actions / GitLab CI 流水线 | `/plugins install cicd-dev@aipm-tools` |
| vue-form-to-json | Vue 2 + Element UI 表单提取为 JSON 动态配置数组 | `/plugins install vue-form-to-json@aipm-tools` |
| code-to-prd | 从现有代码库逆向生成 PRD：扫描路由/组件/API/交互，产出每页每接口的业务文档（支持 React/Vue/Angular/Next.js、NestJS/Django/Express/FastAPI 及全栈）。移植自 alirezarezvani/claude-skills (MIT) | `/plugins install code-to-prd@aipm-tools` |
| grill-me-only | 决策树拷问 skill：把方案/设计/决策按分支深度优先一题一题问你，附推荐答案 + 一句 why，自动处理依赖，最终输出 Decision Record。只 grill，不写文档/代码/图 | `/plugins install grill-me-only@aipm-tools` |

### 招聘与 HR

| 插件 | 说明 | 安装命令 |
|------|------|----------|
| interviewer-assistant | 面试官助手：pre-interview 从简历生成针对性面试题 + 识别包装痕迹；post-interview 对照会议纪要做四维评估 | `/plugins install interviewer-assistant@aipm-tools` |

## 说明

- 大部分插件为自建 skills
- 每个插件目录下都有中文 README.md，详细说明用途和使用方式
- 欢迎团队成员订阅使用
