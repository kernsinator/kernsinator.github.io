---
layout: single
title:  "Installing Arch Linux"
date:   2021-04-25 01:30:00 -0500
categories: linux
tags: linux OS
header:
    teaser: /assets/images/archlogo.png
---

A few days ago I decided to forego sleep in favor of installing Arch Linux on an old Thinkpad X240. It was sucessful, though not without a fair share of challenges. Prior to this, my experience with Linux was limited at best. I run Debian on my main workstation at home, with Windows 10 on my main laptop. I am by no means a power user with either operating system but this was a lot of fun. This project was successful and I am currently using this Arch system to write this article.

Arch takes some knowledge to install. In my case, that knowledge was found in the Arch Linux [installation guide](https://wiki.archlinux.org/index.php/installation_guide). Here is a summary pulled from the table of contents of the guide, as the steps are covered in detail there:

### Pre-installation ###
- Acquire an installation image
- Verify signature
- Prepare an installation medium
- Boot the live environment
- Set the keyboard layout
- Verify the boot mode
- Connect to the internet
- Update the system clock
- Partition the disks
- Format the partitions
- Mount the file systems

### Installation ###
- Select the mirrors
- Install essential packages

### Configure the system ###
- Fstab
- Chroot
- Time Zone
- Localization
- Network configuration
- Initramfs
- Root password
- Boot loader

### Reboot ###

### Post-installation ###
- Preparing system as desired

The entire process involved a LOT of googling to be successful. The installation guide itself easily walked me through the process of downloading and verifying the installation image. I used [balenaEtcher](https://www.balena.io/etcher/) to prepare a USB drive with that image. The first tricky step was to allow my computer to boot from the USB drive instead of the installed OS. After a quick Google search, I found the keys to press while the computer was starting in order to access the BIOS menu. This then allowed me to change the boot order to attempt to boot from the USB drive before the hard drive.

From there, the next several steps easily went as described in the installation guide. I chose a simple partition scheme, with a root partition and a swap partition. I know my needs will likely change in the future, but currently I do not know why I would need to structure things differently.

Once Arch was installed locally, the real fun began. It seemed that everything I was used to doing required more installations. For example, I was used to using `sudo` and even had a basic understanding of the reason why. Using sudo instead of the root user has a major security benefit. But until now, I did not anticipate having to install and configure `sudo`. That process in itself was unsuccessful multiple times. Eventually, I had a user added that had sudo access on the system. Ready for more!

I installed several utilities that I thought would be useful, and settled on XFCE as my desktop environment, which installed several more. Still I encountered some trouble.

I found that many of my problems were related to networking. My initial setup was performed at home and went smoothly enough. The problem I had was when I took my computer to work. I decided that it was more comfortable to take this older, much cheaper, computer to work in case my backpack was lost or stolen at any point. Working on an ambulance means connecting to many different wireless networks throughout the course of the shift. My first stop was a fire station, where I connected to the guest network. I was able to connect without trouble at first. As this site is hosted on Github Pages, I then installed git before attempting to clone the repo for this site.

Every time I attempted the ssh connection to Github, I received a 'connection refused' error. Many Google searches later, I still had not found the answer. Solutions offered online were either unsuccessful or clearly risky to use on my machine. After a while I decided the problem might be the guest network I was using and realized that Github was blocked altogether. Easy enough, I just fired up my personal hotspot from my phone. At that point, I could not even see my hotspot in the list of available networks. More Googling and I came up with nothing. As a last ditch effort, I started looking through my phone settings and saw that not only was my hotspot set to use 5Ghz, but also that the warning message says that might not work with all hardware. Switching to 2.4Ghz, I tried again. Still nothing.

At this point I was getting frustrated. Was every single task going to be this difficult? More Googling to find NetworkManager commands.

`nmcli device wifi list`
Nope.

Tried it again...nothing. A few more times still with no success. I sat there staring at the table for a minute or two before deciding to run that command one more time and then moving on to something else. Apparently enough time had passed and all of a sudden my hotspot was visible in the network list! Connected to the hotspot, I was able to SSH to Github with no problem. I downloaded VSCode and opened up my site filed to get to work.

Once I settled in to start writing, I was feeling pretty good about what I accomplished so far. i decided to open Youtube to play some music while I worked. Well I quickly realized there was no audio. Volume on the video was set to maximum. Oddly enough, I could not find any system audio settings. I eventually discovered that I had to install a package to handle audio output. PulseAudio was the winer here. After installing those controls and a graphical interface for them, I selected my output as the computer speakers and all of a sudden I had sound.

At this point I've got my desktop environment, many of the applications I use on a daily basis, and even have music running. But still being at work, I realize I need headphones or people are going to get annoyed pretty quickly with my 'interesting' musical selections. I brig a pair of true wireless headphones to work every day. I broke those out and realized I would need to figure out how to use them with this computer. At least this time it did not come as a surprise. More Googling led me to install the appropriate bluetooth tools. I then learned to scan for devices from the command line and add them by MAC address. All in all, not that difficult. It did not work at first, but a little tinkering with settings and the connection was successful.

With all of these things accomplished, I now have a functional machine. In the following days, I have been adding more and more useful items, as well as using this computer for other tasks, like setting up a Linode VPS, which I will talk about soon. 

Yesterday I was staying in a hotel and configured Wireguard, which was several steps more complicated that my previous interaction with VPNs through desktop apps. I ran into several DNS issues that I fixed with the help of what seemed like everyone on the internet, as well as many added and deleted connection profiles. After that I still had a problem with a DNS leak that took a few changes in browser settings to fix.

In the end, this was an awesome project that resulted in a repurposed old computer that I can continue to use for all sorts of projects. This machine continues to be a platform for me to learn more about Linux while working from a machine that I don't have to protect like it is my firstborn child. In the future, most of these articles witll be written from the system, as well as most of the management of my other upcoming projects. I appreciate any questions or suggestions in the comment box below, or feel free to shoot me an email instead!