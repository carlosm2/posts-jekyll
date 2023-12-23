---
layout: post
title:  "Exportar APK de un telefono a otro"
date:   2023-12-12 12:32:00
categories: androdi apk linux
---

## Exportar un APK para migrarlo a otro telefono

Tenia la necesidad de instalar una aplicación de idiomas que ya no estaba disponible en la tienda oficial ni en la pagina del fabricante, 
asi que tuve que exportarlo para poder seguir utilizandolo en un nuevo teléfono.

## Paso 1 - Habilita la depuración de adb en tu dispositivo

A fin de usar **adb** con un dispositivo conectado a través de USB, debes habilitar Depuración por USB en la configuración del sistema del dispositivo, 
que se encuentra en Opciones para desarrolladores. En Android 4.2 (nivel de API 17) y versiones posteriores, la pantalla Opciones para desarrolladores 
está oculta de forma predeterminada. Para que sea visible, habilita las Opciones para desarrolladores.
[https://developer.android.com/studio/debug/dev-options?hl=es-419#enable](https://developer.android.com/studio/debug/dev-options?hl=es-419#enable)


## Instalar adb

Android Debug Bridge 
{% highlight java %}apt install adb{% endhighlight %}

