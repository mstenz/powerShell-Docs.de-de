---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ändern des Computerstatus
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736912"
---
# <a name="changing-computer-state"></a>Ändern des Computerstatus

Verwenden Sie zum Zurücksetzen eines Computers in PowerShell entweder ein Standardbefehlszeilentool, WMI oder die CIM-Klasse.
Sie verwenden PowerShell zwar nur zum Ausführen des Tools, dennoch erfahren Sie einige wichtige Details über die Arbeit mit externen Tools in PowerShell, indem Sie lernen, wie Sie den Energiezustand eines Computers in PowerShell ändern.

## <a name="locking-a-computer"></a>Sperren eines Computers

Die einzige Möglichkeit, einen Computer unmittelbar mit den standardmäßig verfügbaren Tools zu sperren, besteht im Aufrufen der Funktion **LockWorkstation()** in **user32.dll**:

```powershell
rundll32.exe user32.dll,LockWorkStation
```

Mit diesem Befehl wird die Arbeitsstation sofort gesperrt. Hierbei wird **rundll32.exe** zum Ausführen von Windows-DLLs (und Speichern ihrer Bibliotheken für die wiederholte Verwendung) verwendet, um `user32.dll` auszuführen – eine Bibliothek mit Windows-Verwaltungsfunktionen.

Wenn Sie eine Arbeitsstation sperren, während die schnelle Benutzerumschaltung aktiviert ist, z. B. bei Computern unter Windows XP, wird der Benutzeranmeldebildschirm anstelle des Bildschirmschoners des aktuellen Benutzers angezeigt.

Um bestimmte Sitzungen auf einem Terminalserver herunterzufahren, verwenden Sie das Befehlszeilentool **tsshutdn.exe**.

## <a name="logging-off-the-current-session"></a>Abmelden der aktuellen Sitzung

Es sind mehrere verschiedene Verfahren verfügbar, um eine Sitzung auf dem lokalen System abzumelden. Die einfachste Möglichkeit besteht in der Verwendung des Remotedesktop-/Terminaldienste-Befehlszeilentools **logoff.exe**. (Weitere Informationen erhalten Sie, indem Sie an der PowerShell-Eingabeaufforderung `logoff /?` eingeben). Zum Abmelden der aktuellen aktiven Sitzung geben Sie `logoff` ohne Argumente ein.

Sie können auch das Tool **shutdown.exe** mit der zugehörigen Abmeldeoption verwenden:

```powershell
shutdown.exe -l
```

Eine weitere Möglichkeit ist die Verwendung von WMI. Die Klasse **Win32_OperatingSystem** umfasst eine **Shutdown**-Methode.
Durch Aufrufen der Methode mit dem 0-Flag wird die Abmeldung initiiert:

Weitere Informationen zur **Shutdown**-Methode finden Sie unter [Shutdown-Methode der Win32_OperatingSystem-Klasse](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem).

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Herunterfahren oder Neustarten eines Computers

Das Herunterfahren und Neustarten von Computern wird im Allgemeinen vom gleichen Tasktyp ausgeführt. Mit Tools, die einen Computer herunterfahren, kann normalerweise auch ein Neustart ausgeführt werden, und umgekehrt. Es gibt zwei einfache Optionen für den Neustart eines Computers über PowerShell. Verwenden Sie entweder **tsshutdn.exe** oder **shutdown.exe** mit den geeigneten Argumenten. Ausführliche Informationen zur Verwendung erhalten Sie über `tsshutdn.exe /?` oder `shutdown.exe /?`.

Sie können Ihren Computer auch direkt über PowerShell herunterfahren und neu starten.

Verwenden Sie den Befehl „Stop-Computer“, um den Computer herunterzufahren.

```powershell
Stop-Computer
```

Verwenden Sie den Befehl „Restart-Computer“, um das Betriebssystem neu zu starten.

```powershell
Restart-Computer
```

Um einen sofortigen Neustart des Computers zu erzwingen, verwenden Sie den -Force-Parameter.

```powershell
Restart-Computer -Force
```
