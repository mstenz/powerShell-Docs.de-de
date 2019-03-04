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
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853046"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="7005e-102">Erstellen eines Workflows mit einem Windows PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="7005e-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="7005e-103">Sie können einen Workflow erstellen, indem Sie ein Windows PowerShell-Skript zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="7005e-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="7005e-104">Um einen Workflow zu erstellen, verwenden Sie das Workflow-Schlüsselwort, gefolgt von einem Namen für den Workflow vor dem Hauptteil des Skripts.</span><span class="sxs-lookup"><span data-stu-id="7005e-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="7005e-105">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7005e-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="7005e-106">Finden Sie den Workflow, in der gleichen genauso wie jeden anderen Windows PowerShell-Befehl.</span><span class="sxs-lookup"><span data-stu-id="7005e-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="7005e-107">Implementieren parallele und Sequence</span><span class="sxs-lookup"><span data-stu-id="7005e-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="7005e-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) unterstützt die parallele Ausführung von Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="7005e-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="7005e-109">Um diese Funktion in einem Windows PowerShell-Skript zu implementieren, verwenden die `parallel` Schlüsselwort vor einen Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="7005e-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="7005e-110">Sie können auch die `foreach -parallel` Konstruktion, um eine Auflistung von Objekten, die parallel durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="7005e-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="7005e-111">Um eine Gruppe von Aktivitäten in sequenzieller Reihenfolge in einem parallelen Block auszuführen, schließen Sie diese Gruppe von Aktivitäten in einem Skriptblock aus, und stellen Sie den Block mit dem Tasksequenz-Schlüsselwort voran.</span><span class="sxs-lookup"><span data-stu-id="7005e-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="7005e-112">Einbinden von Computern in einer Domäne</span><span class="sxs-lookup"><span data-stu-id="7005e-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="7005e-113">Das folgende Skript erstellt einen Workflow, die sie mit einer Domäne verknüpft werden, wenn sie nicht bereits verknüpft sind, und klicken Sie dann erneut den Status überprüft überprüft den Domänenstatus einer Gruppe von Benutzer angegebenen Computer an.</span><span class="sxs-lookup"><span data-stu-id="7005e-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="7005e-114">Dies ist eine Skriptversion des XAML-Workflows, die in erläutert [Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="7005e-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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