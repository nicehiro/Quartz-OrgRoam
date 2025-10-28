+++
title = "One Step Diffusion via Shortcut Models"
author = ["Fangyuan Wang"]
tags = ["diffusion"]
draft = false
+++

Some drawbacks (personaly think) for diffusion / flow matching algorithms:

1.  long forward passes during inference

2.  determined timesteps for all data (which I think should different for different cases, and can be optimized)

This paper introduces shortcut models, a family of generative models that use a single network and training phase to produce high-quality samples in a single or multiple sampling steps.

The key insight is to condition the model not only on the noise level but also the desired step size (can determine the steps). Shortcut models can thus be seen as a generalization of flow-matching models to larger step sizes: whereas flow-matching models only learn the instantaneous velocity, shortcut models additionally learn to make larger jumps. As step size to 0, the shortcut is equivalent to the flow.

Can I use shortcut models as action head in VLA models?
