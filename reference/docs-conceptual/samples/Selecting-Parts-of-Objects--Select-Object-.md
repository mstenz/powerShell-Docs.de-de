---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Auswählen von Objektteilen – Select-Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737167"
---
# <a name="selecting-parts-of-objects-select-object"></a>Auswählen von Objektteilen (Select-Object)

Sie können das Cmdlet `Select-Object` verwenden, um neue, angepasste Windows PowerShell-Objekte zu erstellen, die ausgewählte Eigenschaften der zum Erstellen verwendeten Objekte enthalten. Geben Sie den folgenden Befehl ein, um ein neues Objekt zu erstellen, das nur die Eigenschaften **Name** und **FreeSpace** der WMI-Klasse **Win32_LogicalDisk** enthält:

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

Mit `Select-Object` können Sie berechnete Eigenschaften erstellen. Beispielsweise können Sie **FreeSpace** in Gigabyte statt in Byte anzeigen.

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
