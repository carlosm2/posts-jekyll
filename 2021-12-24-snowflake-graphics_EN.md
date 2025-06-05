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

In my *snowflake proxy* output file I saw an increase in activity, not only there but also in the resource consumption of the entire operating system.

{% highlight c++ %}

# filter results with traffic data:

less nohup.out | grep --color=always "Traffic throughput"

# send the obtained data to a file:

less nohup.out | grep --color=always "Traffic throughput" > trafico.txt

{% endhighlight %}

This gave me the data on active connections and their days-hours, but also a lot of other data like the amount of kbs transferred, but I only wanted to know the number of connections per day and their increase during my sample time of **107 days**.

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


