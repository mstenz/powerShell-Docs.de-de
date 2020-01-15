---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Wiederholen einer Aufgabe für mehrere Objekte
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736878"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="6e769-103">Wiederholen einer Aufgabe für mehrere Objekte (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="6e769-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="6e769-104">Das Cmdlet `ForEach-Object` verwendet Skriptblöcke und den Deskriptor `$_` für das aktuelle Pipelineobjekt, um Ihnen das Ausführen eines Befehls für jedes Objekt in der Pipeline zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6e769-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="6e769-105">Damit können Sie einige komplizierte Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="6e769-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="6e769-106">Besonders nützlich kann dies sein, wenn Sie Daten bearbeiten möchten, um sie besser nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="6e769-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="6e769-107">Beispielsweise kann die Klasse **Win32_LogicalDisk** aus WMI verwendet werden, um für jeden lokalen Datenträger Informationen zum freien Speicherplatz zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="6e769-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="6e769-108">Die Daten werden als Bytes zurückgegeben, sind daher schwierig zu lesen:</span><span class="sxs-lookup"><span data-stu-id="6e769-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="6e769-109">Der **FreeSpace**-Wert kann durch Division der einzelnen Werte durch 1 MB in Megabyte konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="6e769-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="6e769-110">Sie können dazu einen `ForEach-Object`-Skriptblock verwenden, indem Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="6e769-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="6e769-111">Leider erhalten Sie als Ausgabe nun Daten ohne zugeordnete Bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="6e769-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="6e769-112">Da WMI-Eigenschaften wie diese schreibgeschützt sind, kann **FreeSpace** nicht direkt konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="6e769-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="6e769-113">Wenn Sie Folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="6e769-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="6e769-114">Erhalten Sie eine Fehlermeldung:</span><span class="sxs-lookup"><span data-stu-id="6e769-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="6e769-115">Sie könnten die Daten mithilfe bestimmter erweiterter Techniken neu anordnen, ein einfacherer Ansatz ist jedoch die Erstellung eines neues Objekts mit `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="6e769-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
