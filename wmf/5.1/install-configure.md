---
title: Installieren und Konfigurieren von WMF 5.1 (Preview)
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# Installieren und Konfigurieren von WMF 5.1 (Preview) #

***Beachten Sie Folgendes:*** 
*Dies ist ein Platzhalter. Die folgenden Links führen zu WMF 5.0-Versionen und werden aktualisiert, sobald die Binärdateien freigegeben werden.*

Laden Sie das WMF 5.1-Paket für das Betriebssystem und die Architektur herunter, in der es installiert werden soll:

| Betriebssystem       | Architektur | Paketname              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


## Installieren von WMF 5.1 über den Windows-Explorer (bzw. Datei-Explorer in Windows Server 2012 R2 und Windows 8.1)

1. Wechseln Sie zum Ordner, in den Sie die MSU-Datei heruntergeladen haben.

2. Doppelklicken Sie auf die MSU-Datei, um sie auszuführen.

## Installieren von WMF 5.1 über die Eingabeaufforderung##

1. Öffnen Sie nach dem Herunterladen des richtigen Pakets für die Architektur Ihres Computers ein Eingabeaufforderungsfenster mit erhöhten Benutzerrechten (Als Administrator ausführen). Bei den Server Core-Installationsoptionen von Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1 wird das Eingabeaufforderungsfenster standardmäßig mit erhöhten Benutzerrechten geöffnet.

2. Wechseln Sie zum Ordner, in den Sie das Installationspaket für WMF 5.1 heruntergeladen oder kopiert haben.

3. Führen Sie einen der folgenden Befehle aus:
    - Führen Sie auf Computern mit Windows Server 2012 R2 oder Windows 8.1 x64 `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet` aus.
    - Führen Sie auf Computern mit Windows Server 2012 `W2K12-KB3156423-x64.msu /quiet` aus.
    - Führen Sie auf Computern mit Windows Server 2008 R2 SP1 oder Windows 7 SP1 x64 `Win7AndW2K8R2-KB3156424-x64.msu /quiet` aus.
    - Führen Sie auf Computern mit Windows Server 8.1 x86 `Win8.1-KB3156422-x86.msu /quiet` aus.
    - Führen Sie auf Computern mit Windows Server 7 SP1 x86 `Win7-KB3156424-x86.msu /quiet` aus.

## Zusätzliche Installationshinweise für Windows Server 2008 SP1 und Windows 7 SP1##
Für Installation von WMF 5.1 unter Windows Server 2008 SP1 oder Windows 7 SP1 muss Folgendes installiert sein:
- Das neueste Service Pack
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)

> **WinRM-Abhängigkeit:** Windows PowerShell DSC (Desired State Configuration) hängt von WinRM ab. Unter Windows Server 2008 R2 und Windows 7 ist WinRM nicht standardmäßig aktiviert. Führen Sie zum Aktivieren von WinRM in einer Windows PowerShell-Sitzung mit erhöhten Benutzerrechten `Set-WSManQuickConfig` aus.




<!--HONumber=Jul16_HO2-->


