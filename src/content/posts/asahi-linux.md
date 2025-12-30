---
title: Asahi Linux on MacBook experience
published: 2025-12-29
description: 'First time trying Linux on ARM'
image: ''
tags: [Experience]
category: Experience
draft: false
lang: ''
---

# How it all started

A friend told me you can now install [Asahi Linux](https://asahilinux.org/) on M1/M2 MacBooks, which caught my attention. Since MacBooks have a lot of security features and Boot Camp is not available on M-series chips, dual-booting is even harder on a MacBook.

Another concern was graphics drivers. Because MacBooks no longer use Radeon graphics or Intel UHD, the video driver has to be written from scratch.

It turns out Asahi Linux uses a modified Mesa driver, and the efficiency is not too bad.

# Installation

The overall installation is not too complicated. The catch is you cannot change the disk size after partitioning, so you either have to nuke the entire system and repartition or add another partition for Linux, which was a nightmare for me.

The installer is CLI-based. In a short time the procedure is clear and you can boot into Linux.

There are several options: Asahi Linux Fedora Remix with KDE, GNOME, or minimal. As someone who likes a little challenge, I went with minimal.

Right away I was met with a CLI setup that uses arrow keys to create a user and set the region. After some time, I was greeted by a minimal Linux: no WM, no desktop, no GUI.

Here I was pointed to a "desktop" called [Hyprland](https://hypr.land/). It's more for *nerds*, since it doesn't come with a top bar showing system information or clear instructions for keybinds. You have to read the [docs](https://wiki.hypr.land/Configuring/Binds/), so it took me a while to get around it.

:::tip
Because Linux packages often require near-latest software, programs like Quickshell can run into problems with Hyprland not being able to read desktop information. It's preferable to install the latest Hyprland before use; otherwise you'll juggle mismatched package versions if you update later.
:::

To install the latest Hyprland on Fedora, first enable the community-maintained Hyprland repo designed to run on Fedora.

```zsh
sudo dnf copr enable solopasha/hyprland
```

Then install Hyprland:

```zsh
sudo dnf install Hyprland
```

I have made my own dotfiles available on [GitHub](https://github.com/xNeonCatGirlx/Dotfiles).

Google Chrome is not available on ARM, and many Linux users prefer Firefox, so I tried Firefox. In my opinion, Firefox has less compatibility with some websites. For example, I had issues scrolling on [Cambridge GO](https://www.cambridge.org/go/resources) where the page would randomly jump ahead.

The animations out of the box are very smooth, and the fact this WM only uses around 300MB-700MB of RAM is incredible.

# Daily drive?

## Pros

I use both Windows and macOS, and since macOS is based on UNIX, Linux overall felt more like macOS than Windows. Linux has a large open-source community that creates great alternative software available on both macOS and Windows. Some software, such as Hyprland, only runs on Linux, which draws people who love to customize their workspace.

Most Linux distros don't come with bloat. I've had experience removing bloat from Windows 10 (already cleaner than Windows 11), and it still took a painful amount of time to optimize. My Linux setup is clean and light; after installing all the apps, the disk used less than 4GB of space.

On Linux you install only what you need, and software compatibility in 2025 is not too shabby. With Wine and Proton support, you can run many Windows apps and games out of the box.

Linux is very open and gives you permission and access to anything you want as sudo.

## Cons

The learning curve includes new commands and compiling your own software, since support on ARM Linux isn't as good as x86_64. For closed-source apps, running them natively on ARM is nearly impossible. For Windows-only x86_64 apps, you need double translation: Windows to Linux, then x86 Linux to ARM Linux. The performance loss is huge and heavily affects MacBook battery life.

Adobe apps don't work on Linux, along with many others. There are usually alternatives, but they cost time to learn.

Because Linux is so open, you can easily break your system as a newcomer—accidentally deleting configs you spent a long time making or nuking the bootloader.

Linux itself and many apps have long docs you have to read, and sometimes they are outdated or hard to navigate. In my experience, the Linux community isn't very friendly when it comes to helping. Many people just want you to read the docs, and when docs are unclear, it can be frustrating as a new user.

# Conclusion

I would suggest anyone interested in computing give Linux a try. It can help you level up with the command line and programming, and it gives you the freedom to control your system.

You will need to leave your comfort zone when switching and push yourself to try something new.

But be prepared to face problems with app support and when seeking help.