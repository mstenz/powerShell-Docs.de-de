---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Sortieren von Objekten
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="sorting-objects"></a><span data-ttu-id="82727-103">Sortieren von Objekten</span><span class="sxs-lookup"><span data-stu-id="82727-103">Sorting Objects</span></span>
<span data-ttu-id="82727-104">Damit sich angezeigte Daten einfacher auswerten lassen, können sie mit dem Cmdlet **Sort-Object** geordnet werden.</span><span class="sxs-lookup"><span data-stu-id="82727-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="82727-105">**Sort-Object** erhält den Namen von mindestens einer Eigenschaft, nach der sortiert werden soll, und gibt Daten zurück, die nach den Werten dieser Eigenschaften sortiert sind.</span><span class="sxs-lookup"><span data-stu-id="82727-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="82727-106">Nehmen Sie das Problem des Auflistens von „Win32_SystemDriver“-Instanzen.</span><span class="sxs-lookup"><span data-stu-id="82727-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="82727-107">Wenn Sie nach Staus (**State**) und dann nach **Name** sortieren möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="82727-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="82727-108">Dies ist zwar eine ziemlich lange Anzeige, aber Sie sehen die Elemente mit demselben Status in Gruppen zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="82727-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

<span data-ttu-id="82727-109">Sie können die Objekte auch in umgekehrter Reihenfolge sortieren, indem Sie den **Descending**-Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="82727-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="82727-110">Dadurch wird die Sortierreihenfolge umgekehrt, sodass Namen in umgekehrter alphabetischer Reihenfolge und Zahlen nach absteigender Größe sortiert werden.</span><span class="sxs-lookup"><span data-stu-id="82727-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```
