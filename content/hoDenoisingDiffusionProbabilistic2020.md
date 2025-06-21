+++
title = "Denoising Diffusion Probabilistic Models"
author = ["Fangyuan Wang"]
tags = ["diffusion"]
draft = false
+++

Diffusion models are latent variable models of the form \\(p\_{\theta} := \int p\_{\theta}(x\_{0:T}) dx\_{1:T}\\), where \\(x\_1, \cdots, x\_T\\) are latents of the <span class="underline">same dimensionality</span> as the data \\(x\_0 \sim q(x\_0)\\). \\(x\_0\\) represents true data observations such as natural images, \\(x\_T\\) represents pure Gaussian noise, and \\(x\_t\\) is an intermediate noisy version of \\(x\_0\\). The joint distribution \\(p\_{\theta}(x\_{0:T})\\) is called the **reverse process**, and it is defined as a Markov chain (shown in Fig.1) with learned Gaussian transitions starting at \\(p(x\_T) = \mathcal{N}(x\_T; 0, I)\\):

\\[
p\_{\theta}(x\_{0:T}) := p(x\_T) \prod\_{t=1}^T p\_{\theta}(x\_{t-1} | x\_t)
\\]

where \\(p\_{\theta}(x\_{t-1}|x\_t) := \mathcal{N}(x\_{t-1}; \mu\_{\theta}(x\_t, t), \Sigma\_{\theta}(x\_t, t))\\).

{{< figure src="/ox-hugo/representation-of-diffusion-models.png" >}}

What distinguishes diffusion models from other types of latent variable models is that the approximate posterior \\(q(x\_{1:T}|x\_0)\\), called the <span class="underline">forward process</span> or <span class="underline">diffusion process</span>, is fixed to a Markov chain that gradually adds Gaussian noise to the data according to a variance schedule.


## Diffusion Process {#diffusion-process}

For a diffusion process from \\(x\_{t-1}\\) to \\(x\_t\\),

\\[
x\_t = \alpha\_t x\_{t-1} + \beta\_t \epsilon\_t, \epsilon\_t \sim \mathcal{N}(0, I)
\\]

where \\(\alpha\_t, \beta\_t > 0\\) and \\(\alpha\_t^2 + \beta\_t^2 = 1\\). Generally, \\(\beta\_t\\) always close to \\(0\\) and can be considered as noise degree and \\(\epsilon\_t\\) is the Gaussian noise to diffuse \\(x\_{t-1}\\).

Thus we can get:

$$

\begin{aligned}
x\_t &= \alpha\_t x\_{t-1} + \beta\_t \epsilon\_t \\\\
&= \alpha\_t (\alpha\_{t-1}x\_{t-2} + \beta\_{t-1}\epsilon\_{t-1}) + \beta\_t\epsilon\_t \\\\
&= \dots \\\\
&= (\alpha\_t \cdots \alpha\_1)x\_0 + (\alpha\_t \cdots \alpha\_2)\beta\_1\epsilon\_1 + (\alpha\_t \cdots \alpha\_3) \beta\_2 \epsilon\_2 + \cdots + \alpha\_t\beta\_{t-1}\epsilon\_{t-1} + \beta\_t\epsilon\_t
\end{aligned}

$$

Since \\(\epsilon\_t \sim \mathcal{N}(0, I)\\), so \\((\alpha\_t \cdots \alpha\_2)\beta\_1\epsilon\_1 \sim \mathcal{N}(0, (\alpha\_t \cdots \alpha\_2)^2\beta\_1^2)\\), so as others. Thus \\((\alpha\_t \cdots \alpha\_2)\beta\_1\epsilon\_1 + (\alpha\_t \cdots \alpha\_3) \beta\_2 \epsilon\_2 + \cdots + \alpha\_t\beta\_{t-1}\epsilon\_{t-1} + \beta\_t\epsilon\_t \sim \mathcal{N}(0, (\alpha\_t \cdots \alpha\_2)^2\beta\_1^2 + \cdots + \alpha\_t^2\beta\_{t-1}^2 + \beta\_t^2)\\).

When \\(\alpha\_t^2 + \beta\_t^2 = 1\\),

\\[
(\alpha\_t \cdots \alpha\_1)^2 + (\alpha\_t \cdots \alpha\_2)^2\beta\_1^2 + (\alpha\_t \cdots \alpha\_3)^2\beta\_2^2 + \cdots + \alpha\_t^2\beta\_{t-1}^2 + \beta\_t^2 = 1
\\]

So \\(x\_t = \bar{\alpha}\_t x\_0 + \bar{\beta}\_t \bar{\epsilon\_t}\\), where \\(\bar{\epsilon}\_t \sim \mathcal{N}(0, I)\\), \\(\bar{\alpha}\_t = (\alpha\_t \cdots \alpha\_1), \bar{\beta}\_t =  \sqrt{1 - (\alpha\_t \cdots \alpha1)^2}\\).


## Reverse Process {#reverse-process}

We are trying to minimize the distance between original image \\(x\_{t-1}\\) and de-noised image \\(\theta(x\_t)\\), i.e.:

$$

\begin{aligned}
\mathcal{L} &= || x\_{t-1} - \theta(x\_t) ||^2 \\\\
&= || \frac{1}{\alpha\_t}(x\_t - \beta\_t \epsilon\_t) - \theta(x\_t) ||^2 \\\\
&= || \frac{1}{\alpha\_t}(x\_t - \beta\_t \epsilon\_t) - \frac{1}{\alpha}(x\_t - \beta\_t \epsilon\_{\theta}(x\_t, t)) ||^2 \\\\
&= \frac{\beta\_t^2}{\alpha\_t^2} || \epsilon\_t - \epsilon\_{\theta}(x\_t, t) || ^2 \\\\
&\approx || \epsilon\_t - \epsilon\_{\theta}(\alpha\_t x\_{t-1} + \beta\_t \epsilon\_t, t) || ^2 \\\\
&= || \epsilon\_t - \epsilon\_{\theta}(\alpha\_t (\bar\_{\alpha}\_{t-1} x\_0 + \bar{\beta}\_{t-1}\bar{\epsilon}\_{t-1}) + \beta\_t \epsilon\_t, t) || ^2 \\\\
&= || \epsilon\_t - \epsilon\_{\theta}(\bar{\alpha}\_t x\_0 + \alpha\_t \bar{\beta}\_{t-1}\bar{\epsilon}\_{t-1} + \beta\_t\epsilon\_t, t) || ^2
\end{aligned}

$$

We resample \\(x\_t\\) without \\(\bar{\epsilon}\_t\\) because \\(\epsilon\_t\\) and \\(\bar{\epsilon}\_t\\) are not independent.

Currently we have four variable need to sample: \\(x\_0\\), \\(\epsilon\_t\\), \\(\bar{\epsilon}\_t\\) and \\(t\\). We can use a trick to reduce the variance of training by combining \\(\epsilon\_t\\) and \\(\bar{\epsilon}\_t\\):
