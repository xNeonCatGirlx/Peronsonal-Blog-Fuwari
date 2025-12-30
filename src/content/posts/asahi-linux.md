---
title: Asahi Linux on Macbook experience
published: 2025-12-29
description: 'First time trying Linux on arm'
image: ''
tags: [Experience]
category: Experience
draft: true
lang: ''
---

# How it all started

I was told by a friend that you are now able to install [Asahi Linux](https://asahilinux.org/) on M1/M2 Macbooks, which gathered my attention. Since Macbook have a lot of scurity features and now boot camp is now not avaliable on M-Series chip, making it even harder to dual boot on a Macbook.

Another issue that came into mind is the graphics driver. Because Macbooks are no longer using Readon Graphics or Intel UHD, which means the video driver need to be completely written from stratch. 

It turns out, Asahi Linux uses a modifies Mesa driver, and the efficiency is not too bad.

# Installation

The overall installation is not too complecated. The problem being you are not able to change the size of the disk after parition, requiring you too nuke entire system and repartition, or add another partition to Linux. Which turns out to be a nightmare for me.

The installation is a CLI. Without much time, procedure is clear, you can boot into Linux. 

There are several versions of Linux which you can choose, Asahi Linux Fedora remix with KDE, Gnome, or minimal. As someone who likes a little challenge, I decided to go with minimal. 

Right off the bat, I was met with a CLI installation program, which requires you to navigate using the arrow keys to create user and setup region. After some time, I was successful to be greet with a minimal version of Linux. With no WM, no "desktop" and no Graphic Interface. 

Here, I was recommended a "desktop" called [Hyprland](https://hypr.land/). It's more of a desktop for *nerds*, as it doesn't come with a top bar to show system information, nor any clear instruction to show you the keybinds. You will have to read all of that in the [docs](https://wiki.hypr.land/Configuring/Binds/). So it took me a while to get around it.

The animation out of the box is frickin smooth, the fact this WM only eats up around 300MB-700MB of RAM is absolutely incredible.

:::tip
Because Linux packages often require you with the near latest version of software, program like Quickshell I ran into problem with Hyprland not being able to get the desktop information. So it is prefered to install the latest version of Hyprland before use. You will have to deal with a lot of different version of packages of Hyprland if you decided to update later on
:::