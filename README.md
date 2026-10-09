# 生意线 Skill 与网页原型归档

这是「生意线」项目的可复用 Skill、确认卡、网页原型、需求资料和市场技能源码审计归档。

## 目录

- `skills/`：可复用生意线 Skill 源码，包括经营助手、上架流水线和小微经营助手。
- `product-workbench/`：S1–S6 场景工作流，包含业务定义、Skill 包、网页版、确认卡、回归测试和发布材料。
- `prototypes/opendesign/`：OpenDesign 原型集合和 manifest；包含 6 个可点击网页原型。
- `prototypes/生意线-经营复盘工作台-可分享预览.html`：可单独转发的经营复盘工作台 HTML。
- `research/market-skill-audit-20261008/`：市场 Skill 源码快照与审计材料；已排除嵌套 Git 历史对象。
- `docs/`：生意线需求、候选 Skill、GitHub 核验和实施建议文档。

## 预览原型

在仓库根目录运行：

```powershell
python -m http.server 8289
```

然后打开 `http://localhost:8289/prototypes/opendesign/`。也可以直接打开 `prototypes/生意线-经营复盘工作台-可分享预览.html`；该单文件原型需要联网加载 React、Babel 和字体资源。

## 归档说明

本仓库用于项目存档和后续复用。市场技能目录保留源码与审计资料，不包含各来源仓库的 Git 历史；原型中的示例经营数据均为脱敏重构数据。
