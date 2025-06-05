+++
title = "Non-parametric algorithm"
author = ["Fangyuan Wang"]
tags = ["ml"]
draft = false
+++

## Description {#description}

To make predictions using locally weighted linear regression,
we need to keep the entire training set around.
The term "non-parametric" roughly refers to the fact that
the amount of stuff we need to keep in order to represent the
hypothesis h grows linearly with the size of the training set.

为了对输入进行预测，我们预测过程中需要保存所有训练集。
在进行预测时，我们需要使用的数据与训练集的大小成正比。
