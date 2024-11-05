---
layout: post
title:  "Instalar tiny-check en raspberrypi"
date:   2023-01-21 12:32:00
categories: softwarelibre autocuidadodigital raspberrypi spyware
---

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@@@@   @/@@@@@@    @@@@    @@#@@@ *   @@@@
@@@@ @@@@*@@@@@@@@@    @@@@@@@@@@@@@% @@@@
@@@@@ @@@@@@@@ @@@@@  @@@@@ @@@@@@@@ @@@@@
@@@@@@ @@@@@@@@@@        @@@@@@@@@@ @@@@@@
@@@@@@@@  @@@@@@          @@@@@@  @@@@@@@@
@@@@@@@@   @@@@  @@@@@@@@  @@@,   @@@@@@@@
@@@@@@  @@@@@   .@@@@@@@@@   @@@@@  @@@@@@
@@@@@@ /@@    %@@        @@@@   @@  @@@@@@
@@@@       @@@@@@@@@  .@@@@@@@@@      @@@@
@@@  @@@  @@@@@@@@@@  @@@@@@@@@@@ @@@, &@@
@@  @@@@  @@@@@@@@@    @@@@@@@@@* @@@@  @@
@@* @@@     @@@@@  /@@@   @@@@     @@@  @@
@@@@    @@      @@@@@@@@@@     @@@@   @@@@
@@@@@  @@@@@@   @@@@@@@@@@@  @@@@@@@ @@@@@
@@@@@. @@@@@@@&  @@@@@@@@@ .@@@@@@@  @@@@@
@@@@@@@  @@@@@@            @@@@@@  @@@@@@@
@@@@@@@@@@/     @@@@@@@@@@      @@@@@@@@@@
@@@@@@@@@@@@@@@  @@@@@@@@  @@@@@@@@@@@@@@@
@@@@@@@@@@@@@@@@@@@%  (@@@@@@@@@@@@@@@@@@@

## Tinycheck

(Desactualizado)

Traducción de la descripción:

TinyCheck le permite capturar fácilmente las comunicaciones de la red desde un teléfono inteligente o cualquier dispositivo que pueda asociarse a un punto de acceso Wi-Fi para analizarlas rápidamente. Esto se puede usar para verificar si alguna comunicación sospechosa o maliciosa está saliendo desde un teléfono inteligente, mediante el uso de heurísticas o indicadores de compromiso (IoC) específicos.

[https://github.com/KasperskyLab/TinyCheck](https://github.com/KasperskyLab/TinyCheck)

El proyecto tiny-check no ha sido actualizado pero los paquetes que descarga para operar estan mas o menos actualizados y los IOCS tambien se pueden actualizar lo cual lo convierte en una herramienta util, sobretodo amigable para el analisis de stalkerware y spyware.

# Instalación

Parto de un Raspberry Pi OS 11 Full ARM 32 bits que esta basado en **Debian 11 Bullseye**, me voy a la instalacion completa y no una ligera porque mucho software sera usado para generar nuestro tinicheck. Aun no hago pruebas de quitar cierto software ofimatico que haga un poco mas ligero este tinicheck pues para esta instalación estoy usando el siguiente dispositivo:

{% highlight c++ %}
    description: Computer
    product: Raspberry Pi 3 Model B Plus Rev 1.3
    width: 64 bits
     *-cpu:0
          description: CPU
          product: cpu
          physical id: 0
          capacity: 1400MHz
          
      Ethernet interface
                vendor: Microchip Technology, Inc. (formerly SMSC)
                physical id: 1
                bus info: usb@1:1.1.1
                logical name: eth0
                version: 3.00
                size: 1Gbit/s
                capacity: 1Gbit/s
                
      *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmfmac driverversion=7.45.241 firmware=01-703fd60 multicast=yes wireless=IEEE 802.11
          
 {% endhighlight %}

Como pueden ver del resultado del comando **lshw** es una Rasperry Pi 3b+ que tiene integrada una antena wifi lo cual es un requisito, que tenga dos interfases de red, una cableada de donde obtendra la conexion a internet y otra que funcionará como punto de acceso temporal para capturar los datos transmitidos.

Esta es la documentación para instalarlo:

[https://github.com/KasperskyLab/TinyCheck/wiki/TinyCheck-installation](https://github.com/KasperskyLab/TinyCheck/wiki/TinyCheck-installation)

Uno de los pasos que me sirvió antes de ejecutar el script de instalación fue instalar zeek con los siguiente paso documentados de esta página:

[https://software.opensuse.org//download.html?project=security%3Azeek&package=zeek](https://software.opensuse.org//download.html?project=security%3Azeek&package=zeek)

{% highlight c++ %}
echo 'deb http://download.opensuse.org/repositories/security:/zeek/Raspbian_11/ /' | sudo tee /etc/apt/sources.list.d/security:zeek.list
curl -fsSL https://download.opensuse.org/repositories/security:zeek/Raspbian_11/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/security_zeek.gpg > /dev/null
sudo apt update
sudo apt install zeek

 {% endhighlight %}

Después se ejecuta el script de instalación y se queda atorado cuando esta descargando los IOCS como esta documentado en este issue de github:

[https://github.com/KasperskyLab/TinyCheck/issues/97](https://github.com/KasperskyLab/TinyCheck/issues/97)

Pero en una conexión de internet estable despues de un par de horas como maximo ya estaran descargados, en otra publicación mostraré como verificar esto.

Mientras si habilitaron que se ejecute el modo kiosko al inicio entonces en el siguiente reinicio ya deberian de tener un tiny-check funcional :)

Video explicativo de tiny-check:

[https://www.youtube.com/watch?v=hJarUzjSrm0](https://www.youtube.com/watch?v=hJarUzjSrm0)

versión invidious:

[https://invidious.snopyta.org/watch?v=hJarUzjSrm0](https://invidious.snopyta.org/watch?v=hJarUzjSrm0)




