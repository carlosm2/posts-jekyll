---
layout: post
title:  "extender caducidad de llave GPG vencida"
date:   2022-03-17 12:32:00
categories: gnupg openpgp cifrado
---

 ad8888888888ba
dP'         `"8b,
8  ,aaa,       "Y888a     ,aaaa,     ,aaa,  ,aa,
8  8' `8           "8baaaad""""baaaad""""baad""8b
8  8   8              """"      """"      ""    8b
8  8, ,8         ,aaaaaaaaaaaaaaaaaaaaaaaaddddd88P
8  `"""'       ,d8""
Yb,         ,ad8"    
 "Y8888888888P"

# Extender vigencia de una llave GPG/PGP ya vencida

Hay maneras fáciles de extender la fecha de vencimiento de una llave **GPG** de manera amigable y no tan amigable.

Desde **Thunderbird** [https://www.thunderbird.net/](https://www.thunderbird.net/) no hay una manera gráfica de extender la caducidad de una llave con subllaves una vez que ya esta vencida, si queremos realizarlo aparecera este mensaje:

 {% highlight ruby %}'This is a key with a complex structure, changing its expiry date isn't supported'{% endhighlight %}

Para poder seguir usando la llave vencida podemos extender su validez via terminal:

Primero localizamos la llave en cuestion:

{% highlight php %}
$ gpg --list-keys carlosm2@riseup.net

pub   rsa4096/0x5FDA7A75CE42E670 2016-03-17 [SCA] [caducó: 2022-03-17]
      Huella de clave = CFCA 1F08 6AAF 3654 FBC7  D44C 5FDA 7A75 CE42 E670
uid                [  caducada ] carlosm2 <carlosm2@riseup.net>
{% endhighlight %}

con ese comando anterior podemos ver el ID de nuestra llave para editarlo, tambien podemos ver en este ejemplo que la llave tiene estatus de **caducada**.

ahora editamos la llave con:

{% highlight php %}
$ gpg --edit-key 0x5FDA7A75CE42E670
{% endhighlight %}

lo que nos muestra:

{% highlight php %}
sec  rsa4096/0x5FDA7A75CE42E670
     creado: 2016-03-17  caducó: 2022-03-17  uso: SCA 
     confianza: absoluta      validez: caducada
ssb  rsa4096/0x714AC1ACF83A13E9
     creado: 2016-03-17  caducó: 2022-03-18  uso: E   
[  caducada ] (1). carlosm2 <carlosm2@riseup.net>
{% endhighlight %}

despues se selecciona la llave principal con **key 0**:

y **expire**, 1y (1 year/año en este caso)

{% highlight php %}

gpg> expire

Cambiando caducidad de clave primaria.
Por favor, especifique el período de validez de la clave.
         0 = la clave nunca caduca
      <n>  = la clave caduca en n días*
      <n>w = la clave caduca en n semanas
      <n>m = la clave caduca en n meses
      <n>y = la clave caduca en n años
¿Validez de la clave (0)? 1y
{% endhighlight %}

se mostrará la confirmación del cambio:

{% highlight php %}
La clave caduca mié 22 mar 2023 16:04:13 CST
¿Es correcto? (s/n) 
{% endhighlight %}

pedirá la contraseña para aplicar el cambio

en el caso especifico de mi clave tengo subclaves, las que me sugiere tambien modificar su vigencia

{% highlight php %}
gpg: AVISO: Tu subclave de cifrado caduca pronto.
gpg: Puede que también quieras cambiar su fecha de caducidad.
gpg> 
{% endhighlight %}

esto lo hago con **key 1**

con este comando veremos de nuevo nuestra llave maestra con la nueva caducidad y un **'*'** junto a la subclave **ssb** y la vigencia pendiente por cambiar:

{% highlight php %}
sec  rsa4096/0x5FDA7A75CE42E670
     creado: 2016-03-17  caduca: 2023-03-22  uso: SCA 
     confianza: absoluta      validez: absoluta
ssb* rsa4096/0x714AC1ACF83A13E9
     creado: 2016-03-17  caducó: 2022-03-18  uso: E   
[  absoluta ] (1). carlosm2 <carlosm2@riseup.net>
{% endhighlight %}

entonces repito los pasos:

	expire
		1y
		   guardar

y guardamos con: 

{% highlight php %} gpg> save {% endhighlight %}

y listo, podemos verificar vigencia con:

{% highlight php %}
$ gpg --list-key 0x5FDA7A75CE42E670
pub   rsa4096/0x5FDA7A75CE42E670 2016-03-17 [SCA] [caduca: 2023-03-22]
      Huella de clave = CFCA 1F08 6AAF 3654 FBC7  D44C 5FDA 7A75 CE42 E670
uid                [  absoluta ] carlosm2 <carlosm2@riseup.net>
sub   rsa4096/0x714AC1ACF83A13E9 2016-03-17 [E] [caduca: 2023-03-22]
{% endhighlight %}


			
			















