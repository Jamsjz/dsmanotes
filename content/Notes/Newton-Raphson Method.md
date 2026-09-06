---
title: Newton-Raphson Method
publish: true
---
==2026-09-06==
# Newton-Raphson Method
## Formula
**Concept:** An open [[Root-finding algorithm]] using local tangent lines to find where $f(x) = 0$.
Given an initial guess $x_0$, the iteration updates as:
$$x_{i+1} = x_i - \frac{f(x_i)}{f'(x_i)}$$
Where:
- $x_i$: Current approximation.
- $f(x_i)$: [[Function Evaluation]] at $x_i$.
- $f'(x_i)$: First [[Derivative]] evaluated at $x_i$ (requires $f'(x_i) \neq 0$).
## Algorithm
1. **Define** $f(x)$ and compute its derivative $f'(x)$ analytically.
2. **Choose** an initial guess $x_0$, error tolerance $\epsilon$, and maximum iterations $N$.
3. **Loop** for $i = 0, 1, 2, \dots, N$:
    - Compute $f(x_i)$ and $f'(x_i)$.
    - If $f'(x_i) = 0$, terminate (failure due to zero slope).
    - Calculate $x_{i+1} = x_i - \frac{f(x_i)}{f'(x_i)}$.
    - If stopping criterion is satisfied, output $x_{i+1}$ as the root and terminate.
    - Set $x_i = x_{i+1}$.
4. **End** loop if $N$ is reached without meeting tolerance (divergence or slow convergence).
## Example
Find the root of $f(x) = x^2 - 2$ (estimating $\sqrt{2}$).
- **Derivative:** $f'(x) = 2x$
- **Initial Guess:** $x_0 = 1$
- **Iteration 1:**
    $$x_1 = 1 - \frac{1^2 - 2}{2(1)} = 1 - \frac{-1}{2} = 1.5$$
- **Iteration 2:** $$x_2 = 1.5 - \frac{1.5^2 - 2}{2(1.5)} = 1.5 - \frac{0.25}{3} \approx 1.4167$$
## Convergence and Stopping criterion
- **[[Quadratic Convergence]]:** The error at step $i+1$ is roughly proportional to the square of the error at step $i$:
    $$E_{i+1} \approx C \cdot E_i^2$$
    The number of accurate [[Significant figures]] roughly doubles with each iteration when $x_0$ is close to the true root.
- **Stopping Criteria:** Terminate when any of the following conditions are met:
    - **Absolute step difference:**
        $$\vert{}x_{i+1} - x_i\vert{} < \epsilon$$
    - **[[Scientific Computing and Numerical Errors#Absolute and relative errors|Relative Error]] tolerance ($\epsilon_s$):**
        $$\left\vert{} \frac{x_{i+1} - x_i}{x_{i+1}} \right\vert{} < \epsilon_s$$
    - **Residual value:**
        $$\vert{}f(x_{i+1})\vert{} < \epsilon_f$$