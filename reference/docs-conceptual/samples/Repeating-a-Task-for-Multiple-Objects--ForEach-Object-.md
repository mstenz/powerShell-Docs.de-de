---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Wiederholen einer Aufgabe für mehrere Objekte
ms.openlocfilehash: 1442507c4213476f65df3401c1021f8d0fc31956
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030804"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Wiederholen einer Aufgabe für mehrere Objekte (ForEach-Object)

Das Cmdlet **ForEach-Object** verwendet Skriptblöcke und den Deskriptor `$_` für das aktuelle Pipelineobjekt, um Ihnen das Ausführen eines Befehls für jedes Objekt in der Pipeline zu ermöglichen. Damit können Sie einige komplizierte Aufgaben ausführen.

Besonders nützlich kann dies sein, wenn Sie Daten bearbeiten möchten, um sie besser nutzen zu können. Beispielsweise kann die Klasse „Win32_LogicalDisk“ aus WMI verwendet werden, um für jeden lokalen Datenträger Informationen zum freien Speicherplatz zurückzugeben. Die Daten werden als Bytes zurückgegeben, sind daher schwierig zu lesen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Sie können den Wert von „FreeSpace in MB konvertieren, indem Sie jeden Wert zweimal durch 1024 dividieren. Mit der ersten Division werden die Daten in KB umgerechnet, bei der zweiten in MB. Sie können dazu einen ForEach-Object-Skriptblock verwenden, indem Sie Folgendes eingeben:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Leider erhalten Sie als Ausgabe nun Daten ohne zugeordnete Bezeichnung. Da WMI-Eigenschaften wie diese schreibgeschützt sind, kann FreeSpace nicht direkt konvertiert werden. Wenn Sie Folgendes eingeben:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Erhalten Sie eine Fehlermeldung:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Sie könnten die Daten mithilfe bestimmter erweiterter Techniken neu anordnen, ein einfacherer Ansatz ist jedoch die Erstellung ein neues Objekts mit **Select-Object**.
