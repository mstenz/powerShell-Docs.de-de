---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Auswählen von Objektteilen – Select-Object"
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="selecting-parts-of-objects-select-object"></a>Auswählen von Objektteilen (Select-Object)
Sie können das Cmdlet **Select-Object** verwenden, um neue, angepasste Windows PowerShell-Objekte zu erstellen, die ausgewählte Eigenschaften der zum Erstellen verwendeten Objekte enthalten. Geben Sie den folgenden Befehl ein, um ein neues Objekt zu erstellen, das nur die Eigenschaften „Name“ und „FreeSpace“ der WMI-Klasse „Win32_LogicalDisk“ enthält:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

Nach der Ausgabe des Befehls wird der Datentyp nicht angezeigt, aber wenn Sie das Ergebnis nach „Select-Object“ an „Get-Member“ weiterleiten, erkennen Sie, dass Sie über den neuen Objekttyp „PSCustomObject“ verfügen:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Es gibt viele Verwendungsmöglichkeiten für „Select-Object“. Eine davon ist das Replizieren von Daten, die Sie anschließend ändern können. Jetzt können wir uns um das Problem kümmern, das uns im vorherigen Abschnitt aufgefallen ist. Wir können den Wert von „FreeSpace“ in unseren neu erstellten Objekten so aktualisieren, dass die Ausgabe eine aussagekräftige Bezeichnung enthält:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

