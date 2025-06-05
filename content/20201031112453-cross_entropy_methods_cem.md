+++
title = "Cross Entropy Methods(CEM)"
author = ["Fangyuan Wang"]
tags = ["rl"]
draft = false
+++

## Description {#description}

交叉熵方法一般适用于状态空间连续的环境，分布函数一般选择高斯分布。

1.  使用高斯分布 \\(p(A)\\) 生成动作序列 \\(A\_1,\dots,A\_N\\)
2.  计算 \\(J(A\_1),\dots,J(A\_N)\\)
3.  选取上诉计算结果中表现最好（\\(J(A\_i)\\) 值最高）的几组动作序列 \\(A\_{i\_1},\dots,A\_{i\_M}\\) ，其中 \\(M<N\\)
4.  修改高斯分布参数，使得此高斯分布更加贴合 \\(A\_{i\_1},\dots,A\_{i\_M}\\) ，返回 1 步继续执行
