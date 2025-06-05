+++
title = "Deterministic Case"
author = ["Fangyuan Wang"]
tags = ["rl", "mbrl"]
draft = false
+++

## Description {#description}

当状态和动作确定时，下一状态也是确定的。即下一状态是由当前状态和动作相关的函数所确定的。
在已知状态转移方程的情况下，Agent 可以依据模型生成一系列的动作。

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-10-1.png" width="100%" >}}

</div>

\\[
\mathbf{a}\_{1}, \ldots, \mathbf{a}\_{T}=\arg \max \_{\mathbf{a}\_{1}, \ldots, \mathbf{a}\_{T}} \sum\_{t=1}^{T} r\left(\mathbf{s}\_{t}, \mathbf{a}\_{t}\right) \text { s.t. } \mathbf{a}\_{t+1}=f\left(\mathbf{s}\_{t}, \mathbf{a}\_{t}\right)
\\]
