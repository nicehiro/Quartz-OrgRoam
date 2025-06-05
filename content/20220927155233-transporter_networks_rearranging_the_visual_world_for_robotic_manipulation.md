+++
title = "Transporter Networks: Rearranging the Visual World for Robotic Manipulation"
author = ["Fangyuan Wang"]
tags = ["imitation", "rl"]
draft = false
+++

This work consider tasks that can be completed by a sequence of two-pose motion primitives: pick and place. Thus this is a optimal pick and place problem.

They use data collected by experts to train their pick and place model. Pick model take as the input the observation, and output the pixel position of the pick location. The Place model take as the input the observation and pick location, output the pixel position of the place location. More detailed information can check the paper.

Problems:

1.  train one model for each specific model
2.  imitation learning needs so much experts work
