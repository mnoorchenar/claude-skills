---
name: graphviz-diagram-style
description: Produce Graphviz diagrams (flowcharts, process diagrams, decision trees, algorithm flows) with dark-mode styling and a mandatory 3-level contrast stack so nodes never blend into cluster backgrounds.
---

# Graphviz Diagram Style Standard

Use Graphviz for flowcharts, process diagrams, decision trees, and algorithm flows. Never use ASCII/Unicode text graphics for diagrams.

## Standard template

Always include `fontname="DejaVu Sans"` on graph, node, and edge attributes.

```{.graphviz}
digraph Example {
    graph [
        fontsize=20, dpi=150, size="8,11", ratio=auto,
        margin=0, nodesep=2, ranksep=0.5, fontname="DejaVu Sans"
    ];
    node [
        shape=box, style="rounded,filled", fillcolor=lightblue,
        fontsize=20, margin=0.15, fontname="DejaVu Sans"
    ];
    edge [
        fontsize=20, color=darkorange, penwidth=2,
        arrowsize=1.5, fontname="DejaVu Sans"
    ];
    rankdir=LR;
    A [label="Step 1"];
    B [label="Step 2"];
    A -> B [label="Action"];
}
```

## Color contrast rules (critical)

The most common Graphviz rendering failure is a node becoming invisible because its fill color is too close in brightness to its cluster's background. This must never happen.

### The 3-level contrast stack

Every diagram that uses clusters must follow this hierarchy:

| Level | Element | Required property |
|---|---|---|
| 1 | Diagram background | Darkest, near black (implicit or via `bgcolor`) |
| 2 | Cluster `fillcolor` | Mid-dark, clearly visible against black, clearly darker than nodes |
| 3 | Node `fillcolor` | Brightest, vivid, clearly visible against the cluster background |

The brightness jump between level 2 (cluster) and level 3 (node) must be large and obvious. If a node box can't be clearly distinguished from its cluster background at a glance, the contrast is insufficient.

### Approved color pairs (cluster background → node fill)

Always choose from this list, or follow the same pattern:

| Theme | Cluster fillcolor | Node fillcolor | Node fontcolor |
|---|---|---|---|
| Blue | `#0D3B6E` | `#1976D2` | white |
| Deeper Blue | `#0A2744` | `#1E88E5` | white |
| Purple | `#3E0A6E` | `#7B1FA2` | white |
| Green | `#1B3A1B` | `#388E3C` | white |
| Red/Orange | `#5C1A00` | `#BF360C` | white |
| Teal | `#003333` | `#00796B` | white |
| Dark Red | `#4A0000` | `#C62828` | white |

### Never do this

- Never use near-black for cluster backgrounds (e.g. `#0D2137`, `#1A0033`, `#1B0000`, `#071E3D`, `#0D1117`) when nodes inside also use dark fills — nodes become invisible.
- Never omit an explicit `fillcolor` on nodes inside clusters — without it, nodes inherit or blend with the cluster background.
- Never use two colors from the same hue family that differ by less than roughly 30% in brightness for a cluster-to-node pair.

### Self-check before finalizing any diagram

1. Is every node box clearly distinct from its cluster background?
2. Is every node's `fillcolor` explicitly set, not inherited?
3. Is the cluster background mid-dark, not near-black and not near-white?

If any answer is no, fix the colors before finalizing.

### Minimal correct example with clusters

```{.graphviz}
digraph Correct {
    graph [fontsize=18, dpi=150, rankdir=LR, fontname="DejaVu Sans", bgcolor="transparent"];
    node  [shape=box, style="rounded,filled", fontsize=17, fontcolor="white", fontname="DejaVu Sans"];
    edge  [fontsize=14, penwidth=2, arrowsize=1.2, color="#F57C00", fontname="DejaVu Sans"];

    subgraph cluster_a {
        style=filled;
        fillcolor="#0D3B6E";
        fontcolor=white;
        fontname="DejaVu Sans";
        label="Group A";
        A1 [label="Node 1", fillcolor="#1976D2"];
        A2 [label="Node 2", fillcolor="#1976D2"];
    }
    subgraph cluster_b {
        style=filled;
        fillcolor="#3E0A6E";
        fontcolor=white;
        fontname="DejaVu Sans";
        label="Group B";
        B1 [label="Node 3", fillcolor="#7B1FA2"];
        B2 [label="Node 4", fillcolor="#7B1FA2"];
    }
    A1 -> B1; A2 -> B2;
}
```
