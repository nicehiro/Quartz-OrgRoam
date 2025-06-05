+++
title = "Steering Your Generalists: Improving Robotic Foundation Models via Value Guidance"
author = ["Fangyuan Wang"]
draft = false
+++

This paper presents a general approach that enhances the performance of current general robot policies (VLAs) by re-ranking their actions according to a value function learned via offline RL.

One of key concepts of this paper is:

To convert the dataset, which only contains trajectory and annotation, to a form that is amenable to train a Q-function, they annotate the last \\(H\\) transitions of this trajectory with a sparse binary reward value of \\(+1\\) to indicate completion of the task specified by the language instruction. The reward values for all other transitions in this trajectory are marked as \\(0\\).

They use Calibrated Q-Learning (Cal-QL) to train the value function.
