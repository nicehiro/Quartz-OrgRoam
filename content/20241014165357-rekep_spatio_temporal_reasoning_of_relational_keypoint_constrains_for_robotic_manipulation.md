+++
title = "ReKep: Spatio-Temporal Reasoning of Relational Keypoint Constrains for Robotic Manipulation"
author = ["Fangyuan Wang"]
tags = ["robotic", "LLM"]
draft = false
+++

This paper proposes a method, called Relational Keypoint Constraints (ReKep), to mapping a set of 3D keypoints in the environment to a numerical cost (formulate the constraints) by:

1.  detecting keypoints of images using DINOv2
2.  generating python cost functions by using GPT-4o
3.  solving the sense actions of end-effector

The keypoints idea is actually not new, while the proposed ReKep cost is interesting. That makes the proposed method can handle various constraints in the environments, such as:

1.  versatile to diverse tasks
2.  free of manual labeling
3.  optimizable by off-the-shelf solvers to produce robot actions in real-time
