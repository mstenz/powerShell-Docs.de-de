---
title: Erstellen eines Workflows mithilfe eines Windows PowerShell-Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870845"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="28d38-102">Erstellen eines Workflows mit einem Windows PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="28d38-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="28d38-103">Sie können einen Workflow erstellen, indem Sie ein Windows PowerShell-Skript schreiben.</span><span class="sxs-lookup"><span data-stu-id="28d38-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="28d38-104">Um einen Workflow zu erstellen, verwenden Sie das Workflow Schlüsselwort, gefolgt von einem Namen für den Workflow vor dem Text des Skripts.</span><span class="sxs-lookup"><span data-stu-id="28d38-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="28d38-105">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="28d38-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="28d38-106">Sie finden den Workflow genauso wie jeden anderen Windows PowerShell-Befehl.</span><span class="sxs-lookup"><span data-stu-id="28d38-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="28d38-107">Implementieren von parallel und Sequence</span><span class="sxs-lookup"><span data-stu-id="28d38-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="28d38-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) unterstützt die parallele Ausführung von Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="28d38-108">[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) supports execution of activities in parallel.</span></span> <span data-ttu-id="28d38-109">Um diese Funktion in einem Windows PowerShell-Skript zu implementieren, verwenden Sie das `parallel`-Schlüsselwort vor einem Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="28d38-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="28d38-110">Sie können auch die `foreach -parallel` Erstellung verwenden, um eine Auflistung von-Objekten parallel zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="28d38-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="28d38-111">Um eine Gruppe von Aktivitäten in sequenzieller Reihenfolge innerhalb eines parallelen Blocks auszuführen, schließen Sie diese Gruppe von Aktivitäten in einen Skriptblock ein, und stellen Sie dem Block das Sequence-Schlüsselwort voran.</span><span class="sxs-lookup"><span data-stu-id="28d38-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="28d38-112">Hinzufügen von Computern zu einer Domäne</span><span class="sxs-lookup"><span data-stu-id="28d38-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="28d38-113">Mit dem folgenden Skript wird ein Workflow erstellt, der den Domänen Status einer Gruppe von benutzerdefinierten Computern überprüft, Sie mit einer Domäne verknüpft, wenn Sie noch nicht verknüpft sind, und den Status dann erneut überprüft.</span><span class="sxs-lookup"><span data-stu-id="28d38-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>
<span data-ttu-id="28d38-114">Dies ist eine Skript Version des XAML-Workflows, die unter [Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md)erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="28d38-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```