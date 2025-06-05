+++
title = "Collocation Method"
author = ["Fangyuan Wang"]
tags = ["rl"]
draft = false
+++

## Description {#description}

`Collocation method` 对状态和动作求导，有约束性。
\\[
\min \_{\mathbf{u}\_{1}, \ldots, \mathbf{u}\_{T}, \mathbf{x}\_{1}, \ldots, \mathbf{x}\_{T}} \sum\_{t=1}^{T} c\left(\mathbf{x}\_{t}, \mathbf{u}\_{t}\right) \text { s.t. } \mathbf{x}\_{t}=f\left(\mathbf{x}\_{t-1}, \mathbf{u}\_{t-1}\right)
\\]

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-10-5.png" width="100%" >}}

</div>
