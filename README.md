# 日 / 周计划工具 · daily-week-plan

浏览器里用的**日计划 + 周计划**本地工具：把成功人士方法里可复用的结构（MIT、时间块、护栏、复盘关机、主题日等）收成可填写模板。

- **无安装、无后端、无账号**  
- 数据只在本机浏览器 `localStorage`（按日期 / 按周分档）  
- **不填姓名身份**，只写计划  

主文件：`daily-plan-template.html`（部署后站点根路径即打开该工具）

---

## 功能概览

| 模块 | 说明 |
|---|---|
| **日计划** | 意图、MIT、时间块、护栏、可选晨间/健康、复盘、关机 |
| **MIT** | 默认 3 条，最多 6；#1 = 今日一件大事；勾选完成 |
| **→ 明日** | 未完成要事写入明日清单（**不改日期**） |
| **开启新的一天** | 日期 +1，明日 MIT 成为新一天 MIT（真换日） |
| **护栏** | 今天不做 · 延后 · 委派 · 杂念捕获 |
| **关机** | 四步清单 + 总确认（双向联动） |
| **计划审查** | 实时检查：通过 / 待改进 / 跳过 |
| **周计划** | 主题日、成功标准、周复盘；可套用到今日 |
| **导出** | 打印 / 复制 / Markdown / TXT |
| **主题** | 跟随系统 / 浅色 / 深色 |

方法参考：Ivy Lee、时间块（Newport）、富兰克林晨晚、非待办、GTD 捕捉与周回顾等（抽象模块，不抄作息表）。

---

## 本地使用

1. 用浏览器打开 `daily-plan-template.html`  
2. 写 **MIT** → **时间块** → **护栏**  
3. 日终：勾选完成 → **→ 明日** → 复盘 → **关机**  
4. **开启新的一天** 进入下一天  
5. 顶栏切换 **周** 维护主题日；需要时点「套用到今日」  

> 「示例」可一键填演示数据；「清空」只清本日、保留周计划。

---

## 部署到 Netlify

仓库已含 `netlify.toml`：

1. [Netlify](https://app.netlify.com) → **Add new site** → 导入本 Git 仓库  
2. 构建设置自动读取配置：  
   - Build：用 Node 将主 HTML 复制为 `dist/index.html`  
   - Publish：`dist`  
3. 部署完成后访问站点**根路径**即可  

说明：

- 无环境变量、无服务端  
- 只发布工具页，不把 `docs/`、`.grok/` 等推到公网  
- 本地草稿：`netlify deploy --build`；生产：`netlify deploy --build --prod`  

---

## 目录结构

```
daily-week-plan/
├── daily-plan-template.html   # 主工具（单文件）
├── netlify.toml               # Netlify 部署
├── AGENTS.md                  # 项目硬约束（协作 / AI）
├── README.md
├── docs/                      # 需求沉淀、审查、方法研究
├── prompts/                   # 可复制提示词
└── .grok/skills/              # 产品 / UI / 教训 skill
```

| 路径 | 说明 |
|---|---|
| `docs/对话沉淀-需求与教训.md` | 需求与踩坑 |
| `docs/产品业务与代码审查.md` | 业务与代码审查 |
| `docs/成功人士计划研究与审查.md` | 方法研究 |
| `docs/日计划模板-实现说明.md` | 字段与实现 |
| `docs/UX精简说明.md` | 界面去多余说明 |
| `prompts/` | 基线需求、回归清单、审查提示词等 |
| `.grok/skills/` | `make-plan-product` / `ui` / `lessons` |

---

## 协作与提示词

改功能时请遵守 `AGENTS.md`（日切语义、mock 边界、存档规则、去 AI 视觉等）。

常用提示词：

- `prompts/产品需求-基线.md`  
- `prompts/回归验收清单.md`  
- `prompts/审查产品业务与代码.md`  

---

## 技术说明

- 纯静态 HTML/CSS/JS，无构建依赖（Netlify 构建仅复制文件）  
- 状态：`localStorage` 分档 `daily-plan-day-v2:*` / `daily-plan-week-v2:*`  
- 预览与导出共用 `buildPlanView`  

---

## License

未单独声明许可证时，仅供个人学习与使用；若需开源协议可后续补充。
