+++
title = "Generalizable Humanoid Manipulation with Improved 3D Diffusion Policies"
author = ["Fangyuan Wang"]
tags = ["gr1", "manipulation", "humanoid", "robotic", "diffusion", "3D"]
draft = false
+++

This paper is using FFTAI GR1 humanoid robot to do manipulation tasks in diverse unseen scenarios by collecting data from teleoperation and diffusion policy.

1.  For removing preparation works on precise camera calibration and fine-grained point cloud segmentation, they use so called egocentric 3D representation, which is the view of the camera itself, rather than the world frame.

2.  They have tested that using end-effector poses or robot joint positions as actions has no significant difference in performance.

3.  Teleoperation by using Apple Vision Pro has a very low latency of approximately 0.5 seconds.
