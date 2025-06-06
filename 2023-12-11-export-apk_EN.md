---
layout: post
title:  "Export APK for migration"
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

## Export an APK for migration

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

si queremos buscar por ejemplo la aplicación "ubre"
{% highlight python %}
$ adb shell pm list packages | grep ubre
{% endhighlight %}

## Encontrar la ruta de la aplicación

{% highlight python %}
$ adb shell pm list packages -f org.compania.aplicacion
{% endhighlight %}

## Extraer la aplicación especifica

una vez encontrada la ruta de la aplicación que queremos respaldar o extraer del teléfono usamos este comando:
{% highlight c++ %}
$ adb pull /data/app/~~randomdata==/com.compania.tracker-Nqrandom_nOhw==/base.apk
{% endhighlight %}
con lo cual quedará con el nombre base.apk para ser instalado en otro teléfono android compatible, no siempre funciona, pero ese respaldo nos puede servir para el mismo teléfono por si reinstalamos todo el sistema operativo.
