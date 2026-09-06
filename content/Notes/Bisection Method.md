---
publish: true
title: Bisection Method
created: 2026-09-05T21:09:45.744Z
modified: 2026-09-06T09:02:48.519Z
---

==2026-09-06==

# Bisection Method

## Bisection Method Overview

The bisection method is a root-finding algorithm that repeatedly bisects an interval and then selects a subinterval in which a root must lie for a continuous function.

## Formula

The formula for calculating the midpoint (root approximation) $c_n$ in the $n$-th iteration for an interval $[a_n, b_n]$ is:
$c_n = \frac{a_n + b_n}{2}$

## The Algorithm

1. Choose Initial Bracket: Choose two points $a$ and $b$ such that $f(a) \cdot f(b) < 0$. This ensures a root exists between $a$ and $b$ by the Intermediate Value Theorem.
2. Compute Midpoint: Calculate the midpoint $c = \frac{a + b}{2}$.
3. Check Termination: If $f(c) = 0$ or $\vert{}b - a\vert{} < \text{tolerance}$, then $c$ is the root. Stop.
4. Update Bracket:
   - If $f(a) \cdot f(c) < 0$, the root lies in $[a, c]$. Set $b = c$.
   - If $f(b) \cdot f(c) < 0$, the root lies in $[c, b]$. Set $a = c$.
5. Repeat: Return to Step 2.

## Error Bound

The maximum absolute error after n iterations is bounded by the inequality:
$|p_{n}-p|\leq \frac{b-a}{2^{n}}$

## Example Problem

Find a root of the function $f(x) = x^3 - x - 2$ within the interval $[1, 2]$ using a tolerance of $0.05$.

- Step 1: Check signs at endpoints:
  - $f(1) = 1^3 - 1 - 2 = -2$ (negative)
  - $f(2) = 2^3 - 2 - 2 = 4$ (positive)
  - Since $f(1) \cdot f(2) < 0$, a root exists in $[1, 2]$.

### Table of the Example

Here is the step-by-step evaluation table for the function $f(x) = x^3 - x - 2$:

| Iteration ($i$) | Left Boundary ($a$) | Right Boundary ($b$) | Midpoint ($c$) | $f(a)$  | $f(b)$ | $f(c)$  | Interval Width ($\vert{}b-a\vert{}$) |
| --------------- | ------------------- | -------------------- | -------------- | ------- | ------ | ------- | ------------------------------------ |
| 1               | 1.0000              | 2.0000               | 1.5000         | -2.0000 | 4.0000 | -0.1250 | 1.0000                               |
| 2               | 1.5000              | 2.0000               | 1.7500         | -0.1250 | 4.0000 | 1.6094  | 0.5000                               |
| 3               | 1.5000              | 1.7500               | 1.6250         | -0.1250 | 1.6094 | 0.6660  | 0.2500                               |
| 4               | 1.5000              | 1.6250               | 1.5625         | -0.1250 | 0.6660 | 0.2522  | 0.1250                               |
| 5               | 1.5000              | 1.5625               | 1.5313         | -0.1250 | 0.2522 | 0.0591  | 0.0625                               |
| 6               | 1.5000              | 1.5313               | 1.5156         | -0.1250 | 0.0591 | -0.0341 | 0.0313                               |

> [!NOTE]\
> The algorithm stops at iteration 6 because the interval width ($0.0313$) falls below our specified tolerance of $0.05$. The approximated root is $1.5156$.

---

## 4. Order of Convergence Derivation

The order of convergence describes how quickly the error decreases. For the Bisection Method, this is derived by tracking the maximum absolute error at each iteration.

Let the true root be $\alpha \in [a_0, b_0]$.\
The initial interval width is:\
$E_0 = b_0 - a_0$
Since the root $\alpha$ must lie within the interval, the absolute error at any step $n$ is bounded by the length of the interval at that step:\
$e_n = \vert{}c_n - \alpha\vert{} \le \frac{b_n - a_n}{2}$
At each continuous iteration, the interval width is strictly halved:\
$b_1 - a_1 = \frac{b_0 - a_0}{2}$\
$b_2 - a_2 = \frac{b_1 - a_1}{2} = \frac{b_0 - a_0}{2^2}$
Extrapolating this to the $n$-th iteration:\
$b_n - a_n = \frac{b_0 - a_0}{2^n}$
Therefore, the maximum error bound $e_n$ at iteration $n$ is:\
$e_n \le \frac{b_0 - a_0}{2^{n+1}}$
To find the relationship between the error of consecutive iterations, we can look at the error bound for the next step ($e_{n+1}$):\
$e_{n+1} \le \frac{b_0 - a_0}{2^{n+2}} = \frac{1}{2} \left( \frac{b_0 - a_0}{2^{n+1}} \right)$
Substituting the definition of $e_n$ yields:\
$e_{n+1} = \frac{1}{2} e_n$
The general definition for the order of convergence is written as $e_{n+1} = M \cdot e_n^p$, where $p$ is the order of convergence and $M$ is the asymptotic error constant. Comparing this to our equation:

- $M = 0.5$
- $p = 1$
  Thus, the Bisection Method has a linear order of convergence ($p = 1$) with an asymptotic error constant of $0.5$.
