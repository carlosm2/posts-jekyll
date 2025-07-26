---
layout: post
title:  "Export APK for migration (EN)"
date:   2023-12-11 12:31:00
categories: android apk linux adb
---

                                 
     .              .   /      .'. .' 
 -=  o  =-  .'   '              
     |                           
     |                      
     |=====.                
     |.---.|                
     ||=o=||                
     ||   ||                
     ||   ||               
     ||___||               
     |[:::]|               
     '-----'

## Export an APK for migration to another mobile

I needed to install a language application that was no longer available in the official store or on the manufacturer's website,
so I had to export it so I could continue using it on a new phone.

## Step 1 – Enable adb debugging on your device

In order to use **adb** with a device connected via USB, you must enable USB Debugging in the device's system settings,
found in "Developer Options". On Android 4.2 (API level 17) and later, the Developer Options screen
It is hidden by default. To make it visible, enable Developer Options.
[https://developer.android.com/studio/debug/dev-options?hl=es-419#enable](https://developer.android.com/studio/debug/dev-options?hl=es-419#enable)


## Install adb

Android Debug Bridge 
{% highlight python %}$ apt install adb{% endhighlight %}


## Connect your phone to the computer and validate it

It can be done in several ways but I usually do it with a direct USB connection,
enable **File Transfer** from the phone and then check with:

{% highlight python %}$ adb devices{% endhighlight %}

With the previous command you should see your phone listed:

{% highlight python %}
$ adb devices
$ daemon not running; starting now at tcp:5037
$ daemon started successfully
$ List of devices attached
$ f48ec6 device
{% endhighlight %}

## Find the installed application

To list the applications installed on the phone:
{% highlight python %}
$ adb shell pm list packages
{% endhighlight %}

if we want to search for example the application "uber"
{% highlight python %}
$ adb shell pm list packages | grep uber
{% endhighlight %}

## Find the application path

{% highlight python %}
$ adb shell pm list packages -f org.compania.aplicacion
{% endhighlight %}

## Extract the specific application

Once we have found the path to the application we want to back up or extract from the phone, we use this command:
{% highlight c++ %}
$ adb pull /data/app/~~randomdata==/com.compania.tracker-Nqrandom_nOhw==/base.apk
{% endhighlight %}
which will leave it with the name base.apk to be installed on another compatible Android phone, it doesn't always work, but that backup can be useful for the same phone in case we reinstall the entire operating system.
