---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Auswählen von Objektteilen – Select-Object
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030105"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="0fc69-103">Auswählen von Objektteilen (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="0fc69-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="0fc69-104">Sie können das Cmdlet **Select-Object** verwenden, um neue, angepasste Windows PowerShell-Objekte zu erstellen, die ausgewählte Eigenschaften der zum Erstellen verwendeten Objekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="0fc69-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="0fc69-105">Geben Sie den folgenden Befehl ein, um ein neues Objekt zu erstellen, das nur die Eigenschaften „Name“ und „FreeSpace“ der WMI-Klasse „Win32_LogicalDisk“ enthält:</span><span class="sxs-lookup"><span data-stu-id="0fc69-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="0fc69-106">Nach der Ausgabe des Befehls wird der Datentyp nicht angezeigt, aber wenn Sie das Ergebnis nach „Select-Object“ an „Get-Member“ weiterleiten, erkennen Sie, dass Sie über den neuen Objekttyp „PSCustomObject“ verfügen:</span><span class="sxs-lookup"><span data-stu-id="0fc69-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

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

<span data-ttu-id="0fc69-107">Es gibt viele Verwendungsmöglichkeiten für „Select-Object“.</span><span class="sxs-lookup"><span data-stu-id="0fc69-107">Select-Object has many uses.</span></span> <span data-ttu-id="0fc69-108">Eine davon ist das Replizieren von Daten, die Sie anschließend ändern können.</span><span class="sxs-lookup"><span data-stu-id="0fc69-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="0fc69-109">Jetzt können wir uns um das Problem kümmern, das uns im vorherigen Abschnitt aufgefallen ist.</span><span class="sxs-lookup"><span data-stu-id="0fc69-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="0fc69-110">Wir können den Wert von „FreeSpace“ in unseren neu erstellten Objekten so aktualisieren, dass die Ausgabe eine aussagekräftige Bezeichnung enthält:</span><span class="sxs-lookup"><span data-stu-id="0fc69-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
