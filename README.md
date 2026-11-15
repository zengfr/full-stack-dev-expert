# full-stack-dev-expert

全栈编程开发专家技能包：以**一个总指挥 + 14 个子角色**的开发团队模式组织的 agent/subagent 协作技能。
总指挥不写业务代码，只做接收需求、分诊路由、调度子角色、把控质量门禁四件事；
专业产出全部由子角色完成，角色间通过**交接单**传递上下文；
全体角色的一切决策遵循**《软件工程宪法》**（最高工程原则，冲突时以宪法为准）。

## 团队模型

```
              ┌──────────── 总指挥（SKILL.md） ────────────┐
              │ 分诊路由 · 调度 · 质量门禁 · 宪法守护        │
              └───────────────────┬────────────────────────┘
    ┌─────────┬─────────┬─────────┼─────────┬─────────┬─────────┐
  需求分析师   架构师    UI/UX设计师  数据库工程师  测试工程师  安全工程师
    └────┬────┴────┬────┴────┬────┴────┬────┴────┬────┴────┬────┘
       前端工程师   后端工程师          管理后台前端   管理后台后端
       （C 端域）   （通用域）          （管理后台任务时替换上两者）
                          逆向融合工程师（ORRI：观察→逆向→重建→创新）
                          代码审查员 · DevOps 工程师 · 技术文档工程师
```

**主流程**：① 需求澄清 → ② 架构设计 → ③ 并行实现 → ④ 质量保障 → ⑤ 交付部署 → ⑥ 文档归档
（按任务类型裁剪，路由表见 `references/orchestration.md`）

**管理后台路由**：任务命中"管理后台/中后台/admin/运营平台/控制台"时，管理域实现由
管理后台前后端两位专才**替换**通用前后端工程师（RBAC、审计、CRUD 三件套、权限路由）。

**逆向融合路由**：任务指向外部/未知系统的能力、协议、架构或 UI 提取融合时，先经
**逆向融合工程师**按 ORRI 方法论完成观察与逆向，再按场景子路由移交下游；合法性门禁
不通过立即终止（融合竞品能力、提取协议格式、重构摸底、未知代码库学习、UI/架构复刻）。

**执行模式**：A · Task subagent 委派（宿主支持子代理时）／ B · 上下文内换装（Read 角色文件后按契约履职）。
两种模式角色契约完全一致。

## 技术栈覆盖

| 层 | 支持栈（规范文件见 references/standards/） |
|---|---|
| 后端 | Java 17 / Spring Boot 3 · Java 17 / Quarkus 3（云原生/Serverless/native）· Node 20 / NestJS · Python 3.11 / FastAPI · Go 1.22+ |
| ORM | JPA / Hibernate（Spring 与 Quarkus 共用纪律）· TypeORM/Prisma · SQLAlchemy |
| 前端框架 | React 18 · Vue 3.4 · Next.js 14+/15（SSR/SSG/ISR）· HarmonyOS ArkTS（契约衔接） |
| UI 组件层 | Ant Design 5（管理后台默认）· Tailwind CSS 3.4 + shadcn/ui（C 端定制，与 antd 二选一不混用） |
| API 风格 | REST（默认）· GraphQL（ADR 门槛立项：DataLoader/复杂度限制/持久化查询三件套强制） |
| 数据 | MySQL 8 · PostgreSQL 16 · SQLite · Redis 7 · 迁移（Flyway/Liquibase/版本化脚本） |

## 目录结构

```
full-stack-dev-expert/
├── SKILL.md                       # 总指挥：调度中心（入口）
├── agents/                        # 14 个子角色定义
│   ├── requirements-analyst.md    #   需求分析师
│   ├── architect.md               #   架构师
│   ├── ui-ux-designer.md          #   UI/UX 设计师
│   ├── dba.md                     #   数据库工程师
│   ├── frontend-dev.md            #   前端开发工程师（C 端域）
│   ├── backend-dev.md             #   后端开发工程师（通用域）
│   ├── admin-frontend-dev.md      #   管理后台前端工程师（antd 布局/权限路由/CRUD 三件套）
│   ├── admin-backend-dev.md       #   管理后台后端工程师（RBAC/审计/列表导入导出 API）
│   ├── reverse-fusion-dev.md      #   逆向融合工程师（ORRI：观察→逆向→重建→创新）
│   ├── test-engineer.md           #   测试工程师
│   ├── security-engineer.md       #   安全工程师
│   ├── code-reviewer.md           #   代码审查员
│   ├── devops-engineer.md         #   DevOps 工程师
│   └── tech-writer.md               #   技术文档工程师（README/API/arc42+C4+ADR/专业文档集/业务流程与时序/Runbook/CHANGELOG/部署文档）
├── references/
│   ├── constitution.md            # 软件工程宪法（最高效力，全体角色必读）
│   ├── orchestration.md           # 调度协议：路由表、管理后台路由、裁剪、并行、门禁、失败处理
│   ├── stack-routing.md           # 技术栈路由：栈指纹、选型决策树、UI 层选型
│   ├── collaboration.md           # 协作协议：交接单、冲突仲裁、落盘约定
│   ├── ui-patterns/               # 5 类站点类型 UI 模式（UI/UX 设计师路由加载）
│   │   ├── corporate-site.md      #   企业官网（留资转化/案例/信任背书）
│   │   ├── product-site.md        #   产品官网（转化漏斗/定价页/注册下载）
│   │   ├── open-source-site.md    #   开源项目官网（快速上手/文档/暗色模式）
│   │   ├── ecommerce.md           #   电商商城（商详 IA/下单漏斗/信任合规）
│   │   └── admin-console.md       #   后台管理（列表页模式/查改流/防误操作）
│   ├── self-evolution.md          # 技能自进化协议（提示词触发/轮次参数/五步循环/保护门禁）
│   └── standards/                 # 14 份多栈编码规范
│       ├── api-design.md          #   REST API 设计（契约唯一依据）
│       ├── api-graphql.md         #   GraphQL（ADR 门槛 + DataLoader/复杂度/持久化查询）
│       ├── database.md            #   数据库建模与迁移纪律
│       ├── backend-java-spring.md #   Java / Spring Boot
│       ├── backend-quarkus.md     #   Java / Quarkus（云原生/Serverless）
│       ├── backend-jpa-hibernate.md #  JPA/Hibernate（Java 栈共用 ORM 纪律）
│       ├── backend-node-nestjs.md #   Node / NestJS
│       ├── backend-python-fastapi.md # Python / FastAPI
│       ├── backend-golang.md      #   Go（错误处理/并发/context 纪律）
│       ├── frontend-react.md      #   React
│       ├── frontend-vue3.md       #   Vue 3
│       ├── frontend-nextjs.md     #   Next.js App Router（Server/Client 纪律）
│       ├── frontend-antd.md       #   Ant Design 5（管理后台 UI）
│       └── frontend-tailwind-shadcn.md # Tailwind CSS + shadcn/ui
├── templates/                     # 21 个交付物模板
│   ├── handoff-ticket.md          #   交接单（角色间唯一传递载体）
│   ├── requirements-spec.md       #   需求规格
│   ├── prd.md                     #   产品需求文档（真值源 requirements-spec）
│   ├── user-stories.md            #   用户故事与用例（故事地图 + 追踪矩阵）
│   ├── architecture-design.md    #   架构设计 + ADR 索引
│   ├── arc42-doc.md               #   架构文档（arc42 12 章 + C4 分层图 + ADR 索引）
│   ├── adr.md                     #   ADR 分离档案（一个决策一个文件，Nygard 格式）
│   ├── ddd-design.md              #   领域设计与数据合同（限界上下文 → 模型 → 合同）
│   ├── dev-standards.md           #   仓库结构与开发规范（含 monorepo 判定规则）
│   ├── roadmap.md                 #   实施路线与里程碑（出口条件可验证）
│   ├── business-process.md        #   业务流程与时序文档（流程图 + 时序图 + 追踪矩阵）
│   ├── api-contract.md            #   API 契约
│   ├── ui-spec.md                 #   UI/UX 规格
│   ├── reverse-analysis.md        #   逆向分析报告（ORRI：证据档案/置信度/等价性测试）
│   ├── test-plan.md               #   测试计划
│   ├── test-report.md             #   测试报告
│   ├── deploy-guide.md            #   部署指南
│   ├── runbook.md                 #   运维手册（告警响应/故障处置/应急预案）
│   ├── changelog.md               #   变更日志（Keep a Changelog，项目根）
│   ├── pr-summary.md              #   交付摘要
│   └── evolution-report.md        #   技能自进化报告（会话参数/逐轮评审表/汇总/下轮建议）
├── knowledge/                     # 经验知识库（L3 正反参考池，写入只经自进化协议）
│   ├── README.md                  #   KB 治理：分级/条目格式/准入/升级/退出
│   └── lessons.md                 #   任务沉淀与评审发现（KB 条目 + 提案池）
├── evals/evals.json               # 22 个验收用例
└── FILES.md                       # 文件清单
```

## 使用方式

- **OpenCode / Claude Code 类宿主**：将本目录复制到技能目录
  （如 `~/.local/share/opencode/skills/full-stack-dev-expert/`），由 SKILL.md 的
  description 触发加载；总指挥按宿主能力自动选择执行模式 A 或 B。
- **直接投喂**：将 SKILL.md 作为入口 prompt，按其指引 Read 对应角色与协议文件。

## 设计要点

- **技能自进化**：提示词触发（`自进化 N轮 焦点=<域> 模式=<评审|沉淀|横向|纵向>`），
  按轮次执行 探测→提案→自我评审→落盘→报告 五步循环；知识分级（L1 强制/L2 推荐/L3 参考）
  与来源准入（无来源进提案池待验证，不发明知识）；经验知识库 `knowledge/` 沉淀正反参考
  （L3 被 ≥3 任务验证后升级 L2 并评估合入规范层）；宪法与 evals 变更须用户显式批准，
  评审清单 7 项硬门禁 + 1 项软门禁（单一真值源/引用闭环/evals 回归/版本纪律）保证进化不劣化。
- **站点类型模式路由**：UI/UX 设计师开工先判定站点类型（企业官网/产品官网/开源项目
  官网/电商商城/后台管理），加载 `references/ui-patterns/` 对应模式展开类型专属
  页面 IA、核心交互流失败分支与反模式自查；混合站点逐端判定，未命中类型用通用骨架
  + 最接近模式参照并回报确认——不同类型 UI/UX 差异不靠临场发挥。
- **宪法至上**：`references/constitution.md` 定义 29 条工程宪法与冲突优先级
  （正确性与数据安全 > 安全 > 契约与诚实 > 简单 > 交付速度），效力高于一切协议文件。
- **管理后台专才路由**：admin-frontend-dev / admin-backend-dev 替换通用前后端工程师，
  内置 RBAC、审计日志、CRUD 三件套、权限路由等管理域模式；管理端任务安全工程师强制启用。
- **逆向融合（ORRI）**：reverse-fusion-dev 以 观察→逆向→重建→创新 四阶段提取外部系统
  核心设计并融合，六类场景（竞品能力/协议格式/重构摸底/未知代码库/UI 复刻/架构复刻）
  各有子路由；观察零推测、结论挂证据与置信度、净室纪律、合法性门禁前置、等价性测试门禁。
- **契约先行**：架构阶段先出 API 契约草案，前端 Mock、后端实现、测试验证三方共用一份契约。
- **文档工程**：架构文档集（arc42 + C4 + ADR 分离档案）与专业文档集
  （PRD/用户故事与用例/领域设计/开发规范/路线图/业务流程与时序）每份单一真值源，
  技术文档工程师只转译不发明决策；INDEX.md 承担文档治理（类型/归属/更新触发/真值源映射/风险登记）。
- **交接单唯一真值源**：跨阶段只认交接单与产出物，不认"我以为"；用户原话全程逐字透传。
- **质量门禁**：每阶段有明确退出条件；同一阶段最多打回 2 次，第 3 次如实上报分歧。
- **安全一票否决**：仅限高危及以上，否决必须附带修复建议与工作量评估。
- **选型有据**：延续既有栈优先；Quarkus/GraphQL/shadcn 切换均设 ADR 门槛，不为新而新；
  任何新增依赖必须在 ADR 登记。

## 版本

版本号唯一来源：`SKILL.md` metadata；变更历史不落包内文件，`git log` 即变更记录
（提交信息含版本箭头与逐轮采纳/未采纳清单）。
