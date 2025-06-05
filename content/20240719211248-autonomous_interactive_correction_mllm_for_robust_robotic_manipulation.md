+++
title = "Autonomous Interactive Correction MLLM for Robust Robotic Manipulation"
author = ["Fangyuan Wang"]
draft = false
+++

This paper propose an Autonomous Interactive Correction (AIC) MLLM, which makes use of previous low-level interaction experiences to correct SE(3) pose predictions. Specifically, AIC MLLM initially fine-tuned to acquire both pose prediction and feedback prompt comprehension abilities.

They designed two types of prompt instructions through interactions with objects:

1.  visual masks to highlight unmovable parts for position correction
    -   is there a red mask in the image? (How to add labels?)
    -   determine if following points (randomly sampled during training) is in the red mask.
    -   specify the successful contact point and orientation of pulling the object (exclude the red mask part).

2.  textual descriptions to indicate potential directions for rotation correction
    -   generate gripper direction based on contact point, joint's type, unmovable parts and joint axis.

All the ground truth used to train the model is actually collected from the simulator. To mitigate error, they introduce noise into the training process.

For Feedback Information Extraction (FIE) during the interaction process:

1.  Position-related Information Extrcation. The objective is to determine if the predicted contact point lies on unmovable part. First, they use off-the-shelf VIP-LLaVA to mark the image and ask if it is unmovable. If the predicated contact point is on unmovable part, then use SAM to perform segmentation with the red dot as the prompt, and select the smallest mask to represent the segmentation of the unmovable part.

2.  Rotation-related Information Extraction. The objective is to obtain joint type and axis direction based on the history interaction attempt.

Several concerns about this paper:

1.  About the ground truth. Simply get the masks, contact point and valid gripper direction from the simulator is not enough.

2.  What's the difference between an unified MLLM (NOT VLA) and LLM/VLA + Other VLMs?
