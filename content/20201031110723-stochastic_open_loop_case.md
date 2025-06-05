+++
title = "Stochastic Open Loop Case"
author = ["Fangyuan Wang"]
tags = ["rl", "mbrl"]
draft = false
+++

## Description {#description}

当状态和动作确定时，下一状态无法确定，但有一定的分布概率。
在已知状态转移方程的条件下，Agent 依据模型生成一系列的动作。

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-10-2.png" width="100%" >}}

</div>

\begin{array}{c}
p\_{\theta}\left(\mathbf{s}\_{1}, \ldots, \mathbf{s}\_{T} \mid \mathbf{a}\_{1}, \ldots, \mathbf{a}\_{T}\right)=p\left(\mathbf{s}\_{1}\right) \prod\_{t=1}^{T} p\left(\mathbf{s}\_{t+1} \mid \mathbf{s}\_{t}, \mathbf{a}\_{t}\right) \\\\
\mathbf{a}\_{1}, \ldots, \mathbf{a}\_{T}=\arg \max \_{\mathbf{a}\_{1}, \ldots, \mathbf{a}\_{T}} E\left[\sum\_{t} r\left(\mathbf{s}\_{t}, \mathbf{a}\_{t}\right) \mid \mathbf{a}\_{1}, \ldots, \mathbf{a}\_{T}\right]
\end{array}

但其实这种设定是不合理的。即使你知道状态转移方程，由于环境自身的随机性你还是无法判断下个状态。
