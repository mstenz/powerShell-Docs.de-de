---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678137"
---
# <a name="new-guid"></a><span data-ttu-id="e73d7-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="e73d7-102">New-Guid</span></span>
<span data-ttu-id="e73d7-103">Bei Schreiben von Skripts (oder einer DSC-Ressource) benötigen Sie oft einen eindeutigen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="e73d7-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="e73d7-104">GUIDs funktionieren gut und können durch Aufrufen der .NET Framework-Klasse „Guid“ einfach generiert werden. Doch mit einem Cmdlet können GUIDs auch von Endbenutzern einfacher gefunden werden, die mit der .NET Framework-Klasse noch nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="e73d7-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="e73d7-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="e73d7-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="e73d7-106">Guid</span><span class="sxs-lookup"><span data-stu-id="e73d7-106">Guid</span></span>

----

<span data-ttu-id="e73d7-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="e73d7-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
