+++
title = "Reinforcement Learning for Humanoid Robots"
author = ["Fangyuan Wang"]
tags = ["humanoid", "rl", "robotic"]
draft = false
+++

RL promises an effective way to learn motor skills by rewarding desirable behaviors and penalizing undesired behaviors, with minimal or no supervision during training. The end-to-end RL policies translate raw sensory input to actuation and are executable in real time.

Some problems encountered:

-   meticulous design of reward functions
    -   **reinforcement learning w/ sparse reward**

-   sim-to-real gap

    Humanoid robots posses higher DoFs and unstable dynamics, where the center of mass constantly moves out of the support polygon.

    -   **domain randomization** by varing the properties of a robot model, such as mass, friction, and actuator dynamics to train a generalized policy.

    -   **system identification** by approximating the system's input-output behavior from real-world data.

    -   **domain adaptation** by using real-world data directly to fine-tune a simulator-trained policy.
