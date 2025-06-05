+++
title = "GET-Zero: Graph Embodiment Transformer for Zero-shot Embodiment Generalization"
author = ["Fangyuan Wang"]
tags = ["humanoid-hand", "transformer", "graph"]
draft = false
+++

Current whole-body control methods have incomplete embodiment representations which ignore the graph connectivity of the robot, and thus cannot generalize well to an embodiment with a varied graph structure.

This paper propose Graph Embodiment Transfoer, an encoder that uses the embodiment graph as a structural bias in network architecture. It consists of nodes representing local joint information, directed edges representing links connecting parent and child joints, and undirected edges between joints.

They also propose a parent-child encoding lets the model modulate attention based on directed connectivity of the forward joint chain.
