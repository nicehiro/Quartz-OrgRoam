+++
title = "Skew-Fit: State-Covering Self-Supervised Reinforcement Learning"
author = ["Fangyuan Wang"]
tags = ["sequential"]
draft = false
+++

Try to find subgoals by maximizing the [mutual information]({{< relref "20221104114029-mutual_information.md" >}}):

\\[
I(S;G) = H(S) - H(S|G) = H(G) - H(G|S)
\\]

that is trying to maximizing \\(H(S)\\) and minimizing \\(H(S|G)\\).

To minimizing \\(H(S|G)\\), we train a policy by maximizing the reward:
\\[
r = log(G|S)
\\]
which is also the distance between \\(G\\) and \\(S\\). This paper use [RIG]({{< relref "20221119142736-visual_reinforcement_learning_with_imagined_goals.md" >}}) to deal with it.

To maximizing \\(H(S)\\), they add a weight on each state to make the probability of less visited state become bigger.
