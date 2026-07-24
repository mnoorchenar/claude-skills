---
name: matplotlib-seaborn-style
description: Create Matplotlib or Seaborn plots (line, scatter, bar, histogram, pie, distributions, box plots, heatmaps, regression) using wide dark-mode layouts with consistent color palette and multi-panel comparisons.
---

# Matplotlib / Seaborn Style Standard

Use Matplotlib for line, scatter, bar, histogram, and pie charts, and general concept visualization. Use Seaborn for statistical plots: distributions, box plots, heatmaps, regression plots.

More plots generally aid understanding — include multiple panels to show different aspects, comparisons, or progressive complexity, rather than a single cramped plot.

## Standard template

Maximize horizontal space (width 10–14), minimize vertical space (height 3–4). Prefer side-by-side subplots over stacked ones.

```{.matplotlib}
import matplotlib.pyplot as plt
import numpy as np

fig, (ax1, ax2, ax3) = plt.subplots(1, 3, figsize=(14, 3))
# ... plot code ...
plt.tight_layout()
# Do not call plt.show() or plt.savefig()
```

## Dark mode color palette

Use only these colors for fills, lines, or markers: `#1565C0`, `#2E7D32`, `#C62828`, `#6A1B9A`, `#F57C00`, `#0097A7`.

Never use white, pastel, or other light colors for any fill, line, or marker — they don't read well against a dark background.

## After every plot

Always follow the visualization with written interpretation: state explicitly what the reader should observe in the plot and what it confirms or teaches about the underlying concept. Never leave a plot to speak for itself without this follow-up explanation.
