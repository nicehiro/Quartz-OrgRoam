+++
title = "Stochastic Close Loop Case"
author = ["Fangyuan Wang"]
tags = ["rl", "mbrl"]
draft = false
+++

## Description {#description}

当状态和动作确定时，下一状态无法确定。Agent 可以依据模型生成一个策略，即每走一步，生成一步的动作。

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-10-3.png" width="100%" >}}

</div>

\begin{array}{c}
p\left(\mathbf{s}\_{1}, \mathbf{a}\_{1}, \ldots, \mathbf{s}\_{T}, \mathbf{a}\_{T}\right)=p\left(\mathbf{s}\_{1}\right) \prod\_{t=1}^{T} \pi\left(\mathbf{a}\_{t} \mid \mathbf{s}\_{t}\right) p\left(\mathbf{s}\_{t+1} \mid \mathbf{s}\_{t}, \mathbf{a}\_{t}\right) \\\\
\pi=\arg \max \_{\pi} E\_{\tau \sim p(\tau)}\left[\sum\_{t} r\left(\mathbf{s}\_{t}, \mathbf{a}\_{t}\right)\right]
\end{array}
