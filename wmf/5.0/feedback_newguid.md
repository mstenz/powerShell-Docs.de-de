---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="e4628-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="e4628-102">New-Guid</span></span>
<span data-ttu-id="e4628-103">Bei Schreiben von Skripts (oder einer DSC-Ressource) benötigen Sie oft einen eindeutigen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="e4628-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="e4628-104">GUIDs funktionieren gut und können durch Aufrufen der .NET Framework-Klasse „Guid“ einfach generiert werden. Doch mit einem Cmdlet können GUIDs auch von Endbenutzern einfacher gefunden werden, die mit der .NET Framework-Klasse noch nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="e4628-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="e4628-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="e4628-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="e4628-106">Guid</span><span class="sxs-lookup"><span data-stu-id="e4628-106">Guid</span></span>

----

<span data-ttu-id="e4628-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="e4628-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>