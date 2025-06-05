+++
title = "Partial Derivative"
author = ["Fangyuan Wang"]
tags = ["math"]
draft = false
+++

## Description {#description}

一个多元函数，对其中一个变量微分，而保持其他变量恒定（相对于全导数，其所有变量都允许变化）。

设函数 \\(z=f(x,y)\\) 在点 \\((x\_0,y\_0)\\) 的某一邻域内有定义，
当 \\(y\\) 固定在 \\(y\_0\\) 而 \\(x\\) 在 \\(x\_0\\) 处有增量 \\(\delta x\\) 时，相应的函数有增量

\\[
f(x\_0+\delta x,y\_0)-f(x\_0,y\_0)
\\]

如果

\\[
\lim\_{\delta x\rightarrow 0} \frac{f(x\_0+\delta x,y\_0)-f(x\_0,y\_0)}{\delta x}
\\]

存在，则称此极限为函数 \\(f(x,y)\\) 在点 \\((x\_0,y\_0)\\) 处对 \\(x\\) 的偏导数。


## 几何意义 {#几何意义}

函数 \\(z=f(x,y)\\) 对 \\(x\\) 的偏导数，就是其在 \\(xoz\\) 平面上的投影对 \\(x\\) 的导数。


## Ref {#ref}

-   <https://www.zhihu.com/question/26966355/answer/154857139>
