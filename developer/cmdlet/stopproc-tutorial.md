---
title: StopProc Tutorial | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794398"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="74ada-102">StopProc-Tutorial</span><span class="sxs-lookup"><span data-stu-id="74ada-102">StopProc Tutorial</span></span>

<span data-ttu-id="74ada-103">Dieser Abschnitt enthält ein Tutorial zum Erstellen der Stop-Proc-Cmdlet, das ähnelt der [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) Cmdlet von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74ada-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="74ada-104">Dieses Tutorial bietet Codefragmente, die veranschaulichen, wie die Cmdlets implementiert werden, sowie eine Erläuterung des Codes.</span><span class="sxs-lookup"><span data-stu-id="74ada-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="74ada-105">Die Themen in diesem Tutorial</span><span class="sxs-lookup"><span data-stu-id="74ada-105">Topics in this Tutorial</span></span>

<span data-ttu-id="74ada-106">Die Themen in diesem Tutorial dienen, die sequenziell gelesen werden, mit jedem Thema erstellen auf die in vorherigen Thema behandelt wurde.</span><span class="sxs-lookup"><span data-stu-id="74ada-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="74ada-107">[Erstellen ein Cmdlet, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md) in diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet zu erstellen, die System-Änderungen, wie z. B. das Beenden eines Prozesses auf dem Computer unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ada-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="74ada-108">[Hinzufügen von Benutzernachrichten an Ihr Cmdlet](./adding-user-messages-to-your-cmdlet.md) in diesem Abschnitt wird beschrieben, wie die Fähigkeit zum Schreiben von benutzermeldungen, Debugmeldungen, Warnungen und Statusinformationen in Ihrem Cmdlet hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ada-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="74ada-109">[Hinzufügen von Platzhaltererweiterung, Aliase und Cmdlet-Parameter sollte](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) in diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet zu erstellen, parameteraliase, Hilfe und platzhaltererweiterung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ada-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="74ada-110">[Für Cmdlets hinzufügen Parametersätze](./adding-parameter-sets-to-a-cmdlet.md) in diesem Abschnitt beschreibt das Hinzufügen der Parameter legt fest, an ein Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="74ada-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="74ada-111">Parametersätze ermöglichen das-Cmdlet funktioniert Weise basierend auf Parameter vom Benutzer angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="74ada-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="74ada-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="74ada-112">See Also</span></span>

[<span data-ttu-id="74ada-113">Erstellen ein Cmdlet, ändert das System</span><span class="sxs-lookup"><span data-stu-id="74ada-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="74ada-114">Ihr Cmdlet Benutzermeldungen hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="74ada-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="74ada-115">Hinzufügen von Platzhaltererweiterung, Aliase und Hilfe zum Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="74ada-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="74ada-116">Für Cmdlets legt Parameter hinzufügen</span><span class="sxs-lookup"><span data-stu-id="74ada-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="74ada-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="74ada-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
