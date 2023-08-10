---
layout: post
title:  "Descifrar Bitlocker desde Tails"
date:   2023-07-07 12:32:00
categories: tails bitlocker cifrado
---

# Descifrar disco duro cifrado con Bitlocker desde Tails


            .-""-.
           / .--. \
          / /    \ \
          | |    | |
          | |.-""-.|
         ///`.::::.`\
        ||| ::/  \:: ;
        ||; ::\__/:: ;
         \\\ '::::' /
          `=':-..-'`
 

Trabajo muy seguido con computadoras Windows 10, dichas computadoras por una buena politica de privacidad y seguridad están cifradas con [Bitlocker](https://es.wikipedia.org/wiki/BitLocker_Drive_Encryption).

Tenia una instalación corrupta del sistema y necesitaba rescatar archivos y como siempre a la mano tengo una USB Tails asi que me puse a leer sobre descifrar bitlocker desde GNU/Linux en donde vi que existe documentación y un paquete: [dislocker](https://github.com/Aorimn/dislocker) pero no fue necesario, antes de intentar esta forma lo hice desde mi USB Tails.

**Paso 1** Cargar inicio desde Tails 
[https://tails.net/doc/first_steps/start/pc/index.es.html](https://tails.net/doc/first_steps/start/pc/index.es.html)

**Paso 2** Habilitar contraseña de administración, esto será necesario para tener permiso de montar una unidad en nuestro sistema
[https://tails.net/doc/first_steps/welcome_screen/administration_password/index.es.html](https://tails.net/doc/first_steps/welcome_screen/administration_password/index.es.html)

**Paso 3** En nautilus (explorador de archivos) dar click en donde dice "Otras ubicaciones" para seleccionar nuestro disco duro cifrado que aparecerá con un icono de un candado.

**Paso 4** Nos pedirá la contraseña numerica de Bitlocker, la tecleamos con los **guiones incluidos**, despues pedira la contraseña de administración que habilitamos al inicio. Y listo.







