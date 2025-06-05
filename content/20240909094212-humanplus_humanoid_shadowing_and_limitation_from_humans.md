+++
title = "HumanPlus: Humanoid Shadowing and Limitation from Humans"
author = ["Fangyuan Wang"]
tags = ["robotic", "transformer", "imitation", "humanoid", "teleop"]
draft = false
+++

## Why humanoid robots? {#why-humanoid-robots}

Since our surrounding environments, tasks and tools are structured and designed based on the human morphology, human-sized humanoids are the nature hardware platforms of general-purpose robots for potentially solving all tasks that people can complete.


## Contribution {#contribution}

1.  Using human motion dataset, that covers a wide range of skills, to retarget human poses to humanoid robot, then training a task-agnostic low-level policy called Humanoid Shadowing Transformer conditioning on the retargetd humanoid poses.

    At each time step, the input to the policy is humanoid proprioception (root state, joint positions, joint velocities and last action) and humanoid target pose. They use PPO to train this policy in simulation, where the reward is the sum of terms encouraging matching target poses while saving energy and avoiding food slipping.

2.  They modify the Action Chunking Transformer to develop a decoder-only Humanoid Imitation Transformer for skill policies.


## Limitation {#limitation}

Using a fixed retargeting mapping from human poses to humanoid poses, omitting many human joints that do not exist on our humanoid hardware.
