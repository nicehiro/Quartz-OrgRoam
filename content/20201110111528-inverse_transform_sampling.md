+++
title = "Inverse transform sampling"
author = ["Fangyuan Wang"]
tags = ["probability"]
draft = false
+++

## Description {#description}

已知 \\(U\sim Unif[0,1]\\) ，并且有随机变量 \\(X\\) 的累积分布函数 \\(CDF F\_{X}(x)\\) ，如何生成一个随机数 \\(X\\) ？

如果有一个强变换 \\(T:[0,1]\\) ，使得 \\(T(U)=X\\) ，则
\\[
F\_{X}(x)=Pr(X\leq x)=Pr(T(U)\leq x)=Pr(U\leq T^{-1}(x))=T^{-1}(x),x\in\mathbb{R}
\\]
上诉化简用到了 \\(Pr(U\leq y)=y\\) 这个知识。

因此，我们知道 \\(F\_{X}\\) 和 \\(T\\) 互为反函数，即 \\(T(u)=F\_{X}^{-1}(u),u\in[0,1]\\)
又有 \\(T(U)=X\\) ，所以 \\(X=F\_{X}^{-1}(U)\\) 。

也就是说，如果我们有了 \\([0，1]\\) 的随机分布，就对想要的函数进行采样。
