+++
title = "Zero-Shot Robotic Manipulation with Pretrained Image-Editing Diffusion Models"
author = ["Fangyuan Wang"]
tags = ["diffusion"]
draft = false
+++

SuSIE generates subgoals using an image-editing diffusion model and executes those subgoals using a languages-agnostic low-level policy.

Since subgoal generateing process doesn't require robot actions, they augment the BridgeData (only robot demostrations) with a human manipulation dataset (Something-Something) to train the diffusion model.
