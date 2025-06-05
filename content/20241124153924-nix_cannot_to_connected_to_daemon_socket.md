+++
title = "Nix cannot to connected to daemon socket"
author = ["Fangyuan Wang"]
tags = ["nix"]
draft = false
+++

TLDR;

```shell
sudo chown -R user_name /nix
```


## Updated @2024-12-08 {#updated-2024-12-08}

!SHIT! The above answer is wrong!

It's better not to change the permision of Nix Store by ourself.

First, try to check if the nix-daemon is stared:

```shell
sudo launchctl list | grep org.nixos
```

If not, start it:

```shell
sudo launchctl kickstart -k system/org.nixos.nix-daemon
```

Then try to use \`nix run\` to rebuild the system (if you don't have \`/run/current-system/\` in your system.

```shell
nix run nix-darwin --extra-experimental-features "nix-command flakes" -- switch --flake /path/to/your/flake.nix
```


### Important Notes {#important-notes}

> When anything wired happend, remember to check if new nix command has permitted with Full Disk access.
