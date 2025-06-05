+++
title = "Debuger stucked in VSCode"
author = ["Fangyuan Wang"]
tags = ["vscode"]
draft = false
+++

The default `console` in `launch.json` is `integratedTerminal` which is works fine in most cases.

But it might stuck when your program encounter some warnings.

All things are fixed after I change `console` to `integratedConsole`. But still don't know the different between these two parameters.
