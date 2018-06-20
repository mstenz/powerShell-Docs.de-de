---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225588"
---
# <a name="new-guid"></a><span data-ttu-id="e11e9-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="e11e9-102">New-Guid</span></span>
<span data-ttu-id="e11e9-103">Bei Schreiben von Skripts (oder einer DSC-Ressource) benötigen Sie oft einen eindeutigen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="e11e9-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="e11e9-104">GUIDs funktionieren gut und können durch Aufrufen der .NET Framework-Klasse „Guid“ einfach generiert werden. Doch mit einem Cmdlet können GUIDs auch von Endbenutzern einfacher gefunden werden, die mit der .NET Framework-Klasse noch nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="e11e9-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="e11e9-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="e11e9-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="e11e9-106">Guid</span><span class="sxs-lookup"><span data-stu-id="e11e9-106">Guid</span></span>

----

<span data-ttu-id="e11e9-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="e11e9-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
