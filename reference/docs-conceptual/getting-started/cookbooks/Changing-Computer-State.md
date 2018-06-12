---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ändern des Computerstatus
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251516"
---
# <a name="changing-computer-state"></a>Ändern des Computerstatus

Verwenden Sie zum Zurücksetzen eines Computers in Windows PowerShell entweder ein Standardbefehlszeilentool oder ein WMI-Klasse. Sie verwenden Windows PowerShell zwar nur zum Ausführen des Tools, dennoch erfahren Sie einige wichtige Details über die Arbeit mit externen Tools in Windows PowerShell, indem Sie lernen, wie Sie den Energiezustand eines Computers in Windows PowerShell ändern.

### <a name="locking-a-computer"></a>Sperren eines Computers

Die einzige Möglichkeit, einen Computer unmittelbar mit den standardmäßig verfügbaren Tools zu sperren, besteht im Aufrufen der Funktion **LockWorkstation()** in **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Mit diesem Befehl wird die Arbeitsstation sofort gesperrt. Hierbei wird *rundll32.exe* zum Ausführen von Windows-DLLs (und Speichern ihrer Bibliotheken für die wiederholte Verwendung) verwendet, um „user32.dll“, eine Bibliothek von Windows-Verwaltungsfunktionen, auszuführen.

Wenn Sie eine Arbeitsstation sperren, während die schnelle Benutzerumschaltung aktiviert ist, z. B. bei Computern unter Windows XP, wird der Benutzeranmeldebildschirm anstelle des Bildschirmschoners des aktuellen Benutzers angezeigt.

Um bestimmte Sitzungen auf einem Terminalserver herunterzufahren, verwenden Sie das Befehlszeilentool **tsshutdn.exe**.

### <a name="logging-off-the-current-session"></a>Abmelden der aktuellen Sitzung

Es sind mehrere verschiedene Verfahren verfügbar, um eine Sitzung auf dem lokalen System abzumelden. Die einfachste Möglichkeit besteht in der Verwendung des Remotedesktop-/Terminaldienste-Befehlszeilentools **logoff.exe**. (Weitere Informationen erhalten Sie, indem Sie an der Windows PowerShell-Eingabeaufforderung **logoff /?** eingeben). Zum Abmelden der aktuellen aktiven Sitzung geben Sie **logoff** ohne Argumente ein.

Sie können auch das Tool **shutdown.exe** mit der zugehörigen Abmeldeoption verwenden:

```
shutdown.exe -l
```

Eine dritte Möglichkeit ist die Verwendung von WMI. Die Klasse „Win32_OperatingSystem“ besitzt eine Win32Shutdown-Methode. Durch Aufrufen der Methode mit dem 0-Flag wird die Abmeldung initiiert:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Weitere Informationen und andere Funktionen der Win32Shutdown-Methode finden Sie unter „Win32Shutdown-Methode der Win32_OperatingSystem-Klasse“ in MSDN.

### <a name="shutting-down-or-restarting-a-computer"></a>Herunterfahren oder Neustarten eines Computers

Das Herunterfahren und Neustarten von Computern wird im Allgemeinen vom gleichen Tasktyp ausgeführt. Mit Tools, die einen Computer herunterfahren, kann normalerweise auch ein Neustart ausgeführt werden, und umgekehrt. Es gibt zwei einfache Optionen für den Neustart eines Computers aus Windows PowerShell. Verwenden Sie entweder „Tsshutdn.exe“ oder „Shutdown.exe“ mit den entsprechenden Argumenten. Ausführliche Informationen zur Verwendung erhalten Sie mit **tsshutdn.exe /?** oder **shutdown.exe /?**.

Sie können Ihren Computer auch direkt über Windows PowerShell herunterfahren und neu starten.

Verwenden Sie den Befehl „stop-computer“, um Ihren Computer herunterzufahren.

```powershell
stop-computer
```

Verwenden Sie den Befehl „restart-computer“, um das Betriebssystem neu zu starten.

```powershell
restart-computer
```
