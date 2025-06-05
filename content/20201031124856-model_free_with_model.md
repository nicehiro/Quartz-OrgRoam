+++
title = "Model Free with Model"
author = ["Fangyuan Wang"]
tags = ["rl", "mbrl"]
draft = false
+++

## Description {#description}

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-12-3.png" width="100%" >}}

</div>

可以看出，免模型的策略梯度方法中，梯度不是相乘而是相加的，因此，如果给定足够多的样本数据，策略梯度是可以收敛的。
但是，直接对模型进行梯度下降的时候，梯度是相乘的，因此很容易发生梯度爆炸。

提出一种 Dyna 算法，它的本质是在线 Q-Learning 算法的一种改进。

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-12-4.png" width="100%" >}}

</div>
