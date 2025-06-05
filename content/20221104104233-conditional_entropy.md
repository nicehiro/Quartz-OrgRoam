+++
title = "Conditional Entropy"
author = ["Fangyuan Wang"]
tags = ["probability", "math"]
draft = false
+++

In information theory, the conditional entropy quantifies the amount of information needed to describe the outcome of a random variable Y given that the value of another random variable X, X is known. Here, information is measured in shannons, nats, or hartleys. The entropy of Y conditioned on X is written as \\(\mathcal{H}(Y|X)\\).

Remember, the entropy means the uncertainty of the variable. Thus the conditional entropy means the uncertainty of \\(Y\\) when knowing \\(X\\).

\begin{align\*}
\mathcal{H}(Y|X) &= - \sum\_{x,y} p(x, y) \log p(y|x) \\\\
&= - \sum\_{x,y} p(x,y) \log \frac{p(x,y)}{p(x)}
\end{align\*}
