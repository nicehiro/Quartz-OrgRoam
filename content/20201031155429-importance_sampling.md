+++
title = "Importance Sampling"
author = ["Fangyuan Wang"]
tags = ["probability"]
draft = false
+++

## Description {#description}

Importance Sampling is a technique for estimating the expectation \\(\mu\\) of a
random variable \\(f(x)\\) under distribution \\(p\\) from samples of a different
distribution \\(q\\).

The key observation is that \\(\mu\\) is can expressed as the expectation of a
different random variable \\(f^{\*}(x)=\frac{p(x)}{q(x)}\\) under \\(q\\)

\begin{equation}
\begin{aligned}
\mu &= \mathbf{E}\_{p}[f(x)] \\\\
&= \sum\_{x} p(x)f(x) \\\\
&= \sum\_{x} \frac{q(x)}{q(x)}p(x)f(x) \\\\
&= \sum\_{x} \frac{p(x)}{q(x)} q(x)f(x) \\\\
&= \mathbf{E}\_{q} \frac{p(x)}{q(x)} f(x) \\\\
&= \mathbf{E}\_{q} [f^{\*}(x)]
\end{aligned}
\end{equation}

Technique condition: \\(q\\) must have support everywhere \\(p\\) dose.
Without this condition, the equation is biased!
Note: \\(q\\) can support things that \\(p\\) doesn't.
