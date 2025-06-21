---
layout: post
title:  "Format list with sed bash (EN)"
date:   2022-05-20 12:32:00
categories: softwarelibre bash sed
---

       ___________
      |.---------.|
      ||         ||
      ||         ||
      ||         ||
      |'---------'|
       `)__ ____('
       [=== -- o ]--.
     __'---------'__ \
     `""'"""""'""""`/T\
                    \_/
                    


## Arrange word list with sed bash

To format a list in Nahuatl, I had to use KeepassXC.

[https://cacu.tech/softwarelibre,/nahuatl,/keepassxc/2022/06/21/idioma-nahuatl-keepassxc.html](https://cacu.tech/softwarelibre,/nahuatl,/keepassxc/2022/06/21/idioma-nahuatl-keepassxc.html)

I had to look for a list

Fortunately, I have friends who are interested in native languages ​​and who are computer-savvy, so I asked a couple of people who I was sure would be able to provide me with answers. I had already found several dictionaries, but I wanted a word list that was relatively easy to clean so I could have the data in a form that could be used by KeepassXC.

To download the original list you can visit this site:

[https://aulex.org/nah-es/](https://aulex.org/nah-es/) 

which will give you this file:

{% highlight perl %}nah-es.htm{% endhighlight %}

Then you have to filter it, arrange it, the good friend ´petrohs´ gave me this command:

{% highlight perl %}cat nah-es.htm | grep '<p><span class=dict>' 
| sed -e "s/<p><span class=dict>//" -e "s/:.*//"{% endhighlight %}

It was almost perfect, but then I saw that the list had some numbers, because there are words that are repeated because they can have different meanings, there were also question marks and exclamation points, I removed those with this:

{% highlight perl %}cat nah-es.txt | sed 's/[12!¡¿? \-]//g' nah-es.txt > nahuatl-lista.txt{% endhighlight %}

With the data polished, I proceeded to upload it to GitHub and made a Pull Request to upload it to some sites that use these lists in other languages.

[https://github.com/carlosm2/lista-nahuatl](https://github.com/carlosm2/lista-nahuatl)

I thank Don Petrohs [https://github.com/petrohs](https://github.com/petrohs) for helping me format the list.

