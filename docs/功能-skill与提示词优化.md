# 功能：根据对话优化 skill 与提示词

日期：2026-07-18  

## 动机

把近期对话中的**用户需求、踩坑、解法**写回可复用入口，避免下轮 AI 又：

- 清空强制回今天误伤存档  
- weekFocus 只修存盘不修表单  
- 事项用 textarea、预览/MD 不一致  
- 恢复「关机全勾联动」或难词文案  

## 更新清单

| 路径 | 变更要点 |
|---|---|
| `docs/对话沉淀-需求与教训.md` | 补易懂/必做/条目列表/睡觉仪式/清空 A/P0 表单门闩；错误表 #11b–39；用户原话表 |
| `.grok/skills/make-plan-product/SKILL.md` | 清空 A、表单门闩、必做模块、睡觉仪式、条目列表、白话、同步清单 |
| `.grok/skills/make-plan-lessons/SKILL.md` | 高危旧坑表；回归含清空非今天、表单互写、条目列表、睡觉仪式 |
| `.grok/skills/make-plan-ui/SKILL.md` | 白话、条目列表交互、睡觉仪式两列、必做标记 |
| `AGENTS.md` | 与上对齐的硬约束全文 |
| `prompts/产品需求-基线.md` | 同步 16 条必须遵守 |
| `prompts/审查产品业务与代码.md` | P0 检查项（表单门闩/清空 A/weekStrip） |
| `prompts/回归验收清单.md` | 必做、条目、睡觉、清空非今天 |
| `prompts/继续研究成功人士计划并完善.md` | 历史坑检查 |
| `prompts/去AI化视觉.md` | 并入白话文案 |

## 使用方式

| 场景 | 用什么 |
|---|---|
| 改业务 | `make-plan-product` + `AGENTS.md` |
| 修 bug / 回归 | `make-plan-lessons` + `prompts/回归验收清单.md` |
| 改样式文案 | `make-plan-ui` + `prompts/去AI化视觉.md` |
| 全面审查 | `prompts/审查产品业务与代码.md` |
| 方法研究增强 | `prompts/继续研究成功人士计划并完善.md` |
| 新会话约束 | `prompts/产品需求-基线.md` |

## 原则

行为一变 → 代码 + 功能 docs + skill/prompts 同步；只改代码不改 skill = 下轮必复发。  
