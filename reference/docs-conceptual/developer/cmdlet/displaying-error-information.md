---
title: Anzeigen von Fehlerinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369969"
---
# <a name="displaying-error-information"></a><span data-ttu-id="bf9f2-102">Anzeigen von Fehlerinformationen</span><span class="sxs-lookup"><span data-stu-id="bf9f2-102">Displaying Error Information</span></span>

<span data-ttu-id="bf9f2-103">In diesem Thema wird erläutert, wie Benutzerfehler Informationen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="bf9f2-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="bf9f2-104">Wenn das Cmdlet auf einen Fehler stößt, wird die Darstellung der Fehlerinformationen standardmäßig der folgenden Fehlerausgabe ähneln.</span><span class="sxs-lookup"><span data-stu-id="bf9f2-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="bf9f2-105">Allerdings können Benutzerfehler nach Kategorie anzeigen, indem Sie die Variable `$ErrorView` auf `"CategoryView"` festlegen.</span><span class="sxs-lookup"><span data-stu-id="bf9f2-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="bf9f2-106">In der Kategorieansicht werden bestimmte Informationen aus dem Fehler Daten Satz und nicht eine frei Textbeschreibung des Fehlers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bf9f2-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="bf9f2-107">Diese Ansicht kann nützlich sein, wenn Sie über eine lange Liste der zu überprüfenden Fehler verfügen.</span><span class="sxs-lookup"><span data-stu-id="bf9f2-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="bf9f2-108">In der Kategorieansicht wird die vorherige Fehlermeldung wie folgt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bf9f2-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="bf9f2-109">Weitere Informationen zu Fehlerkategorien finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="bf9f2-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf9f2-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bf9f2-110">See Also</span></span>

[<span data-ttu-id="bf9f2-111">Windows PowerShell-Fehler Datensätze</span><span class="sxs-lookup"><span data-stu-id="bf9f2-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="bf9f2-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf9f2-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
