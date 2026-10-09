# 小微经营助手｜可复用 Skill 包候选清单

更新时间：2026-09-30 · 复核版 v0.2

## 一、结论先行

目前没有找到一个可以直接复制、直接上架、覆盖六大模块的“全套小微经营顾问”开源 Skill。可以复用的是成熟的 Skill 工程骨架、数据分析方法和部分业务工作流；小微经营的中文场景、确认卡、材料闸门和事实边界仍需我们自己重写。

建议采用“**底座直接复用 + 方法包改写 + 经营场景自建**”三层组合：

1. 复用内部已经验证的确认卡、开店路线和上架流程；
2. 借鉴 GitHub 上成熟的财务分析、Excel 建模、零售分析和商业提示词方法；
3. 重写成中文小微经营场景，并统一接入确认卡和材料闸门；
4. 对每个外部仓库先完成许可证核验，再决定是否保留代码或文本。

## 二、可直接复用或改写的优先候选

以下候选具备明确许可证或官方来源，优先级高于普通 Demo 项目。直接复用前仍需按仓库 LICENSE 和具体文件逐项确认。

| 优先级 | 候选 | 许可证/来源 | 适合复用什么 | 适合模块 |
|---|---|---|---|---|
| P0 | [Anthropic Agent Skills](https://github.com/anthropics/skills) 中的 `internal-comms`、`webapp-testing`、`brand-guidelines`、`canvas-design` | 仓库说明：许多示例为 Apache 2.0；每个 Skill 以自身 LICENSE 为准 | 触发条件、分步工作流、资源引用、验收和测试结构；不是经营知识本身 | 六模块通用底座、输出质量和回归 |
| P0 | [Matt Pocock Skills](https://github.com/mattpocock/skills) 中的 `grill-me`、`domain-modeling`、`research`、`writing-for-agents` | MIT（仓库级；仍需检查具体目录） | 需求澄清、领域术语、基于可信来源研究、面向 Agent 的指令写法 | 确认卡问题设计、六模块场景模型、Skill 编写 |
| P1 | [venture-analyst-skills](https://github.com/hypermari0/venture-analyst-skills) | MIT | 经营想法评估、GO / NO-GO、GTM 和验证问题 | 方向与选品 |
| P1 | [ba-project-factory](https://github.com/julijakvetna/ba-project-factory) | MIT | 结构化提问、需求拆解、验收标准和分析流程 | 方向选品、选址合规、复盘 |
| P1 | [AI Business Analyst](https://github.com/ShaerWare/ai-development-partner) | MIT | 业务顾问角色、问题诊断、计划和决策输出结构 | 六模块通用方法；需大幅删减技术/开发内容 |
| P1 | [Business Analyst Prompts](https://github.com/tmquang-dev/awesome-ba-prompts) | MIT | 结构化提示词、INVEST/Gherkin/BPMN 等表达方法 | 方向、流程、复盘；只借鉴结构 |

说明：P0/P1 表示“值得先下载审阅”，不等于已经通过 WorkBuddy 回归。每个候选都要先跑一份统一的小吃摊案例，再决定是否进入包。

## 二、内部 Skill：可以直接作为底座

| Skill 包 | 本地位置 | 可复用内容 | 对应六模块 |
|---|---|---|---|
| `jijiaxie-mcp / intent-card` | `jijiaxie-mcp-1.0.1-work/skills/intent-card` | `match_scene → get_scene_form → submit_fields → confirm_intent → compile_task → report`；确认卡、材料闸门、AI 假设标记 | 六个模块全部使用 |
| `guiputi-business-assistant` | `guiputi-skills-repo/skills/guiputi-business-assistant` | 经营形态、开店阶段、目标、动作、小场景、行动卡、跳过和节点状态 | 方向选品、选址、物料、试营业、复盘 |
| `guiputi-listing-pipeline` | `guiputi-skills-repo/skills/guiputi-listing-pipeline` | 选品、定形态、编辑页填写、回归、出包和提交流程 | 后续 Skill 上架 |

这三个是内部资产，建议直接复用规则，不复制成第三套互相冲突的流程。

## 三、业务领域候选：能提高经营质量，但需要重写

### 1. Excel Analyst Pro

- 地址：<https://github.com/jeremylongshore/excel-analyst-pro-skill-md>
- 类型：真正的 Agent Skill / Claude Skill。
- 擅长：先确认文件、单位、期间和输出路径；区分事实、来源事实、假设、公式和缺口；生成预算、预测、期间差异分析；校验公式和回算状态。
- 可借鉴：
  - 经营数据分析前先确认数据口径；
  - 把“用户事实 / AI 假设 / 计算结果 / 缺失材料”分开；
  - 成本、毛利和保本量使用可追溯公式；
  - 输出验证回执。
- 对应模块：成本与定价、复盘与复购、采购与库存。
- 复用结论：**不能直接复制**。仓库 LICENSE 明确禁止商业使用、修改和分发；只能阅读方法，除非取得书面授权。

它仍然值得作为“质量标杆”阅读，但不能作为 WorkBuddy 包依赖。

### 2. Financial Valuation & Risk Analysis Toolkit

- 地址：<https://github.com/paritoshStack/Financial-Valuation-Risk-Analysis-Toolkit>
- 类型：多个 `SKILL.md` 的财务建模方法包。
- 擅长：DCF、敏感性分析、情景分析、盈亏平衡、蒙特卡洛和风险区间。
- 可借鉴：
  - 基准 / 乐观 / 保守三种经营情景；
  - 关键变量敏感性排序；
  - 盈亏平衡和风险提示；
  - 不把单点预测写成确定结果。
- 对应模块：成本与定价、复盘与复购。
- 复用结论：**方法参考**。当前未发现明确 LICENSE 文件，不直接复制正文、公式说明或文件结构；且 DCF/LBO 对个体经营者过重，只提取“情景、敏感性、保本”三类方法。

### 3. Awesome Microsoft Copilot Prompts

- 地址：<https://github.com/kesslernity/awesome-microsoft-copilot-prompts>
- 类型：商业提示词库，不是完整 Skill 包。
- 擅长：Excel 数据故事、采购、销售、客户成功、项目管理、营销等角色化提示词。
- 可借鉴：
  - 用“角色 + 输入材料 + 输出结构 + 验收标准”写技能；
  - 把分析结论转成业务行动；
  - 对异常、趋势和下一步动作分别输出。
- 对应模块：方向选品、获客成交、复盘复购、采购库存。
- 复用结论：**可在许可证条件下改写**。仓库为 CC BY-SA 4.0，若使用其原文或实质改编，需要保留署名、链接、修改说明，并按相同许可分享改编内容。建议只借鉴结构，重新写中文场景。

### 4. Retail Revenue Intelligence

- 地址：<https://github.com/analyticsdurgesh/Retail-Revenue-Intelligence>
- 类型：零售收入分析项目，不是 Agent Skill。
- 擅长：销售数据探索、收入指标、产品分析、RFM/留存等分析思路。
- 可借鉴：
  - 销量、营业额、客单、毛利、复购的字段设计；
  - 商品 ABC 分析和客户分层；
  - 把经营记录转成“继续 / 调整 / 暂停 / 复购”判断。
- 对应模块：复盘与复购、采购与库存、成本与定价。
- 复用结论：**仅作数据模型参考**。它不是可直接安装的 Skill；未完成仓库许可证和数据来源核验前，不复制代码、图表或样例数据。

### 5. Financial Analysis of a Small Business

- 地址：<https://github.com/snehajain86196-hue/financial-analysis-small-business>
- 类型：小企业 Excel 分析练习项目。
- 擅长：整理财务数据、趋势观察、形成分析结论。
- 可借鉴：
  - 小微经营者能理解的收入、成本、利润和趋势字段；
  - Excel 输入表与结论报告的分离方式。
- 对应模块：成本与定价、复盘与复购。
- 复用结论：**只能参考字段和分析流程**。它不是 Skill，且当前未发现明确许可证，不直接复制文件和报告。

### 6. Kitchen-Math

- 地址：<https://github.com/Mou4338/Kitchen-Math>
- 类型：餐饮经营计算器项目。
- 擅长：食材成本、人工成本、综合成本、保本点、线上订单到手价、菜单工程和 ROI。
- 对应模块：成本与定价、采购与库存、复盘与复购。
- 复用结论：**暂不直接复用**。当前搜索结果未显示明确许可证；可以研究它的计算项和产品交互，但不复制代码、公式实现或界面。

### 7. Microsoft Copilot Prompt Library

- 地址：<https://github.com/kesslernity/awesome-microsoft-copilot-prompts>
- 类型：商业岗位提示词库。
- 擅长：Excel 数据故事、采购、销售、客户成功、营销和管理汇报。
- 对应模块：采购库存、获客成交、复盘复购。
- 复用结论：CC BY-SA 4.0。若复制或实质改编原文，需要署名、链接、修改说明，并按相同许可分享改编内容。商业上架包建议只学习结构、自己重写。

## 四、六大模块对应的复用方案

| 模块 | 优先复用来源 | 需要自己重写的部分 |
|---|---|---|
| 方向与选品 | Copilot 商业提示词的角色化提问、内部场景地图 | 中文经营形态、目标客群、低成本验证动作 |
| 成本与定价 | Excel Analyst Pro 的事实/假设/公式分离；财务 Toolkit 的保本和情景 | 单品成本、损耗、毛利、套餐和保本单量，不做 DCF/LBO |
| 选址与合规 | 内部 `guiputi-business-assistant` 场景地图 | 地图、人流观察、官方入口、地区规则和证照材料闸门 |
| 采购与库存 | Retail Revenue Intelligence 的商品/销量字段；Copilot 的采购提示词结构 | 供应商比价、首日备货、保质期、损耗和停止补货点 |
| 获客与成交 | 内部门店经营包；Copilot 的营销/客户成功提示词结构 | 避开已有人负责的短视频，聚焦门头菜单、开业预告、现场成交 |
| 复盘与复购 | Retail Revenue Intelligence 的 RFM/留存思路；财务 Toolkit 的情景分析 | 小摊/小店可填的每日记录、明天改一件事、复购权益和事实边界 |

## 五、其他渠道：适合找“成熟方法”，不等于可直接打包

| 渠道 | 能找到什么 | 使用口径 |
|---|---|---|
| [Agent Skills 规范与 Anthropic Skills](https://agentskills.io/) | Skill 文件结构、触发描述、引用文件、脚本和测试方式 | 优先作为工程规范和模板来源；逐个检查 LICENSE |
| [skills.sh](https://skills.sh/) | 公开 Skill 目录和安装路径 | 只是索引，不是统一许可证；每个仓库单独核验 |
| [OpenAI Skills 仓库](https://github.com/openai/skills) | Codex 技能示例和目录结构 | 单个 Skill 的许可证在其目录内，不能按仓库整体默认开源 |
| Microsoft Copilot Prompt Gallery / 官方业务指南 | 采购、销售、Excel、营销等工作流范式 | 只做方法参考，避免复制具体提示词和页面文案 |
| Shopify、Square、Lightspeed、SCORE、BDC 等官方经营指南 | 菜单定价、库存、客单、复购和小企业经营方法 | 适合做知识来源和规则校验；需要保留来源和更新时间，不直接搬成 Skill 正文 |
| Notion 模板、PromptBase、ClawHub 等市场 | 模板、提示词和社区方案 | 适合作为竞品/需求线索；购买或下载前确认商业再许可、隐私和恶意指令风险 |

## 六、建议进入第一版的复用清单

第一版只吸收以下内容：

1. **确认卡协议**：直接复用内部 `intent-card`。
2. **行动卡结构**：直接复用内部 `guiputi-business-assistant`。
3. **数据口径规则**：借鉴 Excel Analyst Pro，重写为中文小微经营版。
4. **保本 / 情景 / 敏感性方法**：借鉴 Financial Valuation Toolkit，只保留轻量计算。
5. **经营记录字段**：参考 Retail Revenue Intelligence 和小企业 Excel 项目，重新设计中文字段。
6. **提示词结构**：参考 Copilot 提示词库，但不直接粘贴原文。

## 七、暂不纳入

- DCF、LBO、WACC、蒙特卡洛等企业投融资模型；
- 需要实时 POS、支付、地图或电商后台接口才能成立的完整系统；
- 直接复制无明确许可证的仓库代码、文案、Excel、图表或样例数据；
- 短视频运营完整链路，避免与已有负责人的版块重叠；
- 自动发布、自动采购、自动报税和“保证收入”的能力。

## 八、推荐落地顺序

### 第 1 批：直接引入工程方法

- Anthropic `webapp-testing`：用于本机原型验收和回归思路；
- Anthropic `internal-comms`：用于经营日报、复盘和行动回执的输出结构；
- Matt Pocock 的 `grill-me` / `domain-modeling` / `research` / `writing-for-agents` 方法；
- 内部 `intent-card`：作为 WorkBuddy 确认卡唯一入口。

### 第 2 批：改写业务方法

- `venture-analyst-skills`：改成“经营方向与选品验证”；
- `ba-project-factory`：改成“经营问题拆解与完成标准”；
- Excel Analyst Pro 的公开 README 方法：只保留事实、假设、公式、校验四层，不复制受限正文。

### 第 3 批：自建中国小微场景

- 成本与定价：单品成本、损耗、毛利、套餐、保本量；
- 选址与合规：人流观察、候选点比较、官方材料清单；
- 采购与库存：供应商比价、首日备货、停止补货；
- 获客与成交：门头菜单、开业预告、现场成交；
- 复盘与复购：每日记录、明天改一件事、复购权益。

## 九、下一步确认项

在继续做新版 Skill 前，需要先确定：

- 采用哪些候选包作为“方法参考”；
- 是否允许使用 CC BY-SA 内容并承担署名和同许可要求；
- 是否要向 Excel Analyst Pro 作者申请商业授权；
- 第一版六模块是否全部开放，还是先开放成本定价、选址合规、复盘复购三个模块。
