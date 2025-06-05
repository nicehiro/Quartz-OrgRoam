+++
title = "Improving Vision-Language-Action Model with Online Reinforcement Learning"
author = ["Fangyuan Wang"]
tags = ["VLA"]
draft = false
+++

The fine-tuning of VLA models generally employs a supervised fine-tuning (SFT) approach. However, SFT depends on high-quality expert datasets that are costly and difficult to obtain in the robotic domain. And SFT may not fully align VLA models with physical environments due to distribution shif issues.

This paper starts with a VLA model fine-tuned on robotic demonstrations, which includes VLM parameters \\(\theta\\) and low-level action head parameters \\(\psi\\). The learning contains three stages:

1.  Supervised learning on expert dataset to obtain the initial VLA model. Fine-tuning \\(\theta\\) and \\(\psi\\).

2.  Online RL with frozen VLM to fine-tune the action head.

3.  Supervised learning on both expert and online-collected data.

The problem is that online RL is not easy for robots, especially humanoid robots. Can we use offline RL?
