+++
title = "Maximum Likelihood Estimation"
author = ["Fangyuan Wang"]
tags = ["probability"]
draft = false
+++

设总体有分布 \\(f(x;\theta\_1,\dots,\theta\_k)\\) ， \\(X\_1,\dots,X\_n\\) 为自这个总体中抽出的样本，
则样本 \\((X\_1,\dots,X\_n)\\) 的分布（即其概率密度函数或概率函数）为：
\\[
f(x\_1;\theta\_1,\dots,\theta\_k)f(x\_2;\theta\_1,\dots,\theta\_k)\dots f(x\_n;\theta\_1,\dots,\theta\_k)
\\]
记为 \\(L(x\_1,\dots,x\_n;\theta\_1,\dots,\theta\_k)\\) 。

当参数 \\(\theta\_1,\dots,\theta\_k\\) 固定时，函数 \\(L\\) 是一个概率密度函数。
其意义为，样本 \\(X\_1,\dots,X\_n\\) 出现的概率。反过来理解，当 \\(X\_1,\dots,X\_n\\) 固定时，函数 \\(L\\) 的意义为，
给定样本，生成样本的参数为 \\(\theta\_1,\dots,\theta\_k\\) 的概率。但参数没有概率这个说法，就选用了“似然”这个词。

因此，我们要找的参数，其实就是使得 \\(L\\) 最大的参数，即：
\\[
L(X\_1,\dots,X\_n;\theta\_1,\dots,\theta\_n) = \max\_{\theta\_1,\dots,\theta\_n}L(X\_1,\dots,X\_n;\theta\_1,\dots,\theta\_k)
\\]
若 \\(f\\) 连续可导，
\\[
\ln L=\sum\_{i=1}^{n}\ln f(X\_i;\theta\_1,\dots,\theta\_k)
\\]
