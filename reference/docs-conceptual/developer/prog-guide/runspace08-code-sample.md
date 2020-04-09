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
ms.openlocfilehash: 21d7c4fe69e5026089676c43ad69a4263732cc34
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978252"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="824e9-102">RunSpace08-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="824e9-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="824e9-103">Im folgenden finden Sie den Quellcode für das Runspace08-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, mit der einem Befehl Parameter hinzugefügt](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)werden.</span><span class="sxs-lookup"><span data-stu-id="824e9-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="824e9-104">In dieser Beispielanwendung wird ein Runspace erstellt, eine Pipeline erstellt, zwei Befehle zur Pipeline hinzugefügt, dem zweiten Befehl werden zwei Parameter hinzugefügt, und anschließend wird die Pipeline ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="824e9-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="824e9-105">Die Befehle, die der Pipeline hinzugefügt werden, sind die `Get-Process`-und `Sort-Object`-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="824e9-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="824e9-106">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="824e9-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="824e9-107">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="824e9-107">See Also</span></span>

[<span data-ttu-id="824e9-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="824e9-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
