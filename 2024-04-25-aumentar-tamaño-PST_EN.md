---
layout: post
title:  "Increase PST Outlook validity"
date:   2024-04-26 12:32:00
categories: outlook mocosoft powershell
---
## How to Increase the Outlook PST File Size Limit
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

Microsoft Outlook has a 50 GB size limit, which is excessive and makes it difficult to manage for both the file system and any software that needs to handle files of that size. However, I encountered a case where this limit needed to be increased for Outlook to continue functioning correctly. This required editing the following [Windows Registry file](https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/windows-registry-advanced-users).

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

and that's all.
