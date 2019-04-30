---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085325"
---
# <a name="new-guid"></a><span data-ttu-id="6ea96-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="6ea96-102">New-Guid</span></span>
<span data-ttu-id="6ea96-103">Bei Schreiben von Skripts (oder einer DSC-Ressource) benötigen Sie oft einen eindeutigen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="6ea96-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="6ea96-104">GUIDs funktionieren gut und können durch Aufrufen der .NET Framework-Klasse „Guid“ einfach generiert werden. Doch mit einem Cmdlet können GUIDs auch von Endbenutzern einfacher gefunden werden, die mit der .NET Framework-Klasse noch nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="6ea96-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="6ea96-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="6ea96-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="6ea96-106">Guid</span><span class="sxs-lookup"><span data-stu-id="6ea96-106">Guid</span></span>

----

<span data-ttu-id="6ea96-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="6ea96-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
