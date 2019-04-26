---
title: GetProc02 (C#)-Codebeispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 2ac4aea2fdefdfe86349c14fe9b87cd8c41db090
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081704"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="1cdc5-102">GetProc02-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="1cdc5-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="1cdc5-103">Der folgende Code zeigt die Implementierung einer `Get-Process` -Cmdlet, das Befehlszeilen-Eingaben akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="1cdc5-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="1cdc5-104">Beachten Sie, die diese Implementierung definiert eine `Name` verwendet Parameter, um die Befehlszeile, und sie können die [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) Methode als Ausgabe Mechanismus zum Senden der Ausgabe Objekte in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="1cdc5-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1cdc5-105">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1cdc5-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="1cdc5-106">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1cdc5-106">See Also</span></span>

[<span data-ttu-id="1cdc5-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1cdc5-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)