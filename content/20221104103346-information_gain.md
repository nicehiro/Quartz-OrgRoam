+++
title = "Information Gain"
author = ["Fangyuan Wang"]
tags = ["math", "probability"]
draft = false
+++

In information theory and machine learning, information gain is a synonym for Kullback–Leibler divergence; the amount of information gained about a random variable or signal from observing another random variable. However, in the context of decision trees, the term is sometimes used synonymously with mutual information, which is the conditional expected value of the Kullback–Leibler divergence of the univariate probability distribution of one variable from the conditional distribution of this variable given the other one.

In general terms, the expected information gain is the reduction in information entropy \\(\mathcal{H}\\) from a prior state to a state that takes some information as given:

\\[
I(D,x) = H(D) - H(D|x)
\\]

where \\(H(D|x)\\) is the [Conditional Entropy]({{< relref "20221104104233-conditional_entropy.md" >}}).
