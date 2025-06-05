+++
title = "Latent Diffusion Planning for Imitation Learning"
author = ["Fangyuan Wang"]
tags = ["imitation", "diffusion"]
draft = false
+++

Current imitation learning requires large amount of expert demonstrations. This paper proposes Latent Diffusion Planning (LDP) to leverage action-free demonstrations for planning, and sub-optimal data for inverse dynamics model (IDM).

1.  Train the latent encoding of the observation by using VAE loss;

2.  Use diffusion model as planner to forecasting a dense trajectory of short-future latent states;

3.  Train diffusion model as IDM to generate actions based on latent states.
