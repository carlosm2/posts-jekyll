---
layout: post
title:  "Install PiRogue on a pine rock64 (EN)"
date:   2025-07-22 12:32:00
categories: pirogue forensic rock64 debian
---
# Install PiRogue on a Pine Rock64

he project PiRogue Tool Suite [https://pts-project.org/](https://pts-project.org/) - Open-Source Platform for Mobile Device Forensics and Digital Investigations provides us with some tools/software for forensic analysis. In my case, I needed something like this for a few years, so I decided to install a Pi-Rogue.

The official documentation mentions Raspberry Pis as a supported option for installation. However, I only have a few Raspberry Pi 3B+ boards, which come with just 1 GB of RAM—insufficient to run Suricata effectively. For that reason, I decided to install it on a Single Board Computer (SBC), the PINE Rock64 (https://pine64.org/devices/rock64/). Before installing Suricata, I first needed to set up Debian 12, which is my favorite operating system.

From this web address you can download the different versions of Armbian that can be installed on that PINE Rock64:
[https://armbian.tnahosting.net/archive/rock64/archive/](https://armbian.tnahosting.net/archive/rock64/archive/) In my case I choose to install the version based on Debian Bookworm (12) because in the PTS Project Documentation it is documented that it can be installed on Debian 12 systems:
[https://pts-project.org/docs/recipes/turn-a-regular-pc-into-a-pirogue/](https://pts-project.org/docs/recipes/turn-a-regular-pc-into-a-pirogue/)

Once Armbian 12 is installed it will look like this:

{% highlight python %}
    _             _    _           
   /_\  _ _ _ __ | |__(_)__ _ _ _  
  / _ \| '_| '  \| '_ \ / _` | ' \ 
 /_/ \_\_| |_|_|_|_.__/_\__,_|_||_|
                                   
 v25.5.1 for Rock 64 running Armbian Linux 6.12.38-current-rockchip64

 Packages:     Debian stable (bookworm)
 IPv4:         (LAN) 192.168.1.x, 10.8.0.1 (WAN) 189.x.x.x
 IPv6:         (WAN) xxx.xxxx.xxxxx.xxxxxx
 
{% endhighlight %}

However, this SBC does not have a built-in WiFi card, which is required to operate in AP mode with PiRogue. Therefore, I used an external USB WiFi adapter:

{% highlight python %}
cacu@rock64:/home/cacu# lsusb
Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
{% endhighlight %}

I had already successfully tested this external USB antenna on other Linux distributions, without the need for any additional or special drivers. This makes it possible to install Pi-Rogue in Access Point mode, which best fits my needs: analyzing potential malware threats and malicious connections on a device.

To install PiRogue on a Debian-based system, it is recommended to start by updating the operating system.

{% highlight python %}
sudo apt update
sudo apt upgrade
{% endhighlight %}

The following repositories are then added:

{% highlight python %}
sudo wget -O /etc/apt/sources.list.d/pirogue.list https://pts-project.org/debian-12/pirogue.list
sudo wget -O /etc/apt/trusted.gpg.d/pirogue.gpg   https://pts-project.org/debian-12/pirogue.gpg
sudo apt update
sudo apt install pirogue-base
{% endhighlight %}

Once installed, we can check if it was installed correctly, the type of configuration, and the passwords to access the dashboard:

{% highlight python %}
pirogue-admin --configuration-tree
pirogue-admin --current-config
{% endhighlight %}

To check the existing connections, execute this command:

{% highlight python %}
root@rock64:/home/cacu# nmcli connection show

NAME                      UUID                    TYPE      DEVICE          
Wired connection 1        0d5e9649-81ce-masdatos  ethernet  end0            
lo                        36a9c025-f184-masdatos  loopback  lo              
pirogue-isolated-network  c171297d-8af1-masdatos  wifi      wlxa0f3c109b6cf 

{% endhighlight %}
