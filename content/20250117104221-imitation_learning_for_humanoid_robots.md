+++
title = "Imitation Learning for Humanoid Robots"
author = ["Fangyuan Wang"]
tags = ["robotic", "imitation", "humanoid"]
draft = false
+++

Refer to [Imitation Learning]({{< relref "20250116143119-imitation_learning.md" >}}) for more details.

Four possible source of demonstrations for humanoid robots:

-   policy execution on hardware (robot)
    -   collecting data on physical robots (requires a laborious setup of the environment and raises significant safety concerns)

    -   collecting data in simulation (sim-to-real gap)

-   [Teleoperation]({{< relref "20240826101718-teleoperation.md" >}}) (robot)

    Control flow for learning from teleoperated demonstrations:

    1.  human operator (VR, Exoskeleton, Optical Tracking, Motion Capture, Joystick, ALOHA)

    2.  motion retargeting

    3.  desired robot trajectory

    Some limitations:

    -   a majority of teleoperation systems capture only manipulation skills, full-body sensing, including human gaits are missing (requires IMU or exoskeletons which are expensive)

    -   the teleoperation data may limited if the robot's kinematics do not enable seamless retargeting

    -   time-consuming to scale

-   motion capture from human (3D) (human)

    Captures humans interacting with various objects while moving around.

    -   require heavily instrumented environments and actors

    -   less outdoor activities

-   human videos from internet (2D) (human)

    Obtain rich and diverse human motion datafrom the internet.

    -   lower quality, containing noise, non-physical artifacts
