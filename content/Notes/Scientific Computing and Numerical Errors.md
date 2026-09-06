---
publish: true
title: Scientific Computing and Numerical Errors
created: 2026-09-05T20:38:16.724Z
modified: 2026-09-05T20:54:05.360Z
---

==2026-09-06==

# [[Scientific Computing]] and Numerical Errors

## Scientific computing in science and engineering

**Concept:** The use of computer algorithms and numerical methods to solve complex mathematical models in [[Engineering]] and [[Physics]]. It is essential when analytical (exact) solutions are impossible or computationally intractable.

## Sources of computational errors

**Concept:** The discrepancies between exact mathematical solutions and the computed numerical results.

- **[[Modeling errors]]:** Flaws in the mathematical representation of the physical system.
- **[[Blunders]]:** Human programming or data entry mistakes.
- **[[Data uncertainty]]:** Inaccuracies in physical measurements or input parameters.
- **Numerical errors:** Artifacts of the computing process (specifically round-off and truncation).

## Approximations and significant figures

**Concept:** [[Significant figures]] designate the reliability of a numerical value. Computations must track these to avoid falsely implying absolute exactness in results.

- **Rule of thumb:** If an approximation is accurate to $n$ significant figures, the relative error is generally less than $5 \times 10^{-n}$.

## Absolute and relative errors

For a true value $x$ and an approximate computed value $x^*$:

- **[[Absolute Error]] ($E_a$):** The exact magnitude of the difference.
  $E_a=\vert{}x-x^*\vert{}$
- **[[Relative Error]] ($E_r$):** The absolute error normalized by the true value (better for comparing errors across different scales).
  $E_r=\left\vert{}\frac{x-x^*}{x}\right\vert{}$
- **Percent Relative Error ($\epsilon_t$):**
  $\epsilon_t=E_r \times 100\%$

## Round-off errors and truncation errors

- **[[Round-off error]]:** Arises because computers represent continuous real numbers using a finite number of digits (e.g., [[Floating-point arithmetic]] limits).
- **[[Truncation error]]:** Arises from using an approximation in place of an exact, infinite mathematical procedure (e.g., stopping a [[Taylor series]] expansion after a finite number of terms).

## Error propagation and general error formula

**Concept:** Describes how errors in independent input variables cascade through a function to affect the final computed output $f(x_1, x_2, \dots, x_n)$.

- **Maximum Absolute Error Formula:** If each variable $x_i$ has an absolute error $\Delta x_i$, the maximum error in the function $\Delta f$ is approximated by the first-order derivative:
  $\Delta f \approx \sum_{i=1}^{n} \left\vert{} \frac{\partial f}{\partial x_i} \right\vert{} \Delta x_i$
- **Statistical [[Error Propagation]] (Standard Deviation):** If errors are independent and random with standard deviations $\sigma_{x_i}$:
  $\sigma_f = \sqrt{ \sum_{i=1}^{n} \left( \frac{\partial f}{\partial x_i} \sigma_{x_i} \right)^2 }$
