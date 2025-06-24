---
layout: post
title:  "Enable screenshot for KeepassXC on macOS"
date:   2023-03-22 12:32:00
categories: privacy keeepassxc osx macos
---

    .__________________________.
    | .___________________. |==|
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | |  |
    | |                   | | ,|
    | !___________________! |(c|
    !______________________ |__!
    |    ___ -=      ___ -= | ,|
    | ---[_]---   ---[_]--- |(c|
    ---------------------------- 

# Enable screenshots for KeepassXC on OSX

## Screenshots

To make tutorials, documentation, which is one of the things I often do I need to take screenshots, on my base system (Debian Bullseye) I use the software built into gnome screenshot: [https://gitlab.gnome.org/GNOME/gnome-screenshot](https://gitlab.gnome.org/GNOME/gnome-screenshot) and for mp4 and gif animations I use Peek: [https://github.com/phw/peek](https://github.com/phw/peek).

In the case of macOS it is used:

{% highlight java %}Shift +  Command + 5{% endhighlight %}

## Screenshot Lock

There’s a privacy lock I’ve noticed when taking screenshots on Android and macOS in security-focused, privacy-focused apps like KeepassXC: [https://keepassxc.org/](https://keepassxc.org/) and FreeOTP [https://freeotp.github.io/](https://freeotp.github.io/) that you are not allowed to save the screenshot with the data, also happens when a remote viewing software is being used [https://es.wikipedia.org/wiki/VNC](https://es.wikipedia.org/wiki/VNC). 

## Enable this on macOS

This is the instruction to enable an app:

{% highlight java %}$ open -n ./AppName.app --args -AppCommandLineArg{% endhighlight %}

then apply for KeepassXC, open the terminal:

change to the directory where the application is located, in this case:

{% highlight java %}$ cd /Applications{% endhighlight %}

Y luego ejecutar:

{% highlight java %}$ open -n ./KeePassXC.app --args allow-screencapture{% endhighlight %}

esto abrira keepassXC con la posibilidad de hacer capturas de pantalla.



