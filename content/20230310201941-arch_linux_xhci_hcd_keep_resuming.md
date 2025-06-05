+++
title = "Arch Linux xhci_hcd keep resuming"
author = ["Fangyuan Wang"]
tags = ["linux"]
draft = false
+++

The arch linux keep saying `xhci_hcd xHC error in resume` when I suspend the system. After chat with openai chatgpt and google, temporaly solve this problem by **disable** and **enable** the `xhci_hcd` module before and after suspending.
