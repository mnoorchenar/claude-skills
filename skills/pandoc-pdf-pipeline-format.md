---
name: pandoc-pdf-pipeline-format
description: Write markdown compatible with a personal Pandoc + XeLaTeX pipeline that converts markdown to PDF/HTML, with pandoc-plot for matplotlib/graphviz rendering. Use whenever output will be pasted into that converter (fence syntax, math delimiters, emoji/symbol handling, output-block markers).
---

# Pandoc → PDF Pipeline Markdown Format

This skill describes the exact markdown conventions expected by a personal Pandoc + XeLaTeX conversion tool. Content that doesn't follow these conventions may render incorrectly or fail to compile. Use this skill whenever markdown is being produced to paste into that converter, regardless of which teaching-pedagogy skill generated the content.

## Code fences

- **Matplotlib/Seaborn plots**: use `` ```{.matplotlib} `` as the fence. A plain ` ```python ` block containing `import matplotlib`/`pyplot`/`seaborn` is also auto-detected and upgraded, but the explicit `{.matplotlib}` fence is preferred and unambiguous.
- **Graphviz diagrams**: use `` ```{.graphviz} `` (or `{.dot}`). Do not add `height=`/`width=`/`size=` attributes manually — the pipeline auto-sizes graphviz output based on node/edge count and layout direction unless you explicitly set one.
- **Regular code** (Python, SQL, R, bash, etc.): use the standard language fence, e.g. `` ```python ``, `` ```sql ``, `` ```r ``, `` ```bash ``.
- **Plain text/output-only blocks**: fences with language `output`, `text`, `table`, `result`, `expected`, `stdout`, or `console` are rendered in a small, distinctly colored output box automatically.

## Expected-output convention

Within a code fence, a line starting with `-- Expected Output:` (SQL/comment style) or `# Expected Output:` (Python style) automatically splits the block: everything above becomes a normal code block, everything from that marker onward is rendered as a separate styled output box. Always use this exact marker phrasing to get that treatment — don't invent alternate phrasing like `-- Result:` or `# Output is:`.

## Math

- Use standard dollar-delimited math: `$...$` for inline, `$$...$$` for display. The pipeline parses these directly (`tex_math_dollars`); no need for `\(...\)` or `\[...\]`.
- Standard LaTeX macros work inside math mode as expected (`\frac`, `\sum`, `\sqrt`, Greek letters, etc.).
- Avoid unmatched or multi-line dollar signs used as plain currency text near LaTeX-like content — the pipeline's math-detection can misinterpret ambiguous cases. If writing about actual currency near math, keep the two clearly separated in different lines/paragraphs.

## Symbols and emoji

- Only a small, specific emoji set is recognized and rendered nicely in the PDF: `✅ ✔ ✓ ❌ ✖ ⛔ 🚫 🔴 🟢 ⚠️ ⚡ 🔥 💥 💡 📌 🚀 ⚙️ 🔧 👍 💚`. Stick to this set — other emoji are stripped or replaced with `[emoji]` inside code blocks.
- Preferred pair for correctness/incorrectness marking in prose: `✅` and `❌` only, per your teaching-pedagogy skills.
- **Symbol-prefixed line lists**: two or more consecutive lines starting with `✓`/`✔`, `❌`/`✖`, or `⚠`/`⚠️` are automatically converted into a styled checklist/crosslist/warninglist block. To get this styling, write them as consecutive lines with the symbol directly at the start, e.g.:
  ```
  ✓ First correct point
  ✓ Second correct point
  ```
  A single isolated symbol line will not get this special treatment.
- Certain Unicode math/Greek symbols render correctly in body text via built-in mappings: `× ÷ ± ≈ ≠ ≤ ≥ ∞`, Greek letters `α β γ δ θ λ μ π σ ω`, and subscripts/superscripts `₀ ₁ ₂ ₃` / `⁰ ¹ ² ³`. Prefer these over other exotic Unicode symbols in prose text, since unmapped Unicode characters can break the LaTeX compile. (Graphviz labels have broader Unicode support via the DejaVu Sans font — see the `graphviz-diagram-style` skill.)

## Tables

- Standard markdown pipe tables. The renderer auto-fits column widths, but keep cell text reasonably short — long paragraphs inside table cells hurt layout even though they won't break the build. This matches the "tables for summaries, not long text" rule already in the teaching-pedagogy skills.

## Farsi/RTL text

- If a response contains Farsi/Arabic text, no special markup is needed — the pipeline auto-detects it and applies right-to-left rendering with the correct font automatically.

## What NOT to do

- Don't use raw ASCII/Unicode box-drawing art for diagrams — this is already forbidden by the diagram-style skills, but it's worth repeating here: it won't render specially in this pipeline and looks broken in the final PDF.
- Don't manually add LaTeX `\includegraphics`, `\begin{figure}`, or other raw LaTeX unless intentionally producing a raw LaTeX passthrough block — plain markdown + the fences above is sufficient and safer.
- Don't invent custom code-fence languages expecting special rendering — only `{.matplotlib}`, `{.graphviz}`/`{.dot}`, and the plain-text output languages listed above get special handling; anything else is rendered as a generic code block.
