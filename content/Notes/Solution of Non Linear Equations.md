---
title: Solution of Non Linear Equations
publish: true
---
==2026-09-06==
# Solution of Non Linear Equations

There are two ways to find solution of non-linear equations.

> [!note]
> Each method in below ways have same algorithm, so if you know the algorithm for bisection method, you know for all boundry methods.

- [[Boundry Methods for Solving Non-Linear Equations|Boundry methods]]
	- [[Bisection Method]]
	$$
	x = \frac{a+b}{2}
	$$
	- Regula Falsi / False Position Method
	$$
	x = \frac{a \cdot f(b)-b \cdot f(a)}{f(b)-f(a)}
	$$
- [[Iterative method for Solving Non-Linear Equations|Iterative methods]]
	- Newton-Raphson Method
	$$
	x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
	$$
	- Secant Method
	$$
	x_{n+1} = x_n - \frac{f(x_n)(x_n - x_{n-1})}{f(x_n) - f(x_{n-1})}
	$$
	- Fixed point iteration method
$$
x_{n+1} = g(x_n) \quad\text{where, }|g'(x)| < 1
$$
## Summary Table

| Method                             | Main Formula                                                        | Error Bound Formula / Form                                                                                  | Convergence Criteria (Sufficient Condition)                                        | Order of Convergence                  |
| ---------------------------------- | ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ------------------------------------- |
| Bisection                          | $x_n = \frac{a_n + b_n}{2}$                                         | $\lvert x_n - p \rvert \leq \frac{b - a}{2^n}$                                                              | $f(a) \cdot f(b) < 0$ and $f(x)$ is continuous on $[a,b]$.                         | $1$ (Linear, with rate $S = 0.5$)     |
| False Position  <br>(Regula Falsi) | $x_n = b_n - \frac{f(b_n)(b_n - a_n)}{f(b_n) - f(a_n)}$             | $\lvert x_n - p \rvert \leq M \cdot c^n$  <br>_(Varies based on inactive bound)_                            | $f(a) \cdot f(b) < 0$ and $f(x)$ is continuous on $[a,b]$.                         | $1$ (Linear)                          |
| Secant                             | $x_{n+1} = x_n - \frac{f(x_n)(x_n - x_{n-1})}{f(x_n) - f(x_{n-1})}$ | $\lvert e_{n+1} \rvert \approx \lvert \frac{f''(p)}{2f'(p)} \rvert \lvert e_n \rvert \lvert e_{n-1} \rvert$ | Initial guesses $x_0, x_1$ must be sufficiently close to root $p$.                 | $\approx 1.618$ (Golden Ratio)        |
| Newton-Raphson                     | $x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$                            | $\lvert e_{n+1} \rvert \approx \lvert \frac{f''(p)}{2f'(p)} \rvert \lvert e_n \rvert^2$                     | $\lvert \frac{f(x) \cdot f''(x)}{[f'(x)]^2} \rvert < 1$ near root; $f'(p) \neq 0$. | $2$ (Quadratic for simple roots)      |
| Fixed-Point Iteration              | $x_{n+1} = g(x_n)$                                                  | $\lvert x_n - p \rvert \leq \frac{k^n}{1-k} \lvert x_1 - x_0 \rvert$                                        | $\lvert g'(x) \rvert \leq k < 1$ for all $x$ in the interval.                      | $1$ (Linear, assuming $g'(p) \neq 0$) |

## Key Definitions:
- $p$: The exact true root being sought ($f(p) = 0$ or $g(p) = p$).
- $e_n$: The error at step $n$, defined as $e_n = x_n - p$.
- $[a, b]$: The boundary interval tracking the bracketed root.