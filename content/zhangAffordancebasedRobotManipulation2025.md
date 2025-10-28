+++
title = "Affordance-Based Robot Manipulation with Flow Matching"
author = ["Fangyuan Wang"]
draft = false
+++

This paper proposes flow matching policy, that try to minimize the distance between the ground truth trajectory (from initial state to goal) and the predicted one.

The difference between the proposed policy and [Denoising Diffusion Probabilistic Models]({{< relref "hoDenoisingDiffusionProbabilistic2020.md" >}}) policy:

1.  Diffusion policy generates single action or action chunk for current time step from gaussian noise. While flow matching policy generate trajectory of waypoints from noise.

2.  The difference between the flow matching and DDPM:
    -   ODE and SDE
    -   Linear interpolation
