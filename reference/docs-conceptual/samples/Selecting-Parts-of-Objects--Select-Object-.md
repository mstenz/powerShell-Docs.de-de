---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Auswählen von Objektteilen – Select-Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737167"
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="30e2a-103">Auswählen von Objektteilen (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="30e2a-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="30e2a-104">Sie können das Cmdlet `Select-Object` verwenden, um neue, angepasste Windows PowerShell-Objekte zu erstellen, die ausgewählte Eigenschaften der zum Erstellen verwendeten Objekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="30e2a-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="30e2a-105">Geben Sie den folgenden Befehl ein, um ein neues Objekt zu erstellen, das nur die Eigenschaften **Name** und **FreeSpace** der WMI-Klasse **Win32_LogicalDisk** enthält:</span><span class="sxs-lookup"><span data-stu-id="30e2a-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="30e2a-106">Mit `Select-Object` können Sie berechnete Eigenschaften erstellen.</span><span class="sxs-lookup"><span data-stu-id="30e2a-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="30e2a-107">Beispielsweise können Sie **FreeSpace** in Gigabyte statt in Byte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="30e2a-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
