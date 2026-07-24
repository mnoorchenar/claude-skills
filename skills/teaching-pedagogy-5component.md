---
name: teaching-pedagogy-5component
description: Teach technical topics using a mandatory 5-component cycle (concept, visualization, math, numerical example, code) with mastery-level depth, workflow rules, and artifact structure. Use for any self-paced technical learning content.
---

# Five-Component Teaching Pedagogy

## Core Principle

Comprehensive, detailed explanations are mandatory in self-paced learning content. Never sacrifice depth for brevity. Use unlimited subsections to organize complex topics clearly.

**Mastery goal**: After reading each section, the learner must completely understand the topic from basic to advanced level.

## Five-Component Teaching Cycle (ALL MANDATORY)

Complete ALL 5 steps for EACH concept before moving to the next. Never separate theory from practice, and never batch all explanations, then all visualizations, then all math, then all examples, then all code at the end — this creates cognitive overload.

Correct order: For Concept A, do steps 1–5. Then for Concept B, do steps 1–5. And so on.

| # | Component | Requirements |
|---|-----------|--------------|
| 1 | Concept Explanation | Clear definition in plain language, a mandatory real-world analogy, and an explanation of WHY this concept exists and what problem it solves |
| 2 | Visualization | A diagram or plot (see the diagram/plotting style skills for this project if available). Always extend the explanation AFTER the visualization — describe what the learner should observe and what it teaches them |
| 3 | Mathematics | Full-depth treatment (see the math-explanation-depth skill for the exact standard) |
| 4 | Numerical Example | Use mathematical notation (matrices, equations, formatted numbers), not code. Show fully worked calculations with actual numbers, plus an interpretation paragraph explaining what the result means in practice |
| 5 | Code | High-level library usage (e.g. sklearn, tensorflow, pandas). Show configuration and practical usage. Only implement from scratch if explicitly requested. Every line commented (WHAT and WHY). Output is mandatory (include a `# Output:` block) |

## Depth Requirements

Define all terms before use. Address common errors and edge cases. Explain the reasoning behind concepts, not just the mechanics.

## Code Philosophy

Default to high-level library APIs:
- Use production-ready libraries efficiently rather than reinventing the wheel
- Explain each library/parameter in full detail the first time it's used; every later use just references that first explanation
- Avoid academic re-implementations (e.g. writing gini impurity or entropy from scratch) unless the learner explicitly asks for a from-scratch implementation

## Table Usage

Use tables for summaries, comparisons, short descriptions, and simple one-line formulas only. Never use tables for long/complex formulas, matrices, vectors, multi-step numerical calculations, or long text (over ~20 words per cell).

## Workflow

1. In the first response, announce the full list of sections upfront.
2. One section = one new artifact. Never append to a previous artifact.
3. All subsections within a section stay together in the same artifact.
4. Deliver one section at a time with comprehensive explanations.
5. Each section should progress from basic to intermediate to advanced.
6. Use as many subsections as needed for complete clarity.
7. After each section, stop and ask "Ready for the next section?" and wait for confirmation before continuing.
8. After all sections are complete, give one comprehensive practice question covering all content: problem statement, sample data, expected output, progressive hints, and a complete solution using production libraries with exhaustive comments.

## Content Template

Use this structure for each concept within a section:

```markdown
# [Title] - Section [N]: [Name]

## Introduction
[Comprehensive overview: what we'll learn, why it matters, what problem each concept solves, how topics connect to each other and the broader picture]

## [Concept Name]

### What It Is
[Plain-language definition, minimum 3 sentences, plus a concrete real-world analogy that extends into the math, plus how this fits the broader system]

### Why It Exists
[What problem does this solve? What would break or be worse without it?]

### Mathematical Foundation
[See math-explanation-depth skill for the full standard]

### Numerical Example
[Concrete scenario, every step shown, no skipped arithmetic, interpretation paragraph]

### Code
[High-level library usage, configuration explained once, output mandatory]

### Visualization
[State what the plot teaches before showing it; describe what to observe after]
```

## Formatting Rules

- Emoji policy: in markdown text, only ❌ and ✅ are allowed. No other emoji or decorative Unicode symbols anywhere.
- Never use ASCII/Unicode text graphics for diagrams — always use a proper diagramming or plotting tool.
- Artifact format: `text/markdown` for learning guides; use a code artifact only for standalone scripts.

## Symbols Used in Instructions

`★` marks a critical/mandatory rule; `●` marks a required checklist item; `○` marks an optional one.
