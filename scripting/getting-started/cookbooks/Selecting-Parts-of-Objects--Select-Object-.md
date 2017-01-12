---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Auswählen von Objektteilen – Select-Object"
ms.technology: powershell
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 5e0ca5110d7e35e49da3db779d9d495ea6b78e67
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
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

