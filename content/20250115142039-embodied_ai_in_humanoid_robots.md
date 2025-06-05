+++
title = "Embodied AI in Humanoid Robots"
author = ["Fangyuan Wang"]
tags = ["robotic", "embodied", "humanoid"]
draft = false
+++

From the perspective of application:

> Humanoid robots are built to (ideally) replicate human motions in performing various human-level skills, such as <span class="underline">locomotion</span>, <span class="underline">manipulation</span>, and <span class="underline">cognitive capabilities</span>.

From the perspective of composition:

> A humanoid robot refers to any anthropomorphic robot that resembles the form of a human. Typically, a humanoid robot possesses a torso, two arms, and two legs, though the degree of anthropomorphism may vary.


## Background {#background}

[Humanoid Locomotion and Manipulation: Current Progress and Challenges in Control, Planning, and Learning]({{< relref "guHumanoidLocomotionManipulation2025.md" >}}) lists background, i.e., definition of locomotion, manipulation, loco-manipulation, whole-body control.


## Learning Loco-manipulation Skills {#learning-loco-manipulation-skills}


### Reinforcement Learning from Scratch {#reinforcement-learning-from-scratch}

Refer to [Reinforcement Learning for Humanoid Robots]({{< relref "20250117104037-reinforcement_learning_for_humanoid_robots.md" >}}).


### Learning from Demonstration {#learning-from-demonstration}

Refer to [Imitation Learning for Humanoid Robots]({{< relref "20250117104221-imitation_learning_for_humanoid_robots.md" >}}).


### Hybrid Models {#hybrid-models}

-   A teacher policy trained from simulation using pure RL. Then a student policy clones the behavior of the teacher.

-   Using IL first to pre-train an policy from demonstration. Then a RL policy fine-tunes the policy.


### Representaion of Skills {#representaion-of-skills}

-   motion Representation

-   goal representation

-   state transition representation


### Learning for Humanoid Loco-manipulation {#learning-for-humanoid-loco-manipulation}

-   most in simulation, the physical interactions with external environment or objects are often oversimplified

-   careful reward design using RL


## Foundation Models for Humanoid Robots {#foundation-models-for-humanoid-robots}


### Applying LLMs/VLMs to Humanoid Robots {#applying-llms-vlms-to-humanoid-robots}

Refer to [Real-World Robot Applications of Foundation Models: A Review]({{< relref "kawaharazukaRealWorldRobotApplications2024.md" >}}).


### Building Humanoid Foundation Models {#building-humanoid-foundation-models}

Refer to [Robotic Foundation Models]({{< relref "20250117103152-robotic_foundation_models.md" >}}) for robotic foundation models.
