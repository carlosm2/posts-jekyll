---
layout: post
title:  "Exportar APK de un teléfono a otro"
date:   2023-12-12 12:32:00
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

## Exportar un APK para migrarlo a otro teléfono

Tenia la necesidad de instalar una aplicación de idiomas que ya no estaba disponible en la tienda oficial (Play Store) ni en la pagina del fabricante, asi que tuve que exportarlo para poder seguir utilizandolo en un nuevo teléfono.

## Paso 1 - Habilita la depuración de adb en tu dispositivo

A fin de usar **adb** con un dispositivo conectado a través de USB, debes habilitar Depuración por USB en la configuración del sistema del dispositivo, 
que se encuentra en "Opciones para desarrolladoras". En Android 4.2 (nivel de API 17) y versiones posteriores, la pantalla Opciones para desarrolladoras 
está oculta de forma predeterminada. Para que sea visible, habilita las Opciones para desarrolladoras.
[https://developer.android.com/studio/debug/dev-options?hl=es-419#enable](https://developer.android.com/studio/debug/dev-options?hl=es-419#enable)


## Instalar adb

Android Debug Bridge 
{% highlight python %}$ apt install adb{% endhighlight %}


## Conecta tu teléfono a la compu y validalo

Se puede de varias formas pero regularmente yo lo hago en conexión directa USB,
habilitar **Transferencia de archivos** desde el teléfono y luego verificar con:

{% highlight python %}$ adb devices{% endhighlight %}

con el comando anterior deberias ver listado tu telefóno:

{% highlight python %}
$ adb devices
$ daemon not running; starting now at tcp:5037
$ daemon started successfully
$ List of devices attached
$ f48ec6 device
{% endhighlight %}

## Buscar la aplicación instalada

para listar las aplicaciones instaladas en el teléfono:
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

Una vez encontrada la ruta de la aplicación que queremos respaldar o extraer del teléfono usamos este comando:
{% highlight c++ %}
$ adb pull /data/app/~~randomdata==/com.compania.tracker-Nqrandom_nOhw==/base.apk
{% endhighlight %}
con lo cual quedará con el nombre base.apk para ser instalado en otro teléfono android compatible, no siempre funciona, pero ese respaldo nos puede servir para el mismo teléfono por si reinstalamos todo el sistema operativo.
