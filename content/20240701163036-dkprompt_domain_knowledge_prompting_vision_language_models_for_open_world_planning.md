+++
title = "DKPROMPT: Domain Knowledge Prompting Vision-Language Models for Open-World Planning"
author = ["Fangyuan Wang"]
tags = ["OWMM", "VLM"]
draft = false
+++

This paper mainly focus on using prompt to generate domain knowledge and then construct the [PDDLStream]({{< relref "20240604144221-pddlstream.md" >}}) to describe the environment.

While purely PDDL doesn't work well in open world where unforeseen situations are common. Actually even we know all objects, it is still hard to extract useful information to describe current state in the real world.
