+++
title = "Fix nix symlink in MacOS after system upgrade"
author = ["Fangyuan Wang"]
tags = ["mac", "nix"]
draft = false
+++

The MacOS system upgrades basiclly will uninstall Nix every time and reinstall it again. It will remove the symlink `/run/current-system` which is the basic environment you are using.

So we need to restore the symlink and activate the nix environment.

1.  Find what's the `/run/current-system` points to. Actually you may don't have time to know this before your first run into this trouble, so my method is:
    -   It usually points to one folder listed in `/nix/store/`, and with the string `darwin-system`  in the folder name.
    -   We can just use the most recent one as current system. In my case, I only have 1 recent system and others are all at 1970. It is easy to identify.

2.  Link `/run/current-system` to the folder you found.

3.  Then `cd` into the folder, and run `./activate` to activate the system.
