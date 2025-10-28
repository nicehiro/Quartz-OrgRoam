+++
title = "Flow Matching for Gaussian Probability Paths"
author = ["Fangyuan"]
draft = false
+++

## Probability Path {#probability-path}


### Conditional Gaussian Probability Path {#conditional-gaussian-probability-path}

The Gaussian conditional probability path forms the foundation of denoising diffusion models and flow matching.

**Definition**: Let \\(\alpha\_t\\), \\(\beta\_t\\) be noise schedulers: two continuously differentiable, monotonic functions with boundary conditions \\(\alpha\_0 = \beta\_1 = 0\\) and \\(\alpha\_1 = \beta\_0 = 1\\). We define the <span class="underline">conditional probability path</span> as a family of distribution \\(p\_t(x|z)\\) over \\(\mathbb{R}^d\\):

\\[
p\_t(\cdot | z) = \mathcal{N}(\alpha\_t z, \beta\_t^2 I\_d)
\\]

**Boundary Conditions**: The imposed conditions on \\(\alpha\_t\\) and \\(\beta\_t\\) ensure:

\\[
p\_0(\cdot | z) = \mathcal{N}(0, I\_d), \text{ and  } p\_1(\cdot | z) = \mathcal{N}(z, 0) = \delta\_z
\\]

where \\(z \in \mathbb{R}^d\\) is a data point, \\(\delta\_z\\) is the Dirac delta "distribution" that sample from \\(\delta\_z\\) always returns \\(z\\).


### Marginal Gaussian Probability Path {#marginal-gaussian-probability-path}

**Sampling Procedure**: For \\(z \sim p\_{data}\\), \\(\epsilon \sim p\_{init} = \mathcal{N}(0,I\_d)\\), we can sample from marginal path:

\\(x\_t = \alpha\_t z + \beta\_t \epsilon \sim p\_t\\)

This provides a tracable way to sample from the marginal distribution \\(p\_t(x) = \int p\_t(x|z) p\_{data}(z) dz\\).


## Vector Field {#vector-field}


### Conditinoal Gaussian Vector Field {#conditinoal-gaussian-vector-field}

**Definition**: Let \\(\dot{\alpha\_t} = \partial\_t\alpha\_t\\) and \\(\dot{\beta\_t} = \partial\_t\beta\_t\\) denote respective time derivatives of \\(\alpha\_t\\) and \\(\beta\_t\\). The conditional Gaussian vector field given by:

\\[
u\_t^{targe} (x|z) = (\dot{\alpha\_t} - \frac{\dot{\beta\_t}}{\beta\_t} \alpha\_t) z + \frac{\dot{\beta\_t}}{\beta\_t} x
\\]

is a valid conditional vector field model.

**Property**: This vector field generates ODE trajectories \\(X\_t\\) that satisfy \\(X\_t \sim p\_t(\cdot | z) = \mathcal{N}(\alpha\_t z, \beta\_t^2 I\_d)\\) if \\(X\_0 \sim \mathcal{N}(0, I\_d)\\).


#### Proof {#proof}

Construct a <span class="underline">conditional flow model</span> \\(\psi\_t^{targe}(x|z)\\) by defining

\\[
\psi\_t^{targe} (x|z) = \alpha\_t z + \beta\_t x
\\]

If \\(X\_t\\) is the ODE trajectory of \\(\psi\_t^{target}(\cdot| z)\\) with \\(X\_0 \sim p\_{init} = \mathcal{N}(0,I\_d)\\), then

\\[
X\_t = \psi\_t^{target} (X\_0 | z) = \alpha\_t z + \beta\_t X\_0 \sim \mathcal{N}(\alpha\_t z, \beta\_t^2 I\_d) = p\_t(\cdot| z)
\\]

The conditional vector field is:

$$
\begin{aligned}
\frac{d}{dt}\psi_t^{\text{target}}(x|z) &= u_t^{\text{target}}(\psi_t^{\text{target}}(x|z)|z) \quad \text{for all } x, z \in \mathbb{R}^d \\
\stackrel{(i)}{\Leftrightarrow} \dot{\alpha}_t z + \dot{\beta}_t x &= u_t^{\text{target}}(\alpha_t z + \beta_t x|z) \quad \text{for all } x, z \in \mathbb{R}^d \\
\stackrel{(ii)}{\Leftrightarrow} \dot{\alpha}_t z + \dot{\beta}_t \left(\frac{x - \alpha_t z}{\beta_t}\right) &= u_t^{\text{target}}(x|z) \quad \text{for all } x, z \in \mathbb{R}^d \\
\stackrel{(iii)}{\Leftrightarrow} \left(\dot{\alpha}_t - \frac{\dot{\beta}_t}{\beta_t}\alpha_t\right) z + \frac{\dot{\beta}_t}{\beta_t}x &= u_t^{\text{target}}(x|z) \quad \text{for all } x, z \in \mathbb{R}^d
\end{aligned}
$$

In (ii), we reparameterized \\(x \rightarrow (x - \alpha\_t z) / \beta\_t\\).


## Score Function for Conditional Gaussian Probability Paths {#score-function-for-conditional-gaussian-probability-paths}

For the Gaussian path \\(p\_t(x|z) = \mathcal{N}(x;\alpha\_t z, \beta\_t^2 I\_d)\\), we can use the form of the Gaussian probability density to get the <span class="underline">conditional Gaussian score function</span>, which is the derivetive of \\(x\\),

\\[
\nabla \log p\_t(x|z) = - \frac{x - \alpha\_t z}{\beta\_t^2}
\\]

This linear relationship is a unique property of Gaussian distributions and is fundamental to efficient training.


## Flow Matching for Gaussian Conditional Probability Paths {#flow-matching-for-gaussian-conditional-probability-paths}

The conditional flow matching loss is

$$
\begin{align*}
\mathcal{L}_{\text{CFM}}(\theta)
&= \mathbb{E}_{t \sim \text{Unif}(0,1),\, z \sim p_{\text{data}},\, x \sim \mathcal{N}(\alpha_t z, \beta_t^2 I_d)}
\left[\left\|u_t^{\theta}(x)
- \left(\dot{\alpha}_t - \frac{\dot{\beta}_t}{\beta_t}\alpha_t\right)z
- \frac{\dot{\beta}_t}{\beta_t}x
\right\|^2\right] \\
&\stackrel{(i)}{=}
\mathbb{E}_{t \sim \text{Unif}(0,1),\, z \sim p_{\text{data}},\, \epsilon \sim \mathcal{N}(0, I_d)}
\left[\left\|u_t^{\theta}(\alpha_t z + \beta_t \epsilon)
- (\dot{\alpha}_t z + \dot{\beta}_t \epsilon)
\right\|^2\right]
\end{align*}
$$

In (i) we replace \\(x\\) by \\(\alpha\_t z + \beta\_t \epsilon\\).

Let us make \\(\mathcal{L}\_{\text{CFM}}\\) even more concrete for the special case of \\(\alpha\_t = t\\), and \\(\beta\_t = 1-t\\). The corresponding conditional probability path \\(p\_t(x|z) = \mathcal{N}(tz, (1-t)^2)\\) is referred to as the (Gaussian) <span class="underline">CondOT probability path</span>. Then we have \\(\dot{\alpha\_t} = 1, \dot{\beta\_t} = -1\\), so that

$$
\mathcal{L}_{\text{CFM}}(\theta)
= \mathbb{E}_{t \sim \text{Unif},\, z \sim p_{\text{data}},\, \epsilon \sim \mathcal{N}(0, I_d)}
\left[\left\|u_t^{\theta}(t z + (1-t)\epsilon) - (z - \epsilon)\right\|^2\right]
$$

Models like Stable Diffusion 3, Meta's Movie Gen Video are using this procedure.


### Training Procedure {#training-procedure}

Given a dataset of samples \\(z \sim p\_{data}\\), vector field network \\(u\_t^{\theta}\\). For each batch of data:

1.  Sample a data example \\(z\\) from the dataset,

2.  Sample a random time \\(t \sim \text{Unif}\_[0,1]\\),

3.  Sample noise \\(\epsilon \sim \mathcal{N}(0, I\_d)\\)

4.  Set \\(x = tz + (1-t)\epsilon\\)

5.  Compute loss \\(\mathcal{L}\_{\theta} = || u\_t^{\theta}(x) - (z-\epsilon) ||^2\\)

6.  Update the model.


## Score Matching for Gaussian Probability Paths {#score-matching-for-gaussian-probability-paths}

The conditional score matching loss is

$$
\begin{align*}
\mathcal{L}_{\text{CSM}}(\theta) &= \mathbb{E}_{t\sim\text{Unif}, z\sim p_{data}, x\sim p_t(\cdot|z)} [|| s_t^{\theta}(x) + \frac{x - \alpha_t z}{\beta_t^2} ||^2] \\
&= \mathbb{E}_{t\sim\text{Unif}, z\sim p_{data}, \epsilon \sim \mathcal{N}(0, I_d)} [|| s_t^{\theta}(\alpha_t z + \beta_t \epsilon) + \frac{\epsilon}{\beta_t} ||^2] \\
&= \mathbb{E}_{t\sim\text{Unif}, z\sim p_{data}, \epsilon \sim \mathcal{N}(0, I_d)} [\frac{1}{\beta_t^2} || \beta_t s_t^{\theta}(\alpha_t z + \beta_t \epsilon) + \epsilon ||^2]
\end{align*}
$$

Note that \\(s\_t^{\theta}\\) learns to predict the noise that was used to corrupt a data sample \\(z\\). Therefore, the above training loss is also called <span class="underline">denoising score matching</span>. It was soon realized that the above loss is numerically unstable for \\(\beta\_t \approx 0\\) close to zero (i.e. denoising score matching only works if you add a sufficient amount of noise).

In Denosing Diffusion Probabilitic Models (DDPM), it was proposed to drop the constant \\(\frac{1}{\beta\_t^2}\\) in the loss, and reparameterize \\(s\_t^{\theta}\\) into a noise predictor network \\(\epsilon\_t^{\theta}\\) via:

\\[
-\beta\_t s\_t^{\theta}(x) = \epsilon\_t^{\theta}(x)
\\]

thus,

\\[
\mathcal{L}\_{\text{DDPM}}(\theta) = \mathbb{E}\_{t\sim\text{Unif}, z\sim p\_{data}, \epsilon \sim \mathcal{N}(0, I\_d)} [|| \epsilon\_t^{\theta}(\alpha\_t z + \beta\_t \epsilon) - \epsilon ||^2]
\\]
