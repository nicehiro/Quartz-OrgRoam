+++
title = "Humanoid Teleoperation"
author = ["Fangyuan Wang"]
tags = ["teleop", "humanoid"]
draft = false
+++

## What is humanoid teleoperation? {#what-is-humanoid-teleoperation}

Humanoid teleoperation refers to the remote control of a humanoid robot by a human operator. It allows to guide and control the movements and actions of humanoid robots in <span class="underline">real-time</span>, often from a <span class="underline">distance</span>.


## Why humanoid teleoperation? {#why-humanoid-teleoperation}

-   Remote task execution.

-   Data collection for AI training.


## Humanoid teleoperation for data collection {#humanoid-teleoperation-for-data-collection}

To best unlock humanoid's potensial as one of the most promising physical embodiments of general intelligence, one potential answer is to collect large-scale human demonstration data in the real world and learning humanoid skills from it. Here we get the human demonstration data.

Then how to use those data for humanoid robots? There are three ways:

-   Teleoperation (retargeting).

-   Imitation learning.

-   Collect new dataset conducted by humanoid robots using teleoperation. Use those data for imitation learning.


### What's the difference between above three methods? {#what-s-the-difference-between-above-three-methods}

1.  Teleoperation only mapping joint values from human demonstration to the robot, lacking of generalization.

2.  Learning directly from human demonstration doesn't consider the morphological differences, like different body structures, joint configurations, and physical capabilities:
    -   Not all human motions can be directly;

    -   Sensor limitations. Retargeting can provide more structured and robot-specific data.
