+++
title = "Policy Adaptation via Language Optimization: Decomposing Tasks for Few-Shot Imitation"
author = ["Fangyuan Wang"]
tags = ["VLM", "subgoal", "imitation", "robotic"]
draft = false
+++

This paper enables a learned language-conditioned robot policy to perform new tasks with only a few demonstrations by using a pre-trained VLM to determine the correct sequence of decomposed subtasks that are in-distribution for the robot policy.

There are two assumptions:

1.  although tasks are unseens, the low-level manipulation skills are same as seen dataset, which means an action library is provided.
2.  the vlm can approximate the distribution of the subtask annotations in the target task, i.e., the action library will be inputed into the VLM.

They also provide two high-level subtasks, for example, "open the drawer" can still be divided into three low-high-level subtasks: "move to handler", "grasp the handler" and "move backwards".

I'm not agree with the definition of optimal solution to the target task: the same subtask sequence can be used to solve the task, regardless of the initial state. That means if the drawer is open, the optimal subtask sequence still needs to open it.
