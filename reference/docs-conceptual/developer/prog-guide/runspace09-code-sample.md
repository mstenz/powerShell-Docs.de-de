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
ms.openlocfilehash: d7fa39485eea833483682c91c96417a76e5d770f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977538"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="ad17b-102">RunSpace09-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ad17b-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="ad17b-103">Im folgenden finden Sie den Quellcode für das Runspace09-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, die eine Pipeline asynchron](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)aufruft.</span><span class="sxs-lookup"><span data-stu-id="ad17b-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="ad17b-104">Diese Beispielanwendung erstellt und öffnet einen Runspace, erstellt eine Pipeline und ruft Sie asynchron auf und verwendet dann Pipeline Ereignisse, um das Skript asynchron zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="ad17b-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="ad17b-105">Das Skript, das von dieser Anwendung ausgeführt wird, erstellt die ganzen Zahlen 1 bis 10 in Intervallen von 0,5 Sekunden (500 ms).</span><span class="sxs-lookup"><span data-stu-id="ad17b-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="ad17b-106">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ad17b-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="ad17b-107">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ad17b-107">See Also</span></span>

[<span data-ttu-id="ad17b-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ad17b-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
