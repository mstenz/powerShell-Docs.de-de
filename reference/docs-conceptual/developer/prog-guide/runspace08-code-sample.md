---
title: RunSpace08-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 2e9cd80f1869e0d859187eea89eca414a84cb4ab
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870580"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="2fc14-102">RunSpace08-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="2fc14-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="2fc14-103">Im folgenden finden Sie den Quellcode für das Runspace08-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, mit der einem Befehl Parameter hinzugefügt](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)werden.</span><span class="sxs-lookup"><span data-stu-id="2fc14-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="2fc14-104">In dieser Beispielanwendung wird ein Runspace erstellt, eine Pipeline erstellt, zwei Befehle zur Pipeline hinzugefügt, dem zweiten Befehl werden zwei Parameter hinzugefügt, und anschließend wird die Pipeline ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="2fc14-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="2fc14-105">Die Befehle, die der Pipeline hinzugefügt werden, sind die `Get-Process`-und `Sort-Object`-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2fc14-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2fc14-106">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="2fc14-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="2fc14-107">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2fc14-107">See Also</span></span>

[<span data-ttu-id="2fc14-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2fc14-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
