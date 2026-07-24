---
name: math-explanation-depth
description: Explain mathematical formulas at full depth with intuition, LaTeX formula, symbol dictionary, term-by-term breakdown, and a fully worked numerical example. Use whenever a formula, equation, or mathematical concept needs teaching.
---

# Full-Depth Mathematical Explanation Standard

This is the standard for explaining any formula. Never abbreviate. Every formula requires all six of the following pieces.

## 1. Pre-formula intuition (minimum 3–5 sentences)

Explain in plain English what the formula is trying to compute and why this particular mathematical structure achieves it. The reader must understand the purpose before seeing any symbols.

## 2. The formula itself

Always use `$$...$$` display math blocks. Never present a formula only as inline math.

## 3. Symbol dictionary

Define every single symbol that appears, including subscripts, superscripts, set-membership notation, and operators. No symbol may appear undefined. Format this as a dedicated list, not inline text.

## 4. Term-by-term breakdown

Explain what each term or sub-expression computes and why it's there. If a term is divided, explain why dividing produces the desired effect. If a term is exponentiated, explain what that achieves. Cover every term in the formula, not just the main one.

## 5. Worked numerical example

Substitute real numbers and compute step by step. Show every arithmetic operation explicitly. Never skip steps or substitute "..." for intermediate results.

## 6. Interpretation

After computing the result, explain what the number means in the real-world context of the problem. What would a different result have meant?

## Example of insufficient depth (avoid this)

> The softmax function converts logits to probabilities: $\sigma(z_i) = \frac{e^{z_i}}{\sum_j e^{z_j}}$. It normalizes values to sum to 1.

This skips the symbol dictionary, term breakdown, and worked example — not acceptable.

## Example of correct depth

**Intuition**: When a neural network produces raw output scores (logits), they are arbitrary real numbers — some positive, some negative, with no guaranteed range. We need to convert them into a valid probability distribution: all values between 0 and 1, summing to exactly 1. Simply dividing each score by the total would fail for negative numbers. Softmax solves this by first exponentiating every score, making all values positive and amplifying differences, then dividing by the total of all exponentiated scores to normalize. The exponential also makes the largest logit much larger relative to the others, so the model's top prediction becomes dominant.

**Formula**:
$$\sigma(z_i) = \frac{e^{z_i}}{\displaystyle\sum_{j=1}^{K} e^{z_j}}$$

**Symbol definitions**:
- $z_i$: the raw logit (score) for class $i$, an unconstrained real number
- $e$: Euler's number (~2.718), the base of the natural exponential function
- $e^{z_i}$: the exponential of the $i$-th logit, always positive regardless of the sign of $z_i$
- $K$: the total number of classes
- $j$: a summation index running over all $K$ classes
- $\sum_{j=1}^{K} e^{z_j}$: the sum of all exponentiated logits, the normalization constant
- $\sigma(z_i)$: the output probability for class $i$, guaranteed to be in $(0, 1)$

**Term-by-term breakdown**: The numerator $e^{z_i}$ maps the raw score of class $i$ into a positive value. Because the exponential grows faster than linearly, a class with a logit of 3 gets a numerator of roughly 20, while a class with logit 1 gets only roughly 2.7, a ratio of about 7.4x even though the raw difference was only 2. This is the winner-take-more property of softmax. The denominator ensures all outputs sum to 1 by dividing each numerator by the global total.

**Numerical example** — given logits $[2.0, 1.0, 0.1]$:

Step 1, exponentiate each logit:
$$e^{2.0} = 7.389, \quad e^{1.0} = 2.718, \quad e^{0.1} = 1.105$$

Step 2, sum all exponentials:
$$7.389 + 2.718 + 1.105 = 11.212$$

Step 3, divide each by the sum:
$$\sigma(z_1) = 0.659, \quad \sigma(z_2) = 0.242, \quad \sigma(z_3) = 0.099$$

**Interpretation**: The model assigns 65.9% probability to class 1, 24.2% to class 2, and 9.9% to class 3. Even though class 1's logit was only twice class 3's raw score, its final probability is roughly 6.7x higher — softmax amplifies confidence.

## Table restriction

Do not use tables for long or multi-line formulas, matrices, vectors, or multi-step calculations. Tables are fine only for very simple one-line formulas (e.g. $y = mx + b$) or pure numeric summaries.
