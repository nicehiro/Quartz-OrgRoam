+++
title = "Shooting Method"
author = ["Fangyuan Wang"]
tags = ["rl"]
draft = false
+++

## Description {#description}

前面提到的一阶优化方法被称作 `Shooting method` 。它只对动作进行求导，状态是关于动作的函数。

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-10-4.png" width="10%" >}}

</div>

上图横轴是时间，纵轴是状态。给定初始位置之后，选择动作，根据状态转移方程得到下一个状态，直到结束。
可以看到，如果开始的动作发生一个细微的变化，也会对最后的结果造成很大的影响。
