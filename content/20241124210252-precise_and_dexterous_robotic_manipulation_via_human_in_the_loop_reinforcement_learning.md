+++
title = "Precise and Dexterous Robotic Manipulation via Human-in-the-Loop Reinforcement Learning"
author = ["Fangyuan Wang"]
tags = ["robotic", "manipulation", "rl"]
draft = false
+++

## What is this? {#what-is-this}

This paper aims to solve problem that RL methods always only effective for training in simulation due to issues with sample complexity (from real world), assumptions (given reward functions), and optimization stability (the observation is various alot). They do this by:

1.  Using a trained classifier as sparse reward function from human demonstrations.
2.  Using trained ResNet-10 model to generate embeddings of image inputs.
3.  A human can intervene at any time step, then takes control of the robot for up to many steps.
4.  The left training process is basiclly the SERL.


## Some ideas maybe useful {#some-ideas-maybe-useful}

1.  The result of RL in performance that not only exceeds that of hand-designed controllers but also surpasses human teleoperation.
2.  Use an impedance controller with reference limiting in the real-time layer to ensure safety. This is importance and useful in real-world robots.
3.  The sample complexity of learning an optimal policy is closely tied to the cardinality of the state and action spaces as well as the task horizon.
