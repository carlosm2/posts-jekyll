---
layout: post
title:  "Identificar versión de Windows en una USB desde Linux"
date:   2026-07-01 10:32:00
categories: linux windows usb
---

# Pasos para poder identificar la versión de Windows que tiene un instalador USB Windows desde Linux

Si tienes una memoria USB con un instalador de windows aparecera con el nombre: **ESD-USB** pero si de casualidad tienes dos o mas USBs y de diferentes versiones de instalador
de Micro$oft Windows será dificil saber cual es el instalador de Windows versión 10 y version 11, y el tipo de instalador que tienes. Por lo que puedes instalar en tu sistema Linux el siguiente programa:

sudo apt install viminfo

para luego insertar tu USB, montarlo en tu sistema y dirigirte a:

cd /media/tuusuario/ESD-USB/sources

ahi en sources puedes ejecutar:

{% highlight ruby %}

cacu@tech:/media/cacu/ESD-USB/sources#sudo wiminfo install2.swm
WIM Information:
----------------
Path:           install2.swm
GUID:           0x1c8fdb3805ddc54fb29694f8aaeca103
Version:        3584
Image Count:    4
Compression:    LZMS
Chunk Size:     131072 bytes
Part Number:    2/2
Boot Index:     0
Size:           5750478272 bytes
Attributes:     Relative path junction

Available Images:
-----------------
Index:                  1
Name:                   Windows 11 Home
Description:            Windows 11 Home
Display Name:           Windows 11 Home
Display Description:    Windows 11 Home
Directory Count:        33375
File Count:             146492
Total Bytes:            24052648098
Hard Link Bytes:        10126444322
Creation Time:          Thu May 07 08:30:59 2026 UTC
Last Modification Time: Wed Jun 03 18:33:56 2026 UTC
Architecture:           x86_64
Product Name:           Microsoft® Windows® Operating System
Edition ID:             Core
Installation Type:      Client
Product Type:           WinNT
Product Suite:          Terminal Server
Languages:              es-MX 
Default Language:       es-MX
System Root:            WINDOWS
Major Version:          10
Minor Version:          0
Build:                  26200
Service Pack Build:     8457
Service Pack Level:     0
Flags:                  Core
WIMBoot compatible:     no

Index:                  2
Name:                   Windows 11 Home Single Language
Description:            Windows 11 Home Single Language
Display Name:           Windows 11 Home Single Language
Display Description:    Windows 11 Home Single Language
Directory Count:        33375
File Count:             146493
Total Bytes:            24049223151
Hard Link Bytes:        10126444322
Creation Time:          Thu May 07 08:33:22 2026 UTC
Last Modification Time: Wed Jun 03 18:34:01 2026 UTC
Architecture:           x86_64
Product Name:           Microsoft® Windows® Operating System
Edition ID:             CoreSingleLanguage
Installation Type:      Client
Product Type:           WinNT
Product Suite:          Terminal Server
Languages:              es-MX 
Default Language:       es-MX
System Root:            WINDOWS
Major Version:          10
Minor Version:          0
Build:                  26200
Service Pack Build:     8457
Service Pack Level:     0
Flags:                  CoreSingleLanguage
WIMBoot compatible:     no

Index:                  3
Name:                   Windows 11 Education
Description:            Windows 11 Education
Display Name:           Windows 11 Education
Display Description:    Windows 11 Education

{% endhighlight %}

Esto te mostrara las versiónes de Windows que tiene cada USB, si es win 10, 11, Educatión, el lenguage, etc.
