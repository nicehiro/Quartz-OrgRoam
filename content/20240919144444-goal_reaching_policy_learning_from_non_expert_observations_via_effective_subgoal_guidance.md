+++
title = "Goal-Reaching Policy Learning from Non-Expert Observations via Effective Subgoal Guidance"
author = ["Fangyuan Wang"]
tags = ["rl", "subgoal", "goal-conditioned"]
draft = false
+++

This work tries to tackle long-horizon tasks by leveraging non-expert, action-free observation data, which is novel (idea is used before I think but no one described like that).

It involves training a state-goal value function to encourage informative exploration (used before) and learning a high-level policy that generates reasonable subgoals. For generating subgoals, it uses[ Hindsight Experience Replay]({{< relref "20230210213527-hindsight_experience_replay.md" >}}) to sample goals from either the future states within the same trajectory or random states in the dataset (which I think is not so good).
