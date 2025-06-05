+++
title = "Multi-Task Reinforcement Learning with Soft Modularization"
author = ["Fangyuan Wang"]
tags = ["multi-task", "rl"]
draft = false
+++

This work proposes a new model which can share the trained policy model with all other task. It's based on the common sense that most of tasks can share the same policy decision part.

Their work consists of two networks: a base policy network for all tasks and a routing network which can provide task specific information to base policy network and guide the base policy to generalized in different tasks.

The paper did mention they can deal with the sequential tasks by routing network by given a sequence. But, still, this algorithm cannot determine the sequence.
