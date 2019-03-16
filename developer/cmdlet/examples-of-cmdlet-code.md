---
title: Beispiele für die Cmdlet-Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056259"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="30dc8-102">Cmdlet-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="30dc8-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="30dc8-103">Dieser Abschnitt enthält Beispiele für Cmdlet-Code, die Sie verwenden können, starten Sie eigene Cmdlets schreiben.</span><span class="sxs-lookup"><span data-stu-id="30dc8-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30dc8-104">Schrittweise Anweisungen zum Schreiben von Cmdlets, finden Sie unter [Lernprogramme für das Schreiben von Cmdlets](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="30dc8-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="30dc8-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="30dc8-105">In This Section</span></span>

<span data-ttu-id="30dc8-106">[Wie Sie ein einfaches Cmdlet schreiben](./how-to-write-a-simple-cmdlet.md) dieses Beispiel zeigt die grundlegende Struktur der Cmdlet-Code.</span><span class="sxs-lookup"><span data-stu-id="30dc8-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="30dc8-107">[Wie Sie die Cmdlet-Parameter deklarieren](./how-to-declare-cmdlet-parameters.md) dieses Beispiel zeigt, wie Sie die verschiedenen Typen von Parametern deklarieren.</span><span class="sxs-lookup"><span data-stu-id="30dc8-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="30dc8-108">[Gewusst wie: Deklarieren Parametersätze](./how-to-declare-parameter-sets.md) dieses Beispiel zeigt, wie Sie Sätze von Parametern deklarieren, die die Aktion ändern können, ein Cmdlet führt.</span><span class="sxs-lookup"><span data-stu-id="30dc8-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="30dc8-109">[Wie Sie Parameter-Eingabe überprüfen](./how-to-validate-parameter-input.md) diese Beispiele zeigen, wie zum Überprüfen der Parametereingabe.</span><span class="sxs-lookup"><span data-stu-id="30dc8-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="30dc8-110">[Wie Sie dynamische Parameter deklarieren](./how-to-declare-dynamic-parameters.md) dieses Beispiel zeigt, wie Sie einen Parameter zu deklarieren, die zur Laufzeit hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="30dc8-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="30dc8-111">[Wie Sie Skripts in ein Cmdlet Invoke](./how-to-invoke-scripts-within-a-cmdlet.md) dieses Beispiel zeigt, wie Sie ein Skript aufrufen, die an ein Cmdlet bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="30dc8-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="30dc8-112">[Gewusst wie: Überschreiben von Methoden zum Verarbeiten von Eingabe](./how-to-override-input-processing-methods.md) diese Beispiele zeigen die grundlegende Struktur verwendet, um die BeginProcessing ProcessRecord und EndProcessing-Methoden überschreiben.</span><span class="sxs-lookup"><span data-stu-id="30dc8-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="30dc8-113">[Wie Sie Support ShouldProcess-Aufrufe](./how-to-request-confirmations.md) dieses Beispiel zeigt, wie die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden sollten in einem Cmdlet aus aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="30dc8-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="30dc8-114">[Wie unterstützen Transaktionen](./how-to-support-transactions.md) dieses Beispiel zeigt, wie um anzugeben, dass das Cmdlet-Transaktionen unterstützt und wie Sie die Aktion zu implementieren, die ausgeführt wird, wenn das Cmdlet in einer Transaktion verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="30dc8-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="30dc8-115">[Wie Sie Aufträge unterstützen](./how-to-support-jobs.md) dieses Beispiel zeigt, wie Sie Aufträge zu unterstützen, wenn Sie die Cmdlets schreiben.</span><span class="sxs-lookup"><span data-stu-id="30dc8-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="30dc8-116">[Wie Sie ein Cmdlet aus innerhalb eines Cmdlet Aufrufen](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) dieses Beispiel zeigt, wie Sie ein Cmdlet in ein anderes Cmdlet aufrufen, können Sie die Funktionalität des aufgerufenen-Cmdlets zum Cmdlet hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="30dc8-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="30dc8-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="30dc8-117">See Also</span></span>

[<span data-ttu-id="30dc8-118">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="30dc8-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
