# `topic-cluster-architect`

A `Claude Code` skill for building site-specific SEO topic cluster strategies.

It first identifies what type of website it is working with, then designs a cluster strategy that fits that business model instead of applying a generic SEO template.

## What this skill does

This skill helps users turn a website, business, or content problem into a structured strategy report.

It can:
- diagnose the site's archetype
- assess whether the site is new, early-stage, or established
- state a confidence level when the diagnosis depends on partial evidence
- estimate likely SEO impact and success conditions
- identify the likely SEO growth objective
- map the site's topic universe
- design priority `pillar pages`, support content, and internal linking
- optionally use competitor URLs for gap analysis
- optionally use existing page or article inventories for keep / expand / consolidate decisions
- add a focused new-site growth plan when relevant
- generate a readable report with lists and tables

## Who this is for

This skill is useful for:
- independent site owners
- SaaS teams
- ecommerce teams
- agencies and consultants
- SEO strategists
- content leads
- founders who do not know how to structure a content roadmap yet

## What the user gets

After running the skill, the user gets a report that usually includes:
- an executive summary
- site type diagnosis with a confidence level
- site maturity and expected SEO impact
- growth goal interpretation
- topic universe breakdown
- a cluster architecture table
- optional competitor gap insights
- optional existing content fit analysis
- a new-site strategy when relevant
- a phased execution roadmap


## How the output is delivered

The report is delivered in one of these ways:

1. `Preview URL` if the current environment supports preview
   - a temporary preview is generated for easier reading
   - the preview is for viewing only unless the user asks to save it

2. `Inline report in chat` if preview is not available
   - the full report is shown directly in Claude Code

3. `Saved Markdown file` only if the user explicitly says to save it
   - default filename pattern: `topic-cluster-report-YYYY-MM-DD.md`
   - Claude should return the exact saved path after writing the file

Important:
- the report is **not saved by default**
- the user is asked whether they want to save it
- if it is not saved, the preview should be treated as temporary

## How to use in Claude Code

### Invoke the skill directly

In `Claude Code`, run:

```text
/topic-cluster-architect
```

Then provide:
- website URL
- business description
- target audience
- business goal
- optional competitor URLs
- optional existing pages or article inventory

## What users should prepare

Minimum useful input:
- website URL
- one-sentence business description
- target audience
- main goal such as traffic, leads, demos, or sales

Better input for stronger output:
- 2-5 competitor URLs
- existing service pages, category pages, or article list
- target market or geography
- known content problems or priorities

## Skill architecture

This skill uses a 10-part strategy flow:

1. `Site archetype diagnosis`
2. `Site maturity assessment`
3. `Growth goal interpretation`
4. `Topic universe mapping`
5. `Competitor gap and content inventory analysis` when available
6. `Cluster architecture design`
7. `Site-type-specific strategic adjustment`
8. `Expected SEO impact and success conditions`
9. `New-site strategy` when relevant
10. `Preview / save delivery flow`


### Why this matters

Most SEO content planning outputs fail because they:
- treat all websites as if they need the same cluster model
- return keyword lists without architecture
- ignore business model differences
- ignore existing content assets
- do not produce something readable enough to use immediately

This skill is designed to solve those problems.

## Recommended GitHub repo structure

If publishing this on GitHub, a clean structure is:

```text
topic-cluster-architect/
├── SKILL.md
├── README.md
└── references/
    ├── new-site-playbook.md
    ├── output-template.md
    ├── report-delivery.md
    ├── site-archetypes.md
    └── strategy-framework.md

```

## Install for Claude Code on Windows

### Install for all projects (`%USERPROFILE%\.claude\skills`)

#### PowerShell
Run this command from inside the `topic-cluster-architect` folder:

```powershell
New-Item -ItemType Directory -Force -Path "$Env:USERPROFILE\.claude\skills\topic-cluster-architect" | Out-Null; Copy-Item -Recurse -Force ".\*" "$Env:USERPROFILE\.claude\skills\topic-cluster-architect"
```

#### Command Prompt (`cmd`)
Run this command from inside the `topic-cluster-architect` folder:

```cmd
if not exist "%USERPROFILE%\.claude\skills\topic-cluster-architect" mkdir "%USERPROFILE%\.claude\skills\topic-cluster-architect" && xcopy /E /I /Y ".\*" "%USERPROFILE%\.claude\skills\topic-cluster-architect"
```

### Install for current project only (`.claude\skills`)

#### PowerShell
Run this command from the project root where you want to use the skill:

```powershell
New-Item -ItemType Directory -Force -Path ".\.claude\skills\topic-cluster-architect" | Out-Null; Copy-Item -Recurse -Force "<PATH-TO-SKILL>\*" ".\.claude\skills\topic-cluster-architect"
```

#### Command Prompt (`cmd`)
Run this command from the project root where you want to use the skill:

```cmd
if not exist ".\.claude\skills\topic-cluster-architect" mkdir ".\.claude\skills\topic-cluster-architect" && xcopy /E /I /Y "<PATH-TO-SKILL>\*" ".\.claude\skills\topic-cluster-architect"
```

Replace `<PATH-TO-SKILL>` with the folder path where this skill is stored locally.

## Copy-paste test prompts

### Basic site diagnosis
After installation, open `Claude Code` and try:

```text
Use topic-cluster-architect on https://example.com.
First identify the site type and confidence level, then build a readable topic cluster report with tables.
If possible, generate a preview URL. Ask me before saving the report.
```

### With competitors

```text
Use topic-cluster-architect for https://example.com.
My business is [brief description]. My target audience is [audience]. My main goal is [traffic / leads / sales].
Competitors: https://competitor1.com, https://competitor2.com, https://competitor3.com
First diagnose the site type and confidence level, then show competitor topic gaps, priority clusters, and a 90-day roadmap.
Preview first if possible, then ask whether I want to save the report.
```

### With existing content inventory

```text
Use topic-cluster-architect for https://example.com.
This is a [business type] site targeting [audience]. Goal: [goal].
Here is my current content inventory: [paste page/category/article list]
Map the existing assets into a better cluster architecture, tell me what to keep / expand / consolidate / reposition, and include the diagnosis confidence level.
Ask before saving the report.
```

## Where users can find the result

After the skill runs, users should look in one of these places:
- the preview panel or opened preview URL
- the Claude Code chat response
- the saved file path returned by Claude after confirmation

If a file is saved, Claude should explicitly tell the user the path, for example:

```text
Saved report: C:\Users\name\project\topic-cluster-report-2026-04-12.md
```
