---
publish: true
title: Significant figures
created: 2026-09-05T20:49:19.006Z
modified: 2026-09-05T20:53:56.554Z
---

==2026-09-06==

# Significant figures

## Identifying Significant Figures

**Concept:** Determining which digits in a measured or computed number carry meaningful contributions to its [[Measurement precision]].

- **Non-zero digits:** Always significant (e.g., $456$ has 3 sig figs).
- **Captive zeros:** Zeros between non-zero digits are always significant (e.g., $1005$ has 4 sig figs).
- **Leading zeros:** Zeros preceding all non-zero digits are _never_ significant; they only locate the decimal point (e.g., $0.002$ has 1 sig fig).
- **Trailing zeros (with decimal):** Zeros at the end of a number containing a decimal point are significant (e.g., $3.500$ has 4 sig figs).
- **Trailing zeros (no decimal):** Ambiguous. Generally assumed not significant unless stated otherwise. Use [[Scientific notation]] to explicitly define precision (e.g., $1.50 \times 10^3$ clearly has 3 sig figs).
- **Exact numbers:** Counted quantities (e.g., 5 apples) or defined constants (e.g., $1 \text{ inch} = 2.54 \text{ cm}$) have an infinite number of significant figures and do not limit the precision of a calculation.

## Mathematical Operations

**Concept:** Propagating certainty through calculations to ensure the final result does not artificially overstate the [[Precision]] of the input data.

- **Addition and Subtraction:**
  - **Rule:** The final result is rounded to the same number of **decimal places** as the input value with the _fewest_ decimal places.
  - **Example:** $12.11 + 2.1 = 14.21 \rightarrow$ Round to $14.2$ (limited by one decimal place in 2.1).
- **Multiplication and Division:**
  - **Rule:** The final result is rounded to the same number of **significant figures** as the input value with the _fewest_ significant figures.
  - **Example:** $4.56 \times 1.4 = 6.384 \rightarrow$ Round to $6.4$ (limited by two sig figs in 1.4).

## Rounding rules

- Digit to drop is $< 5$: Leave the last retained digit unchanged.
- Digit to drop is $> 5$: Increase the last retained digit by 1.
- Digit to drop is exactly $5$ (or $5$ followed by zeros): Use the **"round half to even"** rule (also called [[Bankers rounding]]) to minimize statistical bias in large datasets.
  - **Example:** $2.35 \rightarrow 2.4$ (rounds up to even).
  - **Example:** $2.25 \rightarrow 2.2$ (stays at even).
