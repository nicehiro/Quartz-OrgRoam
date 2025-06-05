+++
title = "DexMV: Imitation learning for Dexterous Manipulation from Human Videos"
author = ["Fangyuan Wang"]
tags = ["imitation"]
draft = false
+++

This paper proposes a method to extract 3D hand and object poses from human videos, then convert to robot demonstrations. Then they perform imitation learning by augmenting the RL with the collected demonstrations.

For object pose estimation, they use the PVN3D model trained on the YCB dataset to detect objects and estimate 6-DoF poses.

For hand pose estimation, they use MANO model.

For hand poses retargeting to robots, they preseve the Task Space Vectors (TSV) defined from finger tips position to the hand palm position, so that the human and robot hands will have same figer tip position relative to the palm. Besides that, they also includethe TSV from palm to middle phalanx.
