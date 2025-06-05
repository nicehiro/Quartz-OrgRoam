+++
title = "GHIL-Glue: Hierarchical Control with Filtered Subgoal Images"
author = ["Fangyuan Wang"]
tags = ["manipulation", "diffusion", "subgoal"]
draft = false
+++

The problem with [SUSIE]({{< relref "20240325203016-zero_shot_robotic_manipulation_with_pretrained_image_editing_diffusion_models.md" >}}) or most of current generative models (for high-level planning/subgoal generation) is the performance by the interface between high-level and low-level controllers. This paper tries to filter good subgoals by training a subgoal classifier to predict the likelihood of the transition between the current state and a given subgoal, then sample and choose the best one with highest ranking. It is based on the [SUSIE]({{< relref "20240325203016-zero_shot_robotic_manipulation_with_pretrained_image_editing_diffusion_models.md" >}}).

Something interesting:

1.  Constructing negative examples for training the subgoal classifier: wrong instruction, wrong goal image and reverse direction. The reverse direction negative examples seem new to me.

2.  The subgoals can contain visual artifacts that degrade the performance of both the low-level controller and the subgoal classifier. This performance degradation results from the distribution shift between the subgoal images seen by the policy during training and during inference.
    So still, it is hard to guarantee the quality of the subgoals:

    -   Are subgoals hard for low-level policy to achieve? (feasibility)
    -   Are subgoals correct? (in the subgoal space)
    -   Are subgoals optimal? (optimality)

    This paper actually just solve the first two question.
