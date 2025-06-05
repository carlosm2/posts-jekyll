---
layout: post
title:  "Snowflake Requests Increase December 2021"
date:   2021-12-24 12:32:00
categories: softwarelibre tor snowflake proxy
---
# Tor Snowflake Behavioral Analysis December 2021

---------------------                                                                    
@                                                         #    #
@                                                       # #  # #
@                                                      ##### ###
@                                                      ##### ###
@                                                      ##### ###
@                                                      ##### ###
@                                                     ###### ###
@                                                     ###### ###
@                                                     ###### ###
@                                                     ###### ###
@                                                     ###### ###
@                                             #    ## ###### ###
@###############################################################
   septiembre                                         diciembre

---------------------

En mi archivo de salida de *snowflake proxy* se veía un incremento en actividad y no solo ahí sino también en el consumo de recursos de todo el sistema operativo.

{% highlight c++ %}

# filtrar resultados con datos de tráfico:

less nohup.out | grep --color=always "Traffic throughput"

# mandar los datos obtenidos a un archivo:

less nohup.out | grep --color=always "Traffic throughput" > trafico.txt

{% endhighlight %}
Esto me daba los datos de las conexiones activas y sus días-horas, pero también muchos otros datos como la cantidad de kbs transferidos, pero quería únicamente saber la cantidad de conexiones en el día y su incremento durante el tiempo de mi muestra de **107 dias**.

{% highlight c++ %}

# obtener solo las primeras dos columnas:

cut -d: -f '1 2' trafico.txt

# enviar esas dos columnas a un archivo:

cut -d: -f '1 2' trafico.txt >> filtrado.txt

## poner una coma despues de la primera columna de mis datos:

sed 's/ /, /g' filtrado.txt >> filtradoconcomas.txt

{% endhighlight %}

ya con datos separados por comas ya se pueden graficar, pero soy teletubi en esos conceptos asi que uso esta versión web que utiliza **D3.js** 

[https://github.com/densitydesign/raw](https://github.com/densitydesign/raw)

[https://rawgraphs.io/](https://rawgraphs.io/)

con los datos obtuve estas gráficas:

[https://cacu.tech/snowflake/snowflakeconleche.png](https://cacu.tech/snowflake/snowflakeconleche.png)

[https://cacu.tech/snowflake/aumento.png](https://cacu.tech/snowflake/aumento.png)

que muestran el incremento de en promedio **20** peticiones al dia a **280**. 


