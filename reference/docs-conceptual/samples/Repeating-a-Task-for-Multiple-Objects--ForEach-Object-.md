---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Wiederholen einer Aufgabe für mehrere Objekte
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736878"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Wiederholen einer Aufgabe für mehrere Objekte (ForEach-Object)

Das Cmdlet `ForEach-Object` verwendet Skriptblöcke und den Deskriptor `$_` für das aktuelle Pipelineobjekt, um Ihnen das Ausführen eines Befehls für jedes Objekt in der Pipeline zu ermöglichen. Damit können Sie einige komplizierte Aufgaben ausführen.

Besonders nützlich kann dies sein, wenn Sie Daten bearbeiten möchten, um sie besser nutzen zu können. Beispielsweise kann die Klasse **Win32_LogicalDisk** aus WMI verwendet werden, um für jeden lokalen Datenträger Informationen zum freien Speicherplatz zurückzugeben. Die Daten werden als Bytes zurückgegeben, sind daher schwierig zu lesen:

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

Der **FreeSpace**-Wert kann durch Division der einzelnen Werte durch 1 MB in Megabyte konvertiert werden. Sie können dazu einen `ForEach-Object`-Skriptblock verwenden, indem Sie Folgendes eingeben:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

Leider erhalten Sie als Ausgabe nun Daten ohne zugeordnete Bezeichnung. Da WMI-Eigenschaften wie diese schreibgeschützt sind, kann **FreeSpace** nicht direkt konvertiert werden. Wenn Sie Folgendes eingeben:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

Erhalten Sie eine Fehlermeldung:

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

Sie könnten die Daten mithilfe bestimmter erweiterter Techniken neu anordnen, ein einfacherer Ansatz ist jedoch die Erstellung eines neues Objekts mit `Select-Object`.
