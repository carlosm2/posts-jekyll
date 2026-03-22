---
layout: post
title:  "Increase PST Outlook validity"
date:   2024-04-26 12:32:00
categories: outlook mocosoft powershell
---
## Increase outlook PST size validity
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

Micro$oft Outlook tiene limites de tamaño a 50 GB, lo cual es demasiado (porque no es manejable para cualquier sistema de archivos y software manejar un archivo tan grandes)  y de por si hace dificil manejar comodamente este programa, si tienen
el caso de tener que habilitar un tamaño mayor para que outlook siga funcionando tienen que editar este archivo del registro.

{% highlight ruby %}

    Outlook 2003: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\11.0\Outlook\PST
    Outlook 2007: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\12.0\Outlook\PST
    Outlook 2010: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\14.0\Outlook\PST
    Outlook 2013: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\15.0\Outlook\PST
    Outlook 2016: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\PST
    Outlook 2019: HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\PST

{% endhighlight %}

it can be done with Powershell 
[https://learn.microsoft.com/es-es/powershell/scripting/overview?view=powershell-7.4](https://learn.microsoft.com/es-es/powershell/scripting/overview?view=powershell-7.4)

before editing, you have to do a backup.

{% highlight ruby %}


# Specify the path to the registry key you want to back up.
$registryKey = "HKLM:\Software\YourSoftware"

# Specify the path where you want to save the .reg file
$backupFilePath = "C:\Backup\registry_backup.reg"

# Export the registry key from the .reg file
Export-CimInstance -ClassName StdRegProv -Namespace root\default -MethodName ExportKey -Arguments @{
    hDefKey = "HKEY_LOCAL_MACHINE"
    sSubKeyName = $registryKey
    sFileName = $backupFilePath
}

{% endhighlight %}

Once the registry is backed up, we can edit it to increase the default PST file size.
In my case, I'm going to edit the Outlook 2016 registry.

{% highlight ruby %}

    HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\16.0\Outlook\PST

{% endhighlight %}

Add a new **DWORD** (32 Bit) Value with the name **MaxLargeFileSize** 
Value Data: 102400 Decimal (100GB)

Add a new **DWORD** (32 Bit) Value with the name **WarnLargeFileSize** 
Value Data: 97280 Decimal (95GB)

and done. 


