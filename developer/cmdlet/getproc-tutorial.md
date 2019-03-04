---
title: GetProc Tutorial | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862456"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="59d47-102">GetProc-Tutorial</span><span class="sxs-lookup"><span data-stu-id="59d47-102">GetProc Tutorial</span></span>

<span data-ttu-id="59d47-103">Dieser Abschnitt enthält ein Tutorial für eine Get-Proc-Cmdlet erstellen, ähnelt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59d47-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="59d47-104">Dieses Tutorial bietet Codefragmente, die veranschaulichen, wie die Cmdlets implementiert werden, sowie eine Erläuterung des Codes.</span><span class="sxs-lookup"><span data-stu-id="59d47-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="59d47-105">Die Themen in diesem Tutorial</span><span class="sxs-lookup"><span data-stu-id="59d47-105">Topics in this Tutorial</span></span>

<span data-ttu-id="59d47-106">Die Themen in diesem Tutorial dienen, die sequenziell gelesen werden, mit jedem Thema erstellen auf die in vorherigen Thema behandelt wurde.</span><span class="sxs-lookup"><span data-stu-id="59d47-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="59d47-107">[Erstellen ein Cmdlet ohne Parameter](./creating-a-cmdlet-without-parameters.md) in diesem Abschnitt wird beschrieben, wie ein Cmdlet zu erstellen, ruft Informationen aus dem lokalen Computer, ohne die Verwendung von Parametern ab, und schreibt dann die Informationen in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="59d47-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="59d47-108">[Hinzufügen von Parametern, die diesem Prozess Command-Line-Eingabe](./adding-parameters-that-process-command-line-input.md) in diesem Abschnitt wird beschrieben, wie das Cmdlet "Get-Proc" einen Parameter hinzugefügt werden, damit das Cmdlet die Eingabe, die auf der Grundlage explizite Objekte, die an das Cmdlet übergeben verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="59d47-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="59d47-109">Die beschriebenen Implementierung hier ruft Prozesse, die basierend auf ihren Namen und schreibt dann die Informationen in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="59d47-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="59d47-110">[Hinzufügen von Parametern, Prozess-Pipelineeingabe](./adding-parameters-that-process-pipeline-input.md) in diesem Abschnitt wird beschrieben, wie das Cmdlet "Get-Proc" einen Parameter hinzugefügt werden, damit das Cmdlet über die Pipeline übergebenen Objekte verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="59d47-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="59d47-111">Beschriebenen Cmdlets für die Implementierung hier ruft werden auf Grundlage von Objekten, die an das Cmdlet übergeben und schreibt dann die Informationen in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="59d47-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="59d47-112">[Ihr Cmdlet hinzugefügt ohne Abbruch Fehlerberichterstattung](./adding-non-terminating-error-reporting-to-your-cmdlet.md) in diesem Abschnitt wird beschrieben, wie ohne Abbruch Fehlerberichte, die an ein Cmdlet hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="59d47-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="59d47-113">Die hier beschriebene Implementierung erkennt Fehler ohne Abbruch, die auftreten, wenn die Eingabe verarbeitet und einen Fehlerdatensatz in den fehlerdatenstrom geschrieben.</span><span class="sxs-lookup"><span data-stu-id="59d47-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="59d47-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="59d47-114">See Also</span></span>

[<span data-ttu-id="59d47-115">Erstellen ein Cmdlet ohne Parameter</span><span class="sxs-lookup"><span data-stu-id="59d47-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="59d47-116">Hinzufügen von Parametern, die Befehlszeileneingabe verarbeiten</span><span class="sxs-lookup"><span data-stu-id="59d47-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="59d47-117">Hinzufügen von Parametern, die Eingabe der Prozesspipeline</span><span class="sxs-lookup"><span data-stu-id="59d47-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="59d47-118">Ohne Abbruch Fehlerberichte, die an Ihr Cmdlet hinzufügen</span><span class="sxs-lookup"><span data-stu-id="59d47-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="59d47-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="59d47-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
