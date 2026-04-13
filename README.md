# `topic-cluster-architect`

一个面向 `Claude Code` 的 SEO 内容策略 Skill。

给定网站 URL、业务描述、竞品链接或现有内容清单后，它会先判断站点类型，再输出一份适合该站点商业模式的 `Topic Cluster` 策略报告，而不是只返回一堆分散的关键词。

- 先识别网站 archetype，而不是套用通用 SEO 模板
- 规划 `pillar pages`、支持内容、内链关系与执行优先级
- 可结合竞品 URL 做 gap analysis
- 可结合现有页面/文章清单做保留、扩展、合并、重定位建议
- 对新站会补充更聚焦的增长打法
- 输出可读性较强的结构化报告，适合直接讨论或继续落地

## 快速安装

```bash
npx skills add x0u0an/topic-cluster-architect-skill --skill topic-cluster-architect
```

如果你更希望用插件方式安装：

```bash
/plugin marketplace add x0u0an/topic-cluster-architect-skill
/plugin install topic-cluster-architect-skill
```

## 预览展示区

> 截图 / 演示占位区
>
> 你在 GitHub 仓库发布后，可以把实际截图或一个简短 GIF 放在这里，让整个仓库展示效果更接近公开发布的 Skill 页面。

建议放这些预览内容：

- 完整报告总览截图
- cluster 架构表格截图
- 竞品 gap analysis 截图
- preview URL 或保存结果截图

## 这个 Skill 会产出什么


每次运行后，用户通常会得到一份结构化策略报告，内容一般包括：

1. `Executive Summary`
   - 对网站当前 SEO 内容机会的简要判断
   - 当前最值得优先做的方向

2. `Site Diagnosis`
   - 网站类型判断
   - 主 archetype / 次 archetype
   - 判断置信度
   - 站点成熟度（新站 / 早期 / 已建立）

3. `Growth Objective`
   - 更偏需求承接、需求创造、主题权威建设，还是转化导向增长

4. `Topic Universe`
   - 商业主题
   - 问题/解决方案主题
   - use case 主题
   - comparison / alternative 主题
   - 教育型主题
   - 信任建设主题

5. `Cluster Architecture`
   - 重点 `pillar pages`
   - 每个 cluster 的 supporting content
   - 内链角色与结构建议
   - 转化相关性

6. `Optional Analysis`
   - 竞品主题缺口分析
   - 现有内容适配分析
   - 新站优先策略

7. `Execution Roadmap`
   - Phase 1 / 2 / 3 执行顺序
   - 先做什么、后做什么、哪些暂缓

## 报告如何交付

默认会按以下优先级交付结果：

1. `Preview URL`
   - 如果当前环境支持预览，会优先生成预览链接
   - 便于阅读，但默认不自动保存

2. `Chat Inline Report`
   - 如果不能预览，就直接在对话里输出完整报告

3. `Saved Markdown File`
   - 只有当用户明确要求保存时，才会写入文件
   - 默认文件名格式：`topic-cluster-report-YYYY-MM-DD.md`
   - 保存后应返回明确文件路径

示例：

```text
Use topic-cluster-architect on https://example.com.
First identify the site type and confidence level, then build a readable topic cluster report with tables.
If possible, generate a preview URL. Ask me before saving the report.
```

可能得到的结果形式：

```text
Preview generated: <preview-url>
```

或者：

```text
Saved report: C:\Users\name\project\topic-cluster-report-2026-04-12.md
```


## 安装

### 方式一：CLI 安装（推荐）

```bash
# 添加整个 Skill 仓库
npx skills add <YOUR_GITHUB_USERNAME>/topic-cluster-architect-skill

# 只安装当前 Skill
npx skills add <YOUR_GITHUB_USERNAME>/topic-cluster-architect-skill --skill topic-cluster-architect
```

### 方式二：Claude Code Plugin

```bash
/plugin marketplace add <YOUR_GITHUB_USERNAME>/topic-cluster-architect-skill
/plugin install topic-cluster-architect-skill
```

## 使用方式

### 方式一：直接自然描述需求

适合大多数用户，直接在 `Claude Code` 里说：

```text
请分析这个网站，并为它设计一套 topic cluster 策略：https://example.com
```

或者：

```text
请为我的 SaaS 网站规划 SEO 内容集群。这是网址和 3 个竞品链接，请优先告诉我先做哪些 cluster。
```

### 方式二：直接调用 Skill

在 `Claude Code` 中运行：

```text
/topic-cluster-architect
```

然后补充：

- 网站 URL
- 一句话业务描述
- 目标受众
- 主要目标（流量 / 线索 / 演示 / 销售）
- 可选竞品 URL
- 可选现有页面或文章清单

## 示例提示词

### 1）基础版：站点诊断 + cluster 规划

```text
请使用 topic-cluster-architect 分析 https://example.com。
先判断网站类型和置信度，再输出一份清晰的 topic cluster 报告，尽量用表格展示。
如果可以，先生成预览链接；如果要保存文件，先问我。
```

### 2）带竞品：找主题缺口

```text
请使用 topic-cluster-architect 分析 https://example.com。
我的业务是 [一句话描述]，目标受众是 [audience]，主要目标是 [traffic / leads / sales]。
竞品有：https://competitor1.com, https://competitor2.com, https://competitor3.com
请先判断站点类型和置信度，再展示竞品主题缺口、优先 cluster，以及一个 90 天执行路线。
如果可以先预览，再问我要不要保存。
```

### 3）带内容清单：重构现有内容架构

```text
请使用 topic-cluster-architect 分析 https://example.com。
这是一个 [business type] 网站，目标用户是 [audience]，目标是 [goal]。
以下是我现有的内容清单：[粘贴页面 / 分类页 / 文章列表]
请把这些内容重新映射到更合理的 cluster 架构里，并告诉我哪些应该保留、扩展、合并或重定位。
如果要保存报告，先问我。
```

## 适合谁使用

这个 Skill 特别适合：

- 独立站站长
- SaaS 团队
- 电商团队
- 咨询顾问和代理商
- SEO Strategist
- Content Lead
- 还没有形成内容路线图的创业者

## 建议用户提前准备什么

最少建议提供：

- 网站 URL
- 一句话业务描述
- 目标受众
- 主要目标

如果有这些，输出会更强：

- 2-5 个竞品 URL
- 当前 service pages / category pages / article list
- 目标国家或地区
- 当前已知内容问题或优先事项

## Skill 的核心策略框架

这个 Skill 不是简单吐关键词，而是按一个固定策略流来工作：

1. `Site archetype diagnosis`
2. `Site maturity assessment`
3. `Growth goal interpretation`
4. `Topic universe mapping`
5. `Competitor gap / content inventory analysis`
6. `Cluster architecture design`
7. `Site-type-specific strategic adjustment`
8. `Expected SEO impact and success conditions`
9. `New-site strategy`（如适用）
10. `Preview / save delivery flow`

## 为什么这个 Skill 有价值

很多 SEO 内容规划结果不好用，通常是因为它们：

- 把所有网站都当成同一种内容模型来规划
- 只给关键词，不给架构
- 忽略商业模式差异
- 忽略现有内容资产
- 输出不够清晰，难以直接执行

这个 Skill 的设计目标，就是解决这些问题。
