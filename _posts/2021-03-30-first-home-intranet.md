---
layout: single
title:  "Creating Home Intranet"
date:   2021-03-30 01:30:00 -0500
categories: web
tags: intranet introduction
header:
    teaser: /assets/images/lightbulb.jpg
---

# My First Real Project - Home Intranet #

## The Start ##

The first real project I am posting here is fun, but very simple. I am creating a home intranet, using a Raspberry Pi as the server. Not only is this a simple project, but I will be following tutorials found online from start to finish. I'll be using items I already had hiding in a desk drawer, waiting to be applied to a project like this. Now before I begin, it is a good idea to start with my materials...

My webserver will be this Raspberry Pi 3B+ :

![Picture of Raspberry Pi 3B+](/assets/images/bare_raspi.jpg)
*My Pi*

I received that little guy as a gift, in a kit along with a power supply and a plastic case. While I do not have a fan, in the picture above you can see my poorly applied heat sinks. I do have a Raspberry Pi 4B tucked away in the same drawer where I found this one, that is currently fitted with a dual fan case. If overheating is a problem when this project is complete, I will update this post and move to the other Pi/case.


![Picture of Raspberry Pi 3B+ kit](/assets/images/supplies.jpg)
*I know what you're thinking, but no, I'm not sponsored*


Before I forget, I also have a 32GB microSD card for the operating system. I believe it cost me about $10 at Micro Center(Probably my second favorite place to shop, behind the Costco food court). Probably most important of all, the tutorial I am using for this first iteration of the project is from [Tom's Hardware](https://www.tomshardware.com/news/raspberry-pi-web-server,40174.html).

## Let's get started! ##

Kicking off the tutorial mentioned above, I followed a link to another fantastic Tom's Hardware [article](https://www.tomshardware.com/reviews/raspberry-pi-headless-setup-how-to,6028.html) that walks us through the process of a headless installation and setup of the Raspberry Pi. A headless install is when the Raspberry Pi is setup so that it can be managed remotely from a separate computer. This way I don't need to use a separate keyboard and monitor for this project. Once I read through the article, I got my microSD card ready and installed [Raspberry Pi Imager](https://www.raspberrypi.org/software/). Following the article, I installed Raspbian, the Raspberry Pi OS, to my microSD card. I then enabled [ssh](https://en.wikipedia.org/wiki/Secure_Shell_Protocol), according to instructions. A more beginner friendly explanation of ssh can be found [here](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work).

Next up was to connect the Raspberry Pi to the network. I chose to connect the Pi to my network via ethernet. I made that choice because the idea of storing my wifi SSID and password in a plaintext file did not seem like the greatest idea. But what do I know... Anyway, this step was easy. I connected the Pi to my router with an ethernet cable, inserted the microSD card, then connected it to power for the first time.

![Working lights](/assets/images/lights.jpg)

...some blinking lights. Looks good, I think.

Because I'm working from my Windows laptop, I used PuTTY to connect via SSH. Typically, I would use either my main Linux machine, or use WSL. But why not try it a little different today? The default host name is **raspberrypi**. Default credentials are 
- *username:* **pi** 
- *password:* **raspberry**

We will go ahead and change that password now. From the command line, use the `passwd` command. Then enter the current default password, at which point it will prompt to enter the new password. I save my login credentials in a password manager, allowing me to keep long, random passwords. (Helpful tip: right-clicking the mouse pastes from the clipboard into PuTTY). 

At this point, the tutorial dives into setting up a VNC server on the Pi in order to remotely use the GUI. I have no need for this, so I'm going to skip these steps. And we are done configuring the Raspberry Pi for headless access!

## Next Up ##

Back to the [initial tutorial](https://www.tomshardware.com/news/raspberry-pi-web-server,40174.html). I'll give a summary of the commands used, without further explanation.

    sudo apt-get update
    sudo apt-get install apache2 -y
    sudo apt-get install php libapache2-mod-php -y
    sudo apt-get install mariadb-server
    sudo mysql_secure_installation
    sudo apt install php-mysql
    sudo service apache2 restart

To break it down, most of these will not be necessary for the basic HTML page I am using this project for. BUT, they will allow for hosting more interesting projects in the future. Now after running these commands, I tested the server by visiting http:/raspberrypi on my laptop. 

![Test page](/assets/images/test_page.png)
*It worked!*

As noted in the tutorial, */var/www/html* is the directory where your site files will be stored.

I changed my server's host name to something more original. Personal choice, but I like the special touch.
`sudo raspi-config` is the command to save you here. My experience did not match the tutorial exactly, but i found host name settings under system settings.

<hr>

The last major step here is to set up FTP on the server. This will allow me to remotely copy files onto the server from my laptop, a lot easier than doing all the work on the Pi. After writing up the most basic of html and moving it to the server via SFTP through Filezilla, I ran one more test.

![Test page](/assets/images/first_page.png)
*By some miracle, this also worked on the first try*





Further projects: File server...host apps. Should I write about ssh and ftp and all that?