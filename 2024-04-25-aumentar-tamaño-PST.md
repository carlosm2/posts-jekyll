---
layout: post
title:  "Aumentar validez del tamaño del PST Outlook"
date:   2024-04-25 12:32:00
categories: outlook mocosoft powershell
---
## Aumentar validez del tamaño del PST Outlook
        __                      __
     .-'  `'.._...-----..._..-'`  '-.
    /                                \
    |  ,   ,'                '.   ,  |
     \  '-/                    \-'  /
      '._|          _           |_.'
         |    /\   / \    /\    |
         |    \/   | |    \/    |
          \        \"/         /
           '.    =='^'==     .'
             `'------------'`

Micro$oft Outlook tiene limites de tamaño a 50 GB, lo cual es demasiado y de por si hace dificil manejar comodamente este programa, si tienen
el caso de tener que habilitar un tamaño mayor para que outlook siga funcionando tienen que editar este archivo del registro.

{% highlight ruby %}

    Outlook 2003: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\11.0\Outlook\PST
    Outlook 2007: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\12.0\Outlook\PST
    Outlook 2010: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\14.0\Outlook\PST
    Outlook 2013: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\15.0\Outlook\PST
    Outlook 2016: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\PST
    Outlook 2019: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\PST

{% endhighlight %}

se puede hacer con Powershell 
[https://learn.microsoft.com/es-es/powershell/scripting/overview?view=powershell-7.4](https://learn.microsoft.com/es-es/powershell/scripting/overview?view=powershell-7.4)

antes de editar hay que respaldar el registro.

{% highlight ruby %}


# Especifica la ruta la llave del registro que quieres respaldar
$registryKey = "HKLM:\Software\YourSoftware"

# Especifica la ruta donde quieres guardar el .reg file
$backupFilePath = "C:\Backup\registry_backup.reg"

# Exporta la llave del registro .reg file
Export-CimInstance -ClassName StdRegProv -Namespace root\default -MethodName ExportKey -Arguments @{
    hDefKey = "HKEY_LOCAL_MACHINE"
    sSubKeyName = $registryKey
    sFileName = $backupFilePath
}

{% endhighlight %}

una vez respaldado el registro podemos editarlo para poder aumentar el tamaño por defecto del archivo PST
en mi caso voy a editar el registro de Outlook 2016

{% highlight ruby %}

    HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\PST

{% endhighlight %}

Agregar un nuevo **DWORD** (32 Bit) Value con el nombre **MaxLargeFileSize** 
Value Data: 102400 Decimal (100GB)

Agregar un nuevo **DWORD** (32 Bit) Value con el nombre **WarnLargeFileSize** 
Value Data: 97280 Decimal (95GB)

y listo. 


