+++
title = "Emacs Org LaTeX Preview Error"
author = ["Fangyuan Wang"]
tags = ["latex", "orgmode", "emacs"]
draft = false
+++

Remember to check the `*Org Preview LaTeX Output*` buffer for detailed errors.

In my case, it was that Emacs cannot find the `latex` and `dvipng` command in Emacs, even if I have use `exec-path-from-shell` to obtain `PATH` from the system.

So the solution is to add symlinks of those two to `/usr/local/bin`.
