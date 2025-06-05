+++
title = "AgiBot World Colosseo: Large-scale Manipulation Platform for Scalable and Intelligent Embodied Systems"
author = ["Fangyuan Wang"]
draft = false
+++

This paper has two major contributions:

1.  proposes a large dataset, containing 217 specific tasks, 87 skills and 106 scenes. Most of tasks involving dual-arm manipulation, dexterous hands, and collaborative tasks.

2.  proposes a hierarchical Vision-Language-Latent-Action (ViLLA) framework with three training stages: latent action model trained by VQ-VAE objective, latent planner (for action latent) trained by VLM backbone-based model, and action expert (for action).

Some interesting things from the paper:

1.  Two-billion parameter scale has proven effective for robotic tasks.

2.  Action chunking set to 30.
