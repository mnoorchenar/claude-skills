---
name: ggplot2-style
description: Create ggplot2 plots in R (line, scatter, bar, histogram, density, box plots, heatmaps, regression) using wide dark-mode layouts with patchwork side-by-side panels and a consistent color palette.
---

# ggplot2 Style Standard

Use ggplot2 for line, scatter, bar, histogram, density, and point charts, and for statistical plots (distributions, box plots, heatmaps, regression), using extensions like `ggdist` or `ggcorrplot` where useful.

More plots generally aid understanding — include multiple panels to show different aspects, comparisons, or progressive complexity, rather than a single cramped plot.

## Standard template

Maximize horizontal space (figure width 10–14), minimize vertical space (height 3–4). Use `patchwork` for side-by-side panels rather than stacking plots vertically. Always use `theme_minimal()` or `theme_dark()` as the base theme.

```{.r}
library(ggplot2)
library(patchwork)  # for side-by-side plots

p1 <- ggplot(data, aes(x = x_var, y = y_var)) +
  geom_line(color = "#1565C0", linewidth = 1.2) +
  theme_minimal() +
  labs(title = "Plot 1", x = "X", y = "Y")

p2 <- ggplot(data, aes(x = x_var)) +
  geom_histogram(fill = "#2E7D32", color = "white", bins = 30) +
  theme_minimal() +
  labs(title = "Plot 2", x = "X", y = "Count")

p1 | p2  # side-by-side using patchwork
# figure dimensions: width = 14, height = 3-4
```

## Dark mode color palette

Use only these colors for fills, lines, or markers: `#1565C0`, `#2E7D32`, `#C62828`, `#6A1B9A`, `#F57C00`, `#0097A7`.

Never use white, pastel, or other light colors for any fill, line, or marker — they don't read well against a dark background.

## After every plot

Always follow the visualization with written interpretation: state explicitly what the reader should observe in the plot and what it confirms or teaches about the underlying concept. Never leave a plot to speak for itself without this follow-up explanation.
