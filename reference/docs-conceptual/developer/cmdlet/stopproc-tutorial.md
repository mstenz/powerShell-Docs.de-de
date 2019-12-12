---
title: Stop proc-Tutorial | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369409"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="39979-102">StopProc-Tutorial</span><span class="sxs-lookup"><span data-stu-id="39979-102">StopProc Tutorial</span></span>

<span data-ttu-id="39979-103">Dieser Abschnitt enthält ein Tutorial zum Erstellen des Cmdlets "Break-proc", das dem von Windows PowerShell bereitgestellten Cmdlet " [Process-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) " sehr ähnlich ist.</span><span class="sxs-lookup"><span data-stu-id="39979-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="39979-104">Dieses Tutorial enthält Code Fragmente, die veranschaulichen, wie Cmdlets implementiert werden, und eine Erläuterung des Codes.</span><span class="sxs-lookup"><span data-stu-id="39979-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="39979-105">Themen in diesem Tutorial</span><span class="sxs-lookup"><span data-stu-id="39979-105">Topics in this Tutorial</span></span>

<span data-ttu-id="39979-106">Die Themen in diesem Lernprogramm sind so konzipiert, dass Sie sequenziell gelesen werden, wobei jedes Thema auf den im vorherigen Thema behandelten Themen aufbaut.</span><span class="sxs-lookup"><span data-stu-id="39979-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="39979-107">[Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md) In diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet erstellen, das Systemänderungen unterstützt, z. b. das Beenden eines auf dem Computer ausgeführtes Verfahren</span><span class="sxs-lookup"><span data-stu-id="39979-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="39979-108">[Hinzufügen von Benutzer Nachrichten zum Cmdlet](./adding-user-messages-to-your-cmdlet.md) In diesem Abschnitt wird beschrieben, wie Sie die Möglichkeit zum Schreiben von Benutzer Nachrichten, Debugmeldungen, Warnmeldungen und Statusinformationen in das Cmdlet hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="39979-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="39979-109">[Hinzufügen von Aliasen, Platzhalter Erweiterungen und Hilfe zu Cmdlet-Parametern](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) In diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet erstellen, das Parameter Aliase, Hilfe und Platzhalter Erweiterungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39979-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="39979-110">[Hinzufügen von Parameter Sätzen zu Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) In diesem Abschnitt wird beschrieben, wie Parametersätze einem Cmdlet hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="39979-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="39979-111">Mithilfe von Parametersätzen kann das Cmdlet basierend auf den Parametern, die vom Benutzer angegeben werden, unterschiedlich funktionieren.</span><span class="sxs-lookup"><span data-stu-id="39979-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="39979-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="39979-112">See Also</span></span>

[<span data-ttu-id="39979-113">Erstellen eines Cmdlets, das das System ändert</span><span class="sxs-lookup"><span data-stu-id="39979-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="39979-114">Hinzufügen von Benutzer Nachrichten zum Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39979-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="39979-115">Hinzufügen von Aliasen, Platzhalter Erweiterungen und Hilfe zu Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="39979-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="39979-116">Hinzufügen von Parameter Sätzen zu Cmdlets</span><span class="sxs-lookup"><span data-stu-id="39979-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="39979-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="39979-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
