+++
title = "OmniH2O: Universal and Dexterous Human-to-Humanoid Whole-Body Teleoperation and Learning"
author = ["Fangyuan Wang"]
tags = ["robotic", "transformer", "humanoid", "teleop"]
draft = false
+++

This paper proposes a learning-based system for whole-body humanoid teleoperation.

They first retargeting human data to humanoid robots. And then use privileged data (joint positions and rotations, velocities and so on) extracted from the simulation environment and RL to train a teacher policy, and do sim-to-real supervised learning in next phrase.

They also provide a dataset that contains first-person RGBD camera views, control input, and whole-body motor actions.
