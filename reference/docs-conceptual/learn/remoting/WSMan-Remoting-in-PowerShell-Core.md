---
title: WS-Management-Remoting (WSMan) in PowerShell Core
description: Remoting in PowerShell Core mithilfe von WSMan
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402046"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>WS-Management-Remoting (WSMan) in PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Anweisungen zum Erstellen eines Remoting-Endpunkts

Das PowerShell Core-Paket für Windows enthält ein WinRM-Plug-In (`pwrshplugin.dll`) und ein Installationsskript (`Install-PowerShellRemoting.ps1`) in `$PSHome`.
Diese Dateien ermöglichen PowerShell eingehende PowerShell-Remoteverbindungen anzunehmen, wenn ihr Endpunkt angegeben ist.

### <a name="motivation"></a>Beweggründe

Eine PowerShell-Installation kann mithilfe von `New-PSSession` und `Enter-PSSession` PowerShell-Sitzungen mit Remotecomputern erstellen.
Der Benutzer muss zunächst einen WinRM-Remoting-Endpunkt erstellen, um PowerShell das Annehmen von eingehenden Remoteverbindungen zu erlauben.
Dies ist ein Szenario mit expliziter Anmeldung, bei dem der Benutzer „Install-PowerShellRemoting.ps1“ ausführt, um den WinRM-Endpunkt zu erstellen.
Das Installationsskript ist eine kurzfristige Lösung, bis `Enable-PSRemoting` eine zusätzliche Funktion hinzugefügt wird, um diese Aktion auszuführen.
Weitere Informationen finden Sie im Ticket [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Skriptaktionen

Das Skript

1. Erstellt ein Verzeichnis für das Plug-In unter %windir%\System32\PowerShell
1. Kopiert „Pwrshplugin.dll“ an diesen Speicherort
1. Erstellt eine Konfigurationsdatei
1. Registriert das Plug-In für WinRM

### <a name="registration"></a>Registrierung

Das Skript muss in einer PowerShell-Sitzung auf Administratorebene ausgeführt werden, und wird in zwei Modi ausgeführt.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Wird durch die PowerShell-Instanz ausgeführt, die es registriert

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Wird durch eine andere PowerShell-Instanz für die Instanz ausgeführt, die registriert wird

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Beispiel:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**HINWEIS:** Das Remoting-Registrierungsskript startet WinRM neu, deshalb werden alle vorhandenen PSRP-Sitzungen sofort beendet, wenn das Skript ausgeführt wurde. Wenn es während einer Remotesitzung ausgeführt wird, wird die Verbindung beendet.

## <a name="how-to-connect-to-the-new-endpoint"></a>Herstellen einer Verbindung mit dem neuen Endpunkt

Erstellen Sie eine PowerShell-Sitzung mit dem neuen PowerShell-Endpunkt, indem Sie `-ConfigurationName "some endpoint name"` angeben. Verwenden Sie zum Verbinden mit der PowerShell-Instanz aus dem obigen Beispiel einen dieser Aufrufe:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Beachten Sie, dass `New-PSSession`- und `Enter-PSSession`-Aufrufe, die `-ConfigurationName` nicht angeben, den PowerShell-Standardendpunkt `microsoft.powershell` als Ziel verwenden.