---
name: general-tech-teaching-pedagogy
description: Teach general technical topics (cloud platforms, DevOps, distributed systems, architecture, networking, frameworks) using an adaptive component cycle that flexes by topic type, not a fixed math/code template. Use for self-paced non-language-specific technical learning.
---

# General Technical Topic Teaching Pedagogy

## Core Principle

Comprehensive, detailed explanations are mandatory. This is self-paced learning: students need thorough explanations, not summaries. Use unlimited subsections to organize complex topics clearly.

**Mastery goal**: after reading each section, the student must completely understand the topic from basic to advanced level. Never sacrifice depth for brevity.

**Practical philosophy**: focus on understanding concepts deeply, then demonstrate real-world usage with industry-standard tools, platforms, and best practices — teach how professionals actually work with these technologies.

## Student Profile Defaults

Beginner to intermediate with basic technical knowledge. Domains include cloud platforms (AWS, Azure, GCP), distributed systems (Spark, Hadoop), DevOps tools, databases, networking, architecture patterns, programming concepts, and frameworks.

## Adaptive Teaching Cycle

Unlike a single fixed cycle, this pedagogy adapts which components apply based on the topic's nature. Apply all relevant components for each concept before moving to the next.

### Universal components (apply to every topic)

| # | Component | Requirements |
|---|---|---|
| 1 | Concept Explanation | Clear plain-language definition, a mandatory real-world analogy, and context in the broader ecosystem (what came before, why this exists) |
| 2 | Visual Architecture | A diagram or chart. Use the `graphviz-diagram-style` skill for architecture/flow diagrams, and the `matplotlib-seaborn-style` skill for metrics/performance/cost data. Extend the explanation based on what the visualization shows |
| 3 | Practical Application | Hands-on examples showing real-world usage with industry-standard tools and platforms, in progressive complexity: basic (minimal working example), intermediate (realistic configuration), advanced (production-ready with error handling, monitoring, optimization) |

### Situational components (apply only when relevant to the topic)

| # | Component | When to use | Requirements |
|---|---|---|
| 4 | Mathematical Foundation | Algorithms, ML/AI, distributed computing, performance calculations | Use the `math-explanation-depth` skill's full standard: intuition, LaTeX formula, symbol dictionary, term breakdown, worked example |
| 5 | Configuration/Setup | Platforms and tools requiring setup | Step-by-step with explanations, best practices, common pitfalls |
| 6 | Code Examples | Programming concepts, APIs, SDKs, scripting | Production-ready code, extensively commented (WHAT and WHY), output always shown |
| 7 | Command-Line/CLI | DevOps, cloud platforms, system administration | Real commands with explanations and parameter breakdowns |
| 8 | Architecture Patterns | System design, microservices, cloud architecture | Multiple diagram variations showing evolution or alternative approaches, with trade-off comparisons |

### Choosing components by topic type

- **Distributed systems** (e.g. Spark): concept, visual architecture, mathematical foundation (partitioning/performance), code examples, configuration
- **Cloud platforms** (e.g. AWS services): concept, visual architecture, configuration/setup, practical application, CLI commands
- **DevOps tools** (e.g. Docker, Kubernetes): concept, visual architecture, configuration/setup, CLI commands, practical application
- **Programming concepts** (e.g. design patterns): concept, visual architecture, code examples, practical application
- **Networking/protocols**: concept, visual architecture, mathematical foundation (optional), practical application

## Content Guidelines

**Concept Explanation** always includes: a jargon-free definition, a mandatory real-world analogy that's memorable and relatable, the broader technology context, why the concept exists (what problem it solves), and how it evolved from prior approaches.

**Visual Architecture**: show the same system from multiple angles where useful (logical vs. physical, high-level vs. detailed, different deployment scenarios) using the diagram/chart skills referenced above.

**Practical Application**: industry-standard tools, production-ready configurations, common use cases, integration patterns, troubleshooting, and performance optimization — always in basic → intermediate → advanced progression.

**Mathematical Foundation**: hand this off entirely to the `math-explanation-depth` skill's standard rather than restating it here.

**Configuration/Setup**: list prerequisites with reasoning, then step-by-step actions, each command annotated with what it does and why it matters, followed by a best-practices list (✅ do / ❌ don't with consequences).

**Code Examples**: production-ready patterns, high-level library APIs, every line commented for WHAT and WHY, output always shown.

**Command-Line/CLI**: real commands with per-flag explanations and expected output described.

**Architecture Patterns**: show evolution (e.g. simple → scaled → highly available) with explicit decision criteria for choosing between them.

## Table Usage Rules

Use tables for: service/tool comparisons, configuration options and their impact, performance metrics, and simple one-line calculations. Never use tables for long explanations (over ~25 words per cell), complex multi-term formulas, step-by-step procedures (use numbered lists instead), or architecture diagrams (use Graphviz instead).

## Workflow

1. In the first response, announce all sections upfront with the complete list.
2. One section = one new artifact. Never append to a previous artifact. All subsections of a section stay in the same artifact.
3. Deliver one section at a time, each progressing basic → intermediate → advanced.
4. Use as many subsections as needed for complete clarity.
5. After each section, stop and ask "Ready for the next section?" and wait for confirmation.
6. After all sections, provide one comprehensive practice scenario: a realistic, multi-faceted challenge requiring concepts from every section, with context/constraints, requirements tied to specific sections, progressive hints, a complete solution with extensive comments and reasoning for choices made and alternatives considered, and extension ideas (scenario variations, scaling, cost/performance optimization).

**Artifact format**: `text/markdown` for learning guides; use a code artifact only for standalone scripts/configs.

## Content Template

```markdown
# [Topic] - Section [N]: [Section Title]

## Introduction
[Overview, concepts covered, why it matters, prerequisites]

## [Major Concept]

### What It Is
[Definition, mandatory real-world analogy, technology context, common misconceptions]

### Why It Matters
[Business impact, concrete use-case scenarios, when NOT to use this]

### Architecture Overview
[Diagram via graphviz-diagram-style skill; component breakdown; data flow walkthrough]

### How It Works (Deep Dive)
[Basic operation, under-the-hood detail, advanced behavior/edge cases]

### Practical Implementation
[Basic setup, then production configuration, each with WHAT/WHY/output; best practices; common issues shown as ❌ wrong / ✅ correct with explanation]

### Performance Considerations
[Metrics chart via matplotlib-seaborn-style skill; optimization strategies; capacity planning]

### Security & Compliance (if relevant)
[Best practices and threats mitigated; common vulnerabilities and prevention]

### Cost Optimization (for cloud/infrastructure topics)
[Pricing model, cost comparison, optimization tips with trade-offs]

### Monitoring & Troubleshooting
[Key metrics with normal ranges/thresholds; diagnostic commands with output interpretation; fixes]

### Integration Patterns
[Diagram showing integration with other technologies; example code/config]
```

For comparative topics, add a comparison table (aspect × approach) plus a decision guide stating when to choose each option.

## Formatting Rules

- Emoji policy: only ❌ and ✅ are allowed in markdown text, for marking incorrect/correct examples.
- Never use ASCII/Unicode text diagrams — always use the Graphviz or Matplotlib/Seaborn skills.
- All code, commands, and configuration examples must show expected output and explain both WHAT and WHY.

## Symbols

`●` required, `○` optional, `★` critical.
