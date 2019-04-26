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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068282"
---
# <a name="displaying-error-information"></a><span data-ttu-id="bab10-102">Anzeigen von Fehlerinformationen</span><span class="sxs-lookup"><span data-stu-id="bab10-102">Displaying Error Information</span></span>

<span data-ttu-id="bab10-103">Dieses Thema beschreibt die Möglichkeiten, in denen Benutzer Informationen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="bab10-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="bab10-104">Wenn Ihr Cmdlet ein Fehler auftritt, wird die Präsentation der Fehlerinformationen die folgende Fehlerausgabe in der Standardeinstellung entsprechen.</span><span class="sxs-lookup"><span data-stu-id="bab10-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="bab10-105">Benutzer können jedoch anzeigen Fehler nach Kategorie durch Festlegen der `$ErrorView` Variable `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="bab10-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="bab10-106">Kategorieansicht werden spezifische Informationen über die Error-Datensatzes und nicht über eine Freitext-Beschreibung des Fehlers.</span><span class="sxs-lookup"><span data-stu-id="bab10-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="bab10-107">In dieser Ansicht kann nützlich sein, wenn man eine lange Liste von Fehlern zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="bab10-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="bab10-108">In der Kategorieansicht wird die vorherigen Fehlermeldung wie folgt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bab10-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="bab10-109">Weitere Informationen zu den Fehlerkategorien finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="bab10-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bab10-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bab10-110">See Also</span></span>

[<span data-ttu-id="bab10-111">Windows PowerShell-Error-Datensätze</span><span class="sxs-lookup"><span data-stu-id="bab10-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="bab10-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bab10-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
