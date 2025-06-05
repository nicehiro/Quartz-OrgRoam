+++
title = "Robot Motion Diffusion Model: Motion Generation for Robotic Character"
author = ["Fangyuan Wang"]
tags = ["diffusion", "robotic", "motion", "humanoid"]
draft = false
+++

This paper leverages a pre-trained imitation policy (Actor) and a pre-trained Motion Diffusion Model (MDM) in a two-stage process. In the first stage, a Critic is trained using motions from the dataset to evaluate the Actor's performance, linking the kinematic inputs to physical feasibility. In the second stage, the learned Critic is used to fine-tune the MDM, aligning it with the charater's limits and ensuring physical feasbility.

In the deployment stage, it will first use MDM to generate a motion target, then use Actor to generate the low-level actions based on current state and the target.
