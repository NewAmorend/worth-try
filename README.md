# Worth Try

`worth-try` 是一个 Codex skill，用来评估一家公司是否值得去，以及在多个 offer 之间怎么选。

它会把一个容易被信息不对称和情绪影响的职业决策，整理成结构化的双语决策 memo：公司尽调、offer 类型分析、加权评分、风险灯、谈判杠杆和后续追问清单。

## 能解决什么

- 判断某家公司是否值得加入。
- 比较多个 offer，给出选择建议。
- 区分实习、return offer、new-grad、全职、合同工等不同决策逻辑。
- 针对上市公司检索和分析财报、年报、10-K/10-Q、earnings call、收入、利润率、现金流、guidance、重组和裁员。
- 针对初创和私营公司检索和分析融资轮次、融资日期、投资人、估值、runway、bridge/down round 风险、招聘速度、headcount 趋势、客户 traction、创始人和投资人质量。
- 区分事实、推断、未知项和置信度，而不是把 offer 决策伪装成一个精确分数。

## 工作方式

调用 `$worth-try` 后，skill 会：

1. 判断决策类型：单个 offer、多个 offer 对比，或纯公司 worth-joining check。
2. 判断公司阶段：上市公司、后期私企、早期初创、子公司/业务线、agency/consultancy，或阶段不明。
3. 判断 offer 类型：实习、return offer、new-grad full-time、experienced full-time、contract，或类型不明。
4. 追问最少但关键的缺失信息。
5. 在需要时检索公司公开信息，并引用来源。
6. 按明确权重评分，同时标出未知项和红旗。
7. 输出中文优先、带英文标签的决策 memo。

## 输出结构

典型输出包括：

- `结论 / Recommendation`
- `公司阶段与资金面 / Stage and Financial Snapshot`
- `Offer 类型 / Internship vs Full-Time Lens`
- `评分表 / Scorecard`
- `红黄绿灯 / Risk Lights`
- `关键取舍 / Decisive Tradeoffs`
- `谈判杠杆 / Negotiation Levers`
- `待追问 / Questions to Ask`
- `资料与置信度 / Sources and Confidence`

## 示例 Prompt

```text
Use $worth-try to evaluate this full-time offer from Company A. The role is backend engineer in Shanghai, base is ...
```

```text
Use $worth-try to compare these two internship offers: one from a public company and one from a Series B startup.
```

```text
Use $worth-try to check whether this startup is worth joining. Please pay attention to funding round, runway, hiring velocity, and equity risk.
```

## 目录结构

```text
.agents/plugins/marketplace.json      # repo marketplace catalog
plugins/worth-try/                    # installable skill-only plugin
├── .codex-plugin/plugin.json
└── skills/worth-try/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/
        ├── evaluation-rubric.md
        └── research-checklist.md
worth-try/                            # direct local skill copy
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── evaluation-rubric.md
    └── research-checklist.md
```

## 安装

### 作为 Codex Plugin Marketplace 安装

这个仓库包含 repo-scoped marketplace：`.agents/plugins/marketplace.json`。添加 marketplace 后，Codex/ChatGPT desktop app 可以从插件目录安装 `Worth Try`：

```bash
codex plugin marketplace add NewAmorend/worth-try
```

之后刷新或重启 ChatGPT desktop app，在插件目录里选择 `Worth Try` marketplace 并安装 `Worth Try`。安装后可以用：

```text
$worth-try
```

### 作为本地 Skill 安装

这个仓库也保留了直接的 skill 文件夹 `worth-try/`。如果只想本地使用 skill，可以把它放到 Codex skills 目录下，通常是：

```text
~/.codex/skills/worth-try
```

## 注意

这个 skill 是决策辅助，不是法律、金融、移民、税务或心理健康建议。它的目标是把取舍摊开，帮助你在接受或拒绝 offer 前问出更好的问题。
