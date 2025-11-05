+++
title = "Horizon Reduction Makes RL Scalable"
author = ["Fangyuan Wang"]
draft = false
+++

This paper studies the scalability of offline RL. In principle, a truly scalable offline RL algorithm should be able to solve any given problem, regardless of its complexity, given sufficient data, compute, and model capacity.

They observe that despite scaling up data, many existing offline RL algorithms exhibit poor scaling behavior, saturating well below the maximum performance. They empirically verify the hypothesize that the horizon is the main cause behind the poor scaling of offline RL.

Many offline RL algos train Q functions via temporal difference (TD) learning. While the TD learning objective has a fundamental limitation: at any gradient step, the prediction target that the algorithm chases is <span class="underline">biased</span>, and these biases accumulate over the horizon.

The method they proposed mainly focused on how to shrink the long horizon into small, by increasing the TD steps, and SHARSA (which calculates high level state value function and action value function over length-n trajectories.
