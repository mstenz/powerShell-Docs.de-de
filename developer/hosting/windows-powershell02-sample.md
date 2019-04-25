---
title: Beispiel für Windows-PowerShell02 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082514"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="fcd67-102">Windows PowerShell02-Beispiel</span><span class="sxs-lookup"><span data-stu-id="fcd67-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="fcd67-103">Dieses Beispiel zeigt, wie Befehle asynchron ausgeführt wird, wird der Runspaces, der einen runspacepool verwenden.</span><span class="sxs-lookup"><span data-stu-id="fcd67-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="fcd67-104">Im Beispiel generiert eine Liste der Befehle, und klicken Sie dann diese Befehle ausgeführt werden, während des Windows PowerShell-Moduls aus dem Pool einen Runspace öffnet, wenn er benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="fcd67-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcd67-105">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="fcd67-105">Requirements</span></span>

- <span data-ttu-id="fcd67-106">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fcd67-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fcd67-107">Zeigt</span><span class="sxs-lookup"><span data-stu-id="fcd67-107">Demonstrates</span></span>

<span data-ttu-id="fcd67-108">Dieses Beispiel zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="fcd67-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="fcd67-109">Erstellen einen RunspacePool-Objekt, mit einer minimalen und maximalen Anzahl von Runspaces, die zur gleichen Zeit geöffnet sein dürfen.</span><span class="sxs-lookup"><span data-stu-id="fcd67-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="fcd67-110">Erstellen eine Liste der Befehle.</span><span class="sxs-lookup"><span data-stu-id="fcd67-110">Creating a list of commands.</span></span>

- <span data-ttu-id="fcd67-111">Die Befehle ausführen asynchron.</span><span class="sxs-lookup"><span data-stu-id="fcd67-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="fcd67-112">Aufrufen der [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) Methode, um festzustellen, wie viele Runspaces kostenlos sind.</span><span class="sxs-lookup"><span data-stu-id="fcd67-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="fcd67-113">Erfassen die Ausgabe des Befehls mit der [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) Methode.</span><span class="sxs-lookup"><span data-stu-id="fcd67-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="fcd67-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fcd67-114">Example</span></span>

<span data-ttu-id="fcd67-115">Dieses Beispiel zeigt, wie der Runspaces, der einen runspacepool geöffnet und asynchron ausführen von Befehlen in diese Runspaces.</span><span class="sxs-lookup"><span data-stu-id="fcd67-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="fcd67-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fcd67-116">See Also</span></span>

[<span data-ttu-id="fcd67-117">Schreiben Sie eine Windows PowerShell-Hostanwendung</span><span class="sxs-lookup"><span data-stu-id="fcd67-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)