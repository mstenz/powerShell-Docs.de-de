---
title: Starten des Windows PowerShell 2.0-Moduls
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
---
# Starten des Windows PowerShell 2.0-Moduls
In diesem Abschnitt wird erläutert, wie das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul unter [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] und [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul enthalten, und auf anderen Systemen gestartet wird, auf denen [!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] installiert sind.

[!INCLUDE[psversion4](../Token/psversion4_md.md)] und [!INCLUDE[psversion3](../Token/psversion3_md.md)] sind mit [!INCLUDE[psversion2](../Token/psversion2_md.md)] abwärtskompatibel. Cmdlets, Anbieter, Snap-Ins, Module und Skripts, die für [!INCLUDE[psversion2](../Token/psversion2_md.md)] geschrieben wurden, können in [!INCLUDE[psversion4](../Token/psversion4_md.md)] und [!INCLUDE[psversion3](../Token/psversion3_md.md)] unverändert ausgeführt werden. Doch aufgrund einer Änderung der Richtlinie für die Laufzeitaktivierung in Microsoft .NET Framework 4 können [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Hostprogramme, die für [!INCLUDE[psversion2](../Token/psversion2_md.md)] geschrieben und mit Common Language Runtime (CLR) 2.0 kompiliert wurden, nicht unverändert in [!INCLUDE[psversion3](../Token/psversion3_md.md)] oder [!INCLUDE[psversion4](../Token/psversion4_md.md)] ausgeführt werden, die mit CLR 4.0 kompiliert wurden. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul soll ausschließlich verwendet werden, wenn ein vorhandenes Skript oder Hostprogramm nicht ausgeführt werden kann, da es nicht mit [!INCLUDE[psversion4](../Token/psversion4_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] oder Microsoft .NET Framework 4 kompatibel ist. Solche Fälle sind allerdings eher selten.

Viele Programme, die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul erfordern, starten es automatisch. Diese Anweisungen gelten für die seltenen Fälle, in denen Sie das Modul manuell starten müssen.

## Installieren und Aktivieren erforderlicher Programme
Vor dem Starten des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls aktivieren Sie das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul und Microsoft .NET Framework 3.5 mit Service Pack 1. Anweisungen hierzu finden Sie unter [Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

Systeme, auf denen [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) oder [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] installiert sind, verfügen über alle erforderlichen Komponenten. Es ist keine weitere Konfiguration erforderlich. Informationen zum Installieren von [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) oder [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] finden Sie unter [Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Starten des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls
Beim Starten von [!INCLUDE[mshshort](../Token/mshshort_md.md)] wird die neueste Version standardmäßig gestartet. Zum Starten von [!INCLUDE[mshshort](../Token/mshshort_md.md)] mit dem [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul verwenden Sie den „Version“-Parameter von „PowerShell.exe“. Sie können den Befehl an jeder Eingabeaufforderung einschließlich Windows PowerShell und „Cmd.exe“ ausführen.

```
PowerShell.exe -Version 2
```

## Starten einer Remotesitzung mit dem [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul
Zum Ausführen des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls in einer Remotesitzung erstellen Sie auf dem Remotecomputer eine Sitzungskonfiguration (auch „Endpunkt“ genannt), die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul lädt. Die Sitzungskonfiguration wird auf dem Remotecomputer gespeichert und kann von jedem autorisierten Benutzer verwendet werden, um Sitzungen zu erstellen, die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul verwenden.

Dies ist eine komplexe Aufgabe, die in der Regel von einem Systemadministrator ausgeführt wird.

Im folgenden Verfahren wird der **PSVersion**-Parameter des Cmdlets [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) zum Erstellen einer Sitzungskonfiguration verwendet, die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul nutzt. Sie können auch den **PowerShellVersion**-Parameter des Cmdlets [New-PSSessionConfigurationFile](assetId:///5f3e3633-6e90-479c-aea9-ba45a1954866) verwenden, um eine Sitzungskonfigurationsdatei für eine Sitzung zu erstellen, die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul lädt. Sie können auch den **PSVersion**-Parameter des Cmdlets [Set-PSSessionConfiguration](assetId:///b21fbad3-1759-4260-b206-dcb8431cd6ea) verwenden, um eine Sitzungskonfigurationsdatei so zu ändern, dass das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul verwendet wird.

Weitere Informationen zu Sitzungskonfigurationsdateien finden Sie unter [about_Session_Configurations](assetId:///c7217447-1ebf-477b-a8ef-4dbe9a1473b8).Informationen zu Sitzungskonfigurationen, einschließlich Einrichtung und Sicherheit, finden Sie unter [about_Session_Configurations [v4]](assetId:///a2fbe12a-350c-4d04-be50-24102824e3ab).

#### So starten Sie eine [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Remotesitzung

1.  Zum Erstellen einer Sitzungskonfiguration, die das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul erfordert, verwenden Sie den **PSVersion**-Parameter des Cmdlets [Register-PSSessionConfiguration](assetId:///e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) mit dem Wert „2.0“. Führen Sie diesen Befehl auf dem Computer auf der Serverseite oder dem empfangenden Ende der Verbindung aus.

    Der folgende Befehl erstellt die PS2-Sitzungskonfiguration auf dem Computer „Server01“. Starten Sie [!INCLUDE[psversion4](../Token/psversion4_md.md)] oder [!INCLUDE[psversion3](../Token/psversion3_md.md)] mit der Option **Als Administrator ausführen**, um diesen Befehl auszuführen.

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  Zum Erstellen einer Sitzung auf dem Computer „Server01“, der die PS2-Sitzungskonfiguration nutzt, verwenden Sie den **ConfigurationName**-Parameter von Cmdlets, die eine Remotesitzung aufbauen, wie z. B. das Cmdlet [New-PSSession](assetId:///76f6628c-054c-4eda-ba7a-a6f28daaa26f).

    Wenn eine Sitzung gestartet wird, die die Sitzungskonfiguration verwendet, wird das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul automatisch in die Sitzung geladen.

    Der folgende Befehl erstellt eine Sitzung auf dem Computer „Server01“, die die PS2-Sitzungskonfiguration verwendet. Der Befehl speichert die Sitzung in der Variablen „$s“.

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## Starten eines Hintergrundauftrags mit dem [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul
Zum Starten eines Hintergrundauftrags mit dem [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul verwenden Sie den **PSVersion**-Parameter des Cmdlets [Start-Job](assetId:///2bc04935-0deb-4ec0-b856-d7290cca6442).

Der folgende Befehl startet einen Hintergrundauftrag mit dem [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul.

```
Start-Job {Get-Process} -PSVersion 2.0
```

Weitere Informationen zu Hintergrundaufträgen finden Sie unter [about_Jobs [v4]](assetId:///7362512a-8a4e-4575-b2ea-a740e5c4f002).



<!--HONumber=Apr16_HO1-->


