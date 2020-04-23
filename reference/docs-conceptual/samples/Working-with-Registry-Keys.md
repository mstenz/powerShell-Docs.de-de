---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Arbeiten mit Registrierungsschlüsseln
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736844"
---
# <a name="working-with-registry-keys"></a>Arbeiten mit Registrierungsschlüsseln

Registrierungsschlüssel sind Elemente auf PowerShell-Laufwerken, deshalb gleicht deren Verwendung der Arbeit mit Dateien und Ordnern. Ein wichtiger Unterschied besteht darin, dass jedes Element auf einem registrierungsbasierten PowerShell-Laufwerk ein Container ist, genau wie ein Ordner auf einem Dateisystemlaufwerk. Registrierungseinträge und deren zugehörige Werte sind jedoch Eigenschaften der Elemente, nicht unterschiedliche Elemente.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Auflisten aller Unterschlüssel eines Registrierungsschlüssels

Mit `Get-ChildItem` können Sie alle Elemente anzeigen, die sich direkt in einem Registrierungsschlüssel befinden. Fügen Sie den optionalen Parameter **Force** hinzu, um ausgeblendete oder Systemelemente anzuzeigen. Dieser Befehl zeigt z. B. die Elemente an, die sich direkt auf dem PowerShell-Laufwerk `HKCU:` befinden, das der Registrierungsstruktur `HKEY_CURRENT_USER` entspricht:

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

Dies sind die im Registrierungs-Editor (Regedit.exe) unter `HKEY_CURRENT_USER` angezeigten Schlüssel der obersten Ebene.

Sie können diesen Registrierungspfad auch anhand des Namens des Registrierungsanbieters gefolgt von `::` angeben. Der vollständige Name des Registrierungsanbieters lautet `Microsoft.PowerShell.Core\Registry`, aber dieser kann auf `Registry` verkürzt werden. Jeder der folgenden Befehle listet die Inhalte direkt unter `HKCU:` auf.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Diese Befehle listen nur die direkt enthaltenen Elemente auf, ähnlich dem Befehl `DIR` in **Cmd.exe** oder `ls` in einer UNIX-Shell. Um enthaltene Elemente anzuzeigen, müssen Sie den Parameter **Recurse** angeben. Um alle Registrierungsschlüssel in `HKCU:` aufzulisten, verwenden Sie den folgenden Befehl.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem` stellt mit den Parametern **Path**, **Filter**, **Include** und **Exclude** komplexe Filterfunktionen zur Verfügung, die allerdings typischerweise nur auf Namen basieren. Zum Durchführen einer komplexen Filterung basierend auf anderen Eigenschaften von Elementen können Sie das Cmdlet `Where-Object` verwenden. Der folgende Befehl sucht alle Schlüssel in `HKCU:\Software`, die nicht mehr als einen Unterschlüssel und zudem genau vier Werte enthalten:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Kopieren von Schlüsseln

Das Kopieren erfolgt mit `Copy-Item`. Das folgende Beispiel kopiert den `CurrentVersion`-Unterschlüssel von `HKLM:\SOFTWARE\Microsoft\Windows\` und alle zugehörigen Eigenschaften nach `HKCU:\`.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

Wenn Sie diesen neuen Schlüssel im Registrierungs-Editor oder über `Get-ChildItem` untersuchen, stellen Sie fest, dass am neuen Speicherort keine Kopien der enthaltenen Unterschlüssel vorhanden sind. Um den gesamten Inhalt eines Containers zu kopieren, müssen Sie den Parameter **Recurse** angeben. Um den vorherigen Kopierbefehl rekursiv zu machen, verwenden Sie diesen Befehl:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

Sie können auch weiterhin andere bereits verfügbare Tools verwenden, um Dateisystemkopien auszuführen. Alle Tools zur Bearbeitung der Registrierung – darunter **reg.exe**, **regini.exe**, **regedit.exe** – sowie COM-Objekte, die die Bearbeitung der Registrierung unterstützen (z. B. **WScript.Shell** und die WMI-Klasse **StdRegProv**) können in Windows PowerShell verwendet werden.

## <a name="creating-keys"></a>Erstellen von Schlüsseln

Das Erstellen neuer Schlüssel in der Registrierung ist einfacher als das Erstellen eines neuen Elements in einem Dateisystem. Da alle Registrierungsschlüssel Container sind, müssen Sie keinen Elementtyp, sondern einfach einen expliziten Pfad angeben, z. B.:

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

Sie können auch einen anbieterbasierten Pfad verwenden, um einen Schlüssel anzugeben:

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>Löschen von Schlüsseln

Das Löschen von Elementen funktioniert im Wesentlichen für alle Anbieter gleich. Die folgenden Befehle entfernen Elemente automatisch ohne Benutzereingriff:

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Entfernen aller Schlüssel unter einem bestimmten Schlüssel

Mit `Remove-Item` können Sie enthaltene Elemente entfernen. Sie werden jedoch aufgefordert, das Entfernen zu bestätigen, wenn ein Element weitere Elemente enthält. Wenn Sie beispielsweise versuchen, den erstellten Unterschlüssel `HKCU:\CurrentVersion` zu löschen, wird Folgendes angezeigt:

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Um enthaltene Elemente ohne Rückfrage zu löschen, geben Sie den Parameter **Recurse** an:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Wenn Sie alle Elemente in `HKCU:\CurrentVersion`, aber `HKCU:\CurrentVersion` selbst nicht löschen möchten, verwenden Sie stattdessen Folgendes:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
