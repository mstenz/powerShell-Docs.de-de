---
title: RunSpace09-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 122a40dea93d874a7c131774e3d1abb148bcd4fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360129"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="29b90-102">RunSpace09-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="29b90-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="29b90-103">Im folgenden finden Sie den Quellcode für das Runspace09-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, die eine Pipeline asynchron](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)aufruft.</span><span class="sxs-lookup"><span data-stu-id="29b90-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="29b90-104">Diese Beispielanwendung erstellt und öffnet einen Runspace, erstellt eine Pipeline und ruft Sie asynchron auf und verwendet dann Pipeline Ereignisse, um das Skript asynchron zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="29b90-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="29b90-105">Das Skript, das von dieser Anwendung ausgeführt wird, erstellt die ganzen Zahlen 1 bis 10 in Intervallen von 0,5 Sekunden (500 ms).</span><span class="sxs-lookup"><span data-stu-id="29b90-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="29b90-106">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="29b90-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="29b90-107">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="29b90-107">See Also</span></span>

[<span data-ttu-id="29b90-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="29b90-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
