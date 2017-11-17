---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="1d312-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="1d312-102">New-Guid</span></span>
<span data-ttu-id="1d312-103">Bei Schreiben von Skripts (oder einer DSC-Ressource) benötigen Sie oft einen eindeutigen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="1d312-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="1d312-104">GUIDs funktionieren gut und können durch Aufrufen der .NET Framework-Klasse „Guid“ einfach generiert werden. Doch mit einem Cmdlet können GUIDs auch von Endbenutzern einfacher gefunden werden, die mit der .NET Framework-Klasse noch nicht vertraut sind:</span><span class="sxs-lookup"><span data-stu-id="1d312-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="1d312-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="1d312-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="1d312-106">Guid</span><span class="sxs-lookup"><span data-stu-id="1d312-106">Guid</span></span>

----

<span data-ttu-id="1d312-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="1d312-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

