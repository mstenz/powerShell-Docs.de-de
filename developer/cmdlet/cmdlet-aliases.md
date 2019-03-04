---
title: Cmdlet-Aliase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860506"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="c56dd-102">Cmdlet-Aliase</span><span class="sxs-lookup"><span data-stu-id="c56dd-102">Cmdlet Aliases</span></span>

<span data-ttu-id="c56dd-103">Sie können Cmdlet-Aliase verwenden, um die Cmdlet-benutzerfreundlichkeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="c56dd-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="c56dd-104">Sie können Aliase für häufig verwendete-Cmdlets, Eingabe zu verringern und Abschließen von Aufgaben schnell erleichtern hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c56dd-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="c56dd-105">Sie können die integrierten Aliase in Ihre Cmdlets einschließen, oder Benutzer können ihre eigenen benutzerdefinierten Aliasen definieren.</span><span class="sxs-lookup"><span data-stu-id="c56dd-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="c56dd-106">Z. B. die [Get-Command](/powershell/module/microsoft.powershell.core/get-command) Cmdlet verfügt über eine integrierte `gcm` Alias.</span><span class="sxs-lookup"><span data-stu-id="c56dd-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="c56dd-107">Aliase können auch die Befehlsnamen aus anderen Sprachen hinzufügen, sodass Benutzer keine neuen Befehle zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="c56dd-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="c56dd-108">Alias-Richtlinien</span><span class="sxs-lookup"><span data-stu-id="c56dd-108">Alias Guidelines</span></span>

<span data-ttu-id="c56dd-109">Beachten Sie Folgendes, wenn Sie die integrierten Aliase für Ihre Cmdlets erstellen:</span><span class="sxs-lookup"><span data-stu-id="c56dd-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="c56dd-110">Bevor Sie den Aliasnamen zuweisen, starten Sie Windows PowerShell, und führen Sie die [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) Cmdlet, um die Aliase anzuzeigen, die bereits verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c56dd-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="c56dd-111">Enthalten Sie ein Alias-Präfix, das verweist auf das Verb den Cmdlet-Namen und ein Alias-Suffix, die das Nomen der Cmdlet-Namen verweist.</span><span class="sxs-lookup"><span data-stu-id="c56dd-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="c56dd-112">Z. B. der Alias für die `Import-Module` ist "Ipmo"-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c56dd-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="c56dd-113">Eine Liste der alle Verben und ihre Aliase, finden Sie unter [Cmdlet-Verbs](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c56dd-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="c56dd-114">Cmdlets, die das gleiche Verb haben, enthalten Sie das gleiche Präfix für den Alias.</span><span class="sxs-lookup"><span data-stu-id="c56dd-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="c56dd-115">Beispielsweise verwenden die Aliase für alle Windows PowerShell-Cmdlets, die das Verb "Get" in deren Namen das Präfix "g".</span><span class="sxs-lookup"><span data-stu-id="c56dd-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="c56dd-116">Cmdlets, die dem gleichen Namen haben, enthalten Sie das gleiche Alias-Suffix.</span><span class="sxs-lookup"><span data-stu-id="c56dd-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="c56dd-117">Beispielsweise verwenden die Aliase für alle Windows PowerShell-Cmdlets, die das Nomen "Session", deren Name das Suffix "sn".</span><span class="sxs-lookup"><span data-stu-id="c56dd-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="c56dd-118">Verwenden Sie für Cmdlets, die von den Befehlen in anderen Sprachen entsprechen den Namen des Befehls.</span><span class="sxs-lookup"><span data-stu-id="c56dd-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="c56dd-119">Im Allgemeinen stellen Sie Aliase so kurz wie möglich.</span><span class="sxs-lookup"><span data-stu-id="c56dd-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="c56dd-120">Stellen Sie sicher, dass der Alias mindestens ein eigenständiges Zeichen für das Verb und ein eigenständiges Zeichen für die das Nomen verfügt.</span><span class="sxs-lookup"><span data-stu-id="c56dd-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="c56dd-121">Fügen Sie mehr Zeichen, die nach Bedarf, um den alias eindeutig zu machen.</span><span class="sxs-lookup"><span data-stu-id="c56dd-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="c56dd-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c56dd-122">See Also</span></span>

[<span data-ttu-id="c56dd-123">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c56dd-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
