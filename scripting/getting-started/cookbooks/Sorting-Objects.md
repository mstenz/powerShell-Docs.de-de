---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Sortieren von Objekten
ms.technology: powershell
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 00ee71337331c730f37723152175e2ca10263191
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="sorting-objects"></a>Sortieren von Objekten
Damit sich angezeigte Daten einfacher auswerten lassen, können sie mit dem Cmdlet **Sort-Object** geordnet werden. **Sort-Object** erhält den Namen von mindestens einer Eigenschaft, nach der sortiert werden soll, und gibt Daten zurück, die nach den Werten dieser Eigenschaften sortiert sind.

Nehmen Sie das Problem des Auflistens von „Win32_SystemDriver“-Instanzen. Wenn Sie nach Staus (**State**) und dann nach **Name** sortieren möchten, geben Sie Folgendes ein:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Dies ist zwar eine ziemlich lange Anzeige, aber Sie sehen die Elemente mit demselben Status in Gruppen zusammengefasst:

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

Sie können die Objekte auch in umgekehrter Reihenfolge sortieren, indem Sie den **Descending**-Parameter angeben. Dadurch wird die Sortierreihenfolge umgekehrt, sodass Namen in umgekehrter alphabetischer Reihenfolge und Zahlen nach absteigender Größe sortiert werden.

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

