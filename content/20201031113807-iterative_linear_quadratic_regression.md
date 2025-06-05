+++
title = "Iterative Linear Quadratic Regression"
author = ["Fangyuan Wang"]
tags = ["math", "lqr", "ilqr"]
draft = false
+++

## Description {#description}

[LQR]({{< relref "20201031112847-linear_quadratic_regression.md" >}}) 方法适用于状态转移方程为线性的，损失函数为二次的环境中，但实际中很多问题都不满足这个条件。
那么我们用一个线性方程来近似拟合现实问题的非线性环境动力学方程吗？

可以使用泰勒展开来近似。
\\[
f\left(\mathbf{x}\_{t}, \mathbf{u}\_{t}\right) \approx f\left(\hat{\mathbf{x}}\_{t}, \hat{\mathbf{u}}\_{t}\right)+\nabla\_{\mathbf{x}\_{t}, \mathbf{u}\_{t}} f\left(\hat{\mathbf{x}}\_{t}, \hat{\mathbf{u}}\_{t}\right)\left[\begin{array}{c}
\mathbf{x}\_{t}-\hat{\mathbf{x}}\_{t} \\\\
\mathbf{u}\_{t}-\hat{\mathbf{u}}\_{t}
\end{array}\right]
\\]
\\[
c\left(\mathbf{x}\_{t}, \mathbf{u}\_{t}\right) \approx c\left(\hat{\mathbf{x}}\_{t}, \hat{\mathbf{u}}\_{t}\right)+\nabla\_{\mathbf{x}\_{t}}, \mathbf{u}\_{t} c\left(\hat{\mathbf{x}}\_{t}, \hat{\mathbf{u}}\_{t}\right)\left[\begin{array}{c}
\mathbf{x}\_{t}-\hat{\mathbf{x}}\_{t} \\\\
\mathbf{u}\_{t}-\hat{\mathbf{u}}\_{t}
\end{array}\right]+\frac{1}{2}\left[\begin{array}{c}
\mathbf{x}\_{t}-\hat{\mathbf{x}}\_{t} \\\\
\mathbf{u}\_{t}-\hat{\mathbf{u}}\_{t}
\end{array}\right]^{T} \nabla\_{\mathbf{x}\_{t}, \mathbf{u}\_{t}}^{2} c\left(\hat{\mathbf{x}}\_{t}, \hat{\mathbf{u}}\_{t}\right)\left[\begin{array}{c}
\mathbf{x}\_{t}-\hat{\mathbf{x}}\_{t} \\\\
\mathbf{u}\_{t}-\hat{\mathbf{u}}\_{t}
\end{array}\right]
\\]

移项之后，化简：
\\[
\bar{f}\left(\delta \mathbf{x}\_{t}, \delta \mathbf{u}\_{t}\right)=\mathbf{F}\_{t}\left[\begin{array}{l}
\delta \mathbf{x}\_{t} \\\\
\delta \mathbf{u}\_{t}
\end{array}\right]
\\]
\\[
\bar{c}\left(\delta \mathbf{x}\_{t}, \delta \mathbf{u}\_{t}\right)=\frac{1}{2}\left[\begin{array}{c}
\delta \mathbf{x}\_{t} \\\\
\delta \mathbf{u}\_{t}
\end{array}\right]^{T} \begin{array}{c}
\mathbf{C}\_{t}\left[\begin{array}{c}
\delta \mathbf{x}\_{t} \\\\
\delta \mathbf{u}\_{t}
\end{array}\right]+\left[\begin{array}{c}
\delta \mathbf{x}\_{t} \\\\
\delta \mathbf{u}\_{t}
\end{array}\right]^{T} \mathbf{c}\_{t}
\end{array}
\\]

其中：
\\[
\mathbf{F}\_t=\nabla\_{\mathbf{x}\_t,\mathbf{u}\_t}f\left(\hat{\mathbf{x}\_t},\hat{\mathbf{u}\_t}\right)
\\]
\\[
\mathbf{C}\_t=\nabla^{2}\_{\mathbf{x}\_t,\mathbf{u}\_t}c\left(\hat{\mathbf{x}\_t},\hat{\mathbf{u}\_t}\right)
\\]
\\[
\mathbf{c}\_t=\nabla\_{\hat{\mathbf{x}\_t},\hat{\mathbf{u}\_t}}c\left(\hat{\mathbf{x}\_t},\hat{\mathbf{u}\_t}\right)
\\]
\\[
\delta\_{\mathbf{x}\_t}=\mathbf{x}\_t-\hat{\mathbf{x}\_t}
\\]
\\[
\delta\_{\mathbf{u}\_t}=\mathbf{u}\_t-\hat{\mathbf{u}\_t}
\\]

我们将其转换成了一个 LQR 问题。至此，我们可以得到 iLQR 算法：

<style>.org-center { margin-left: auto; margin-right: auto; text-align: center; }</style>

<div class="org-center">

{{< figure src="/ox-hugo/lec-10-8.png" width="100%" >}}

</div>
