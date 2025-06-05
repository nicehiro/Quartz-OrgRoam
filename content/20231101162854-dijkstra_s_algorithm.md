+++
title = "Dijkstra's Algorithm"
author = ["Fangyuan Wang"]
tags = ["shortest", "path"]
draft = false
+++

We want to get the shortest path starting from \\(s\\) to other nodes.

Let \\(S\\) be the explored nodes. For \\(u \in S\\), \\(d[u] =\\) length of a shortest path from \\(s\\) to \\(u\\).

For \\(x \notin S\\), \\(d(x) = \min\_{(r,x):r \in S}{d[r] + l(r,x)}\\).

It requires no negative values of vertex.

Running time is \\(O(mn)\\). Can be improved to \\(O(m\log n)\\) via priority queue.

Cannot handle the graph with negative cycle.
