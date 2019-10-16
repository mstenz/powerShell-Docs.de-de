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
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366479"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="62e77-102">RunSpace08-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="62e77-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="62e77-103">Im folgenden finden Sie den Quellcode für das Runspace08-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, mit der einem Befehl Parameter hinzugefügt](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)werden.</span><span class="sxs-lookup"><span data-stu-id="62e77-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="62e77-104">In dieser Beispielanwendung wird ein Runspace erstellt, eine Pipeline erstellt, zwei Befehle zur Pipeline hinzugefügt, dem zweiten Befehl werden zwei Parameter hinzugefügt, und anschließend wird die Pipeline ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="62e77-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="62e77-105">Die Befehle, die der Pipeline hinzugefügt werden, sind die `Get-Process`-und `Sort-Object`-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="62e77-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="62e77-106">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="62e77-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="62e77-107">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="62e77-107">See Also</span></span>

[<span data-ttu-id="62e77-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="62e77-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
