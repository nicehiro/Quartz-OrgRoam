+++
title = "Knapsack Problem"
author = ["Fangyuan Wang"]
draft = false
+++

## Problem Definition {#problem-definition}

Given a set of \\(n\\) items \\(X\\), size \\(s\_i \geq 0\\), values \\(v\_i \geq 0\\), a weight limit \\(B\\), and a target value \\(V\\), is there a subset \\(S \subseteq X\\) such that:
\\(\sum\_{i\in S} s\_i \leq B\\) and \\(\sum\_{i \in S} v\_i \geq V\\)


## Prove Knapsack problem is [NP-complete]({{< relref "20231030205540-np_complete.md" >}}) {#prove-knapsack-problem-is-np-complete--20231030205540-np-complete-dot-md}

1.  Prove Knapsack problem is NP.
2.  Choose [Subset Sum Problem]({{< relref "20231030210830-subset_sum_problem.md" >}})
3.  Prove that [Subset Sum Problem]({{< relref "20231030210830-subset_sum_problem.md" >}}) \\(\leq\_P\\) Knapsack Problem.
    Given Subset Sum instance \\(w\_1, \cdots, w\_n\\) and an integer \\(W\\), set \\(s\_i = v\_i = w\_i\\) and \\(B = V = W\\).
