---
title: Windows PowerShell02 Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367299"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="8daad-102">Windows PowerShell02-Beispiel</span><span class="sxs-lookup"><span data-stu-id="8daad-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="8daad-103">In diesem Beispiel wird gezeigt, wie Befehle asynchron mit den Runspaces eines Runspace-Pools ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8daad-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="8daad-104">Das Beispiel generiert eine Liste mit Befehlen und führt diese Befehle aus, während die Windows PowerShell-Engine einen Runspace aus dem Pool öffnet, wenn Sie benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="8daad-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="8daad-105">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8daad-105">Requirements</span></span>

- <span data-ttu-id="8daad-106">Dieses Beispiel erfordert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="8daad-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8daad-107">Deutlich</span><span class="sxs-lookup"><span data-stu-id="8daad-107">Demonstrates</span></span>

<span data-ttu-id="8daad-108">In diesem Beispiel wird Folgendes veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="8daad-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="8daad-109">Das Erstellen eines runspacepool-Objekts mit einer minimalen und maximalen Anzahl von Runspaces, die gleichzeitig geöffnet sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="8daad-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="8daad-110">Erstellen einer Liste von Befehlen.</span><span class="sxs-lookup"><span data-stu-id="8daad-110">Creating a list of commands.</span></span>

- <span data-ttu-id="8daad-111">Asynchrones Ausführen der Befehle.</span><span class="sxs-lookup"><span data-stu-id="8daad-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="8daad-112">Aufrufen der [System. Management. Automation. Runspaces. runspacepool. getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) -Methode, um zu sehen, wie viele Runspaces kostenlos sind.</span><span class="sxs-lookup"><span data-stu-id="8daad-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="8daad-113">Erfassen der Befehlsausgabe mit der [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) -Methode.</span><span class="sxs-lookup"><span data-stu-id="8daad-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="8daad-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8daad-114">Example</span></span>

<span data-ttu-id="8daad-115">Dieses Beispiel zeigt, wie Sie die Runspaces eines Runspace-Pools öffnen und Befehle in diesen Runspaces asynchron ausführen.</span><span class="sxs-lookup"><span data-stu-id="8daad-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="8daad-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8daad-116">See Also</span></span>

[<span data-ttu-id="8daad-117">Schreiben einer Windows PowerShell-Host Anwendung</span><span class="sxs-lookup"><span data-stu-id="8daad-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
