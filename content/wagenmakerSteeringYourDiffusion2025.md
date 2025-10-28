+++
title = "Steering Your Diffusion Policy with Latent Space Reinforcement Learning"
author = ["Fangyuan Wang"]
draft = false
+++

This paper introduces diffusion steering via refinforcement learning, (DSRL) by adapting the BC policy by running RL over its latent-noise space.

Diffusion policy work only if the noise \\(\omega \sim \mathcal{N}(0,I)\\). And if \\(\omega\\) is chosen some other way, the policy will not produce actions that match the distribution of the demonstration. So this paper try to use a new noise policy to modify the distribution of noise \\(\omega\\), choose \\(\omega\\) so that the resulting action leads to a desired result.

The idea is novel, and the results show it work. But there are some reasons why flow matching / diffusion policy choose normal distribution to sample noise. How to ensure the learned noise distribution satisfy the requirements?
