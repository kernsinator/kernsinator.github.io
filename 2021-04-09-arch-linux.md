---
layout: single
title:  "Installing Arch Linux"
date:   2020-07-20 01:30:00 -0500
categories: programming
tags: C programming introduction
header:
    teaser: /assets/images/c-logo.png
---

A few days ago I decided to forego sleeping in favor of installing Arch Linux on an old Thinkpad X240. Mission Accomplished. Not without Hiccups.

No audio - fixed.

SSH to github, connection refused. TOok lots of googling then found that it was the network at the fire station. Tried using hotspot...no success. Spent a little bit confused. Looked through hotspot settings. Found that 5Ghz is default. Maybe old computer cant connect (like warning says). switch to 2.4Ghz. Still nothing. Google network manager commands. Try nmcli device wifi list. Nada. Few more times. Nada. By luck, tried one more time. Holy fuckshits it worked. Once connected, ssh to github no problem. Downloaded vscode and boom goes the dynamite.