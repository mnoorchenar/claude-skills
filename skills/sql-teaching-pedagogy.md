---
name: sql-teaching-pedagogy
description: Teach SQL through progressive, problem-based business scenarios with three difficulty levels and step-by-step incremental query building. Use for self-paced SQL learning content (PostgreSQL primary, MySQL callouts).
---

# SQL Problem-Based Teaching Pedagogy

## Core Principle

Learn by solving real problems, not memorizing isolated functions. Students learn multiple SQL concepts simultaneously by tackling progressively complex business scenarios. Each section presents ONE business scenario at three difficulty levels, not three unrelated problems.

**Mastery goal**: after each section, the student can solve real-world data problems by combining multiple SQL concepts together, not just recall individual clauses in isolation.

## Student Profile Defaults

Beginner with basic database knowledge. Goal: SQL for data science and engineering. PostgreSQL is the primary teaching database; note MySQL differences in 💡 callout boxes whenever syntax varies (e.g. `SERIAL` vs `AUTO_INCREMENT`, `LIMIT` syntax, date functions).

## Three-Level Problem Progression (per section)

Each section teaches through one business scenario at three complexity levels. Level 2 explicitly extends Level 1's solution; Level 3 extends Level 2's. Never present three disconnected problems.

| Level | Complexity | Functions introduced | Query length |
|---|---|---|---|
| 1: Foundation | Simple, focused problem | 2–3 basic functions | 3–8 lines |
| 2: Building | Adds layers to Level 1 | +2–3 intermediate functions | 8–15 lines |
| 3: Mastery | Real-world complexity | +2–3 advanced functions | 15–25 lines |

## Four-Component Cycle (mandatory for each problem level)

| # | Component | Requirements |
|---|---|---|
| 1 | Business Context & Schema | Real-world scenario, complete schema with comments, explain business relationships and design rationale |
| 2 | Sample Data | Realistic data (8–12 rows), clearly showing the business situation |
| 3 | Step-by-Step Solution | Break the query into 2–6 logical steps, show output after every step, explain "why this step?" after each |
| 4 | Visualization | Use the account's `graphviz-diagram-style` skill for query execution flow or data transformation diagrams |

## Step-by-Step Query Building (critical)

Never show a complete query all at once for a new concept. Build it incrementally:
- Break the query into 2–6 logical steps
- Each step adds exactly one new concept (e.g. add `WHERE`, then add `GROUP BY`, then add `HAVING`)
- Show the output table after every single step
- Explain the business and technical reasoning behind that step before moving on
- The final step shows the complete, working query

Format for each step:

```markdown
**Step N: [Action name]**
```sql
-- [Brief explanation, notes that it builds on Step N-1]
SELECT ...
```

**Output after Step N:**
| column1 | column2 |
|---------|---------|
| ...     | ...     |

**Why this step?** [Business value and technical reasoning]
```

## Content Template

```markdown
# [Title] - Section [N]: [Business Domain Name]

## Introduction
[Business problem to solve, why it matters in real work, overview of the three levels]

## Business Scenario
[Company/situation, what data exists, what questions need answering]
**Real-World Analogy**: [concrete everyday comparison]

## Schema & Sample Data
[CREATE TABLE statements with comments explaining business meaning of each column and constraint]
[💡 MySQL note only if syntax differs]
[Sample data tables per table, 8-12 rows, with a short note on what the data represents]

## Problem Level 1: Foundation
### Problem Statement
[Simple, focused business question]
**What You'll Learn**: [2-3 concepts]
**Success Criteria**: [what the output should show and why]

### Solution Breakdown
[Step-by-step format above, 2-5 steps]

### Complete Solution
[Full commented query, plus `-- Expected Output:` with the result table]

### Business Interpretation
[What the result means practically, what decisions it supports]

### Visualization
[Graphviz diagram of the query flow, using the graphviz-diagram-style skill; state what to observe before and after]

### Functions Used Summary
| Function/Clause | Purpose | Example from this query |
|---|---|---|

### Common Mistakes & Edge Cases
[❌ wrong approach with why it fails, ✅ correct approach]

## Problem Level 2: Building
[Same structure as Level 1, explicitly stating how it extends Level 1, adding join/aggregation-level concepts]

## Problem Level 3: Mastery
[Same structure, extending Level 2, adding window functions / CTEs / subqueries / advanced date handling / complex joins as appropriate]

## Level Comparison
| Level | Query Length | Concepts Used | Business Value |
|---|---|---|---|

## Best Practices Learned
✅ DO: [key practices, performance tips]
❌ DON'T: [common mistakes, anti-patterns]

## Quick Reference
[Concise syntax patterns for each level]
```

## Table Usage Rules

Use tables for: sample data, query results, transformation steps, functions-used summaries, level comparisons, and short descriptions (≤20 words per cell). Never use tables for long explanatory text, complex conceptual discussion, or detailed code explanations — use prose or code comments instead.

## Workflow

1. In the first response, announce all sections upfront.
2. One section (with all three levels) = one new artifact. Never append to a previous artifact.
3. Deliver one section at a time.
4. After each section, stop and ask "Ready for the next section?" and wait for confirmation.
5. After all sections, give one comprehensive final practice problem: a complex business scenario drawing on concepts from every section, multiple related tables, 15–20 rows of sample data, expected output, 4–5 progressive hints, and a complete solution with step-by-step breakdown, extensive comments, alternative approaches, performance considerations, and business interpretation.

**Artifact format**: `text/markdown` for learning guides.

## Formatting Rules

- Emoji policy: only ❌ and ✅ are allowed in markdown text, used specifically to mark incorrect/correct examples. No other emoji or decorative Unicode symbols.
- Never use ASCII/Unicode text diagrams (arrows, box-drawing characters) — always use the `graphviz-diagram-style` skill for any visual flow.
- 💡 is reserved specifically for MySQL syntax callouts, not general notes.

## Symbols

`●` required, `○` optional, `★` critical, `✅` correct, `❌` error, `💡` MySQL note.
