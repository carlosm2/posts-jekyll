---
layout: post
title:  "Asegurar acceso SSH a raspberrypi"
date:   2022-01-01 12:32:00
categories: raspberrypi ssh
---

# Asegurar conexión SSH de una raspberrry pi

(aunque aplica para cualquier servidora)

   
   ┈┈┈╱▏┈┈┈┈┈╱▔▔▔▔╲┈┈┈┈
┈┈┈▏▏┈┈┈┈┈▏╲▕▋▕▋▏┈┈┈
┈┈┈╲╲┈┈┈┈┈▏┈▏┈▔▔▔▆┈┈
┈┈┈┈╲▔▔▔▔▔╲╱┈╰┳┳┳╯┈┈
┈╱╲╱╲▏┈┈┈┈┈┈▕▔╰━╯┈┈┈
┈▔╲╲╱╱▔╱▔▔╲╲╲╲┈┈┈┈┈┈
┈┈┈╲╱╲╱┈┈┈┈╲╲▂╲▂┈┈┈┈
┈┈┈┈┈┈┈┈┈┈┈┈╲╱╲╱┈┈┈┈
   

Una vez conectada la raspberry pi a nuestra red podemos buscarla con el comando **netdiscover**:

[https://www.kali.org/tools/netdiscover/](https://www.kali.org/tools/netdiscover/)

{% highlight c++ %}
sudo netdiscover
{% endhighlight %}
lo que mostrara en nuestro segmento de red la IP de nuestro dispositivo:

{% highlight c++ %}

   IP             Count    MAC Vendor / Hostname
                                                                                
 192.168.0.2       1      Raspberry Pi Foundation   
{% endhighlight %} 
 entonces procedemos con el siguiente comando para conectarnos:
{% highlight c++ %} 
ssh cacu@192.168.0.2 -o PasswordAuthentication=yes
{% endhighlight %}
  
aparecerá este mensaje de advertencia:
{% highlight c++ %}
The authenticity of host '192.168.0.2 (192.168.0.2)' can't be established.
ECDSA key fingerprint is SHA256:xxxxxx.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
{% endhighlight %}
ponemos nuestra contraseña del usuario y ya estamos dentro.

pero es mas bacán accesar via llave ssh por eso vamos a agregar nuestra llave publica a la raspberrypi:
{% highlight c++ %}
ssh-copy-id -i id_rsa.pub cacu@192.168.0.2
{% endhighlight %}
lo que arroja los siguientes datos:
{% highlight c++ %}
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
cacu@192.168.0.2's password: 
{% endhighlight %}
donde ponemos nuestra contraseña para confirmar la adición de la llave.

y ahora a probar la nueva conexión via:
{% highlight c++ %}
ssh cacu@192.168.0.2
{% endhighlight %}

## Modificar el archivo /etc/ssh/sshd_config

Para asegurar nuestra conexión ssh para para que no entren con root, sean solo 3 intentos en la contraseña, que solo acceda nuestro usuario (y a blue demon por si me pasa algo) y otro puerto que no sea el por defecto:
{% highlight c++ %}
sudo vim /etc/ssh/sshd_config
{% endhighlight %}

donde modificaremos estos datos:

{% highlight c++ %}
Port 22445
PermitRootLogin no
LoginGraceTime 30
MaxAuthTries 3
MaxStartups 3
AllowUsers cacu bluedemon
{% endhighlight %}

finalmente probamos el acceso con puerto cambiado:
{% highlight c++ %}
ssh cacu@192.168.0.2 -p 22445
{% endhighlight %}

