+++
title = "Gradient Temporal-Difference"
author = ["Fangyuan Wang"]
tags = ["rl"]
draft = false
+++

This method cannot be applied directly to neural network because they involve
projection on to the space of the basis functions.

Moreover, GTD for neural networks has been done only for policy evaluation,
not control.

And the "semi-gradient" TD works faster in practice on almost all problems.


## Reference {#reference}

-   <http://incompleteideas.net/Talks/gradient-TD-2011.pdf>

-   <https://www.reddit.com/r/reinforcementlearning/comments/9dh1th/why_are_gradient_td_methods_not_used_in_deep_rl/>
