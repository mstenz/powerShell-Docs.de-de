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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369979"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="479cc-102">Cmdlet-Aliase</span><span class="sxs-lookup"><span data-stu-id="479cc-102">Cmdlet Aliases</span></span>

<span data-ttu-id="479cc-103">Sie können Cmdlet-Aliase verwenden, um die Benutzer Darstellung des Cmdlets zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="479cc-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="479cc-104">Sie können-Aliase zu häufig verwendeten Cmdlets hinzufügen, um die Eingabe zu reduzieren und Aufgaben schneller auszuführen.</span><span class="sxs-lookup"><span data-stu-id="479cc-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="479cc-105">Sie können integrierte Aliase in ihre Cmdlets einschließen, oder Benutzer können Ihre eigenen benutzerdefinierten Aliase definieren.</span><span class="sxs-lookup"><span data-stu-id="479cc-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="479cc-106">Beispielsweise verfügt das [Get-Command](/powershell/module/microsoft.powershell.core/get-command) -Cmdlet über einen integrierten `gcm`-Alias.</span><span class="sxs-lookup"><span data-stu-id="479cc-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="479cc-107">Sie können Aliase auch zum Hinzufügen von Befehlsnamen aus anderen Sprachen verwenden, sodass Benutzer keine neuen Befehle erlernen müssen.</span><span class="sxs-lookup"><span data-stu-id="479cc-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="479cc-108">Alias Richtlinien</span><span class="sxs-lookup"><span data-stu-id="479cc-108">Alias Guidelines</span></span>

<span data-ttu-id="479cc-109">Befolgen Sie diese Richtlinien, wenn Sie integrierte Aliase für die Cmdlets erstellen:</span><span class="sxs-lookup"><span data-stu-id="479cc-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="479cc-110">Bevor Sie Aliase zuweisen, starten Sie Windows PowerShell, und führen Sie dann das [Get-Alias-](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) Cmdlet aus, um die bereits verwendeten Aliase anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="479cc-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="479cc-111">Fügen Sie ein Alias Präfix ein, das auf das Verb des Cmdlet-namens verweist, und ein Alias Suffix, das auf das Substantiv des Cmdlet-namens verweist.</span><span class="sxs-lookup"><span data-stu-id="479cc-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="479cc-112">Der Alias für das Cmdlet "`Import-Module`" ist beispielsweise "ipmo".</span><span class="sxs-lookup"><span data-stu-id="479cc-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="479cc-113">Eine Liste aller Verben und deren Aliase finden [Sie unter Cmdlet-Verben](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="479cc-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="479cc-114">Für Cmdlets, die über das gleiche Verb verfügen, müssen Sie dasselbe Alias Präfix einschließen.</span><span class="sxs-lookup"><span data-stu-id="479cc-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="479cc-115">Beispielsweise wird für die Aliase für alle Windows PowerShell-Cmdlets, die das Verb "Get" im Namen aufweisen, das Präfix "g" verwendet.</span><span class="sxs-lookup"><span data-stu-id="479cc-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="479cc-116">Verwenden Sie für Cmdlets mit demselben Substantiv dasselbe Alias Suffix.</span><span class="sxs-lookup"><span data-stu-id="479cc-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="479cc-117">Beispielsweise wird für die Aliase für alle Windows PowerShell-Cmdlets, die das "Session"-Substantiv in Ihrem Namen aufweisen, das "sn"-Suffix verwendet.</span><span class="sxs-lookup"><span data-stu-id="479cc-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="479cc-118">Verwenden Sie für Cmdlets, die Befehlen in anderen Sprachen entsprechen, den Namen des Befehls.</span><span class="sxs-lookup"><span data-stu-id="479cc-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="479cc-119">Im Allgemeinen sollten Sie Aliase so kurz wie möglich machen.</span><span class="sxs-lookup"><span data-stu-id="479cc-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="479cc-120">Stellen Sie sicher, dass der Alias mindestens ein unterschiedliches Zeichen für das Verb und ein eindeutiges Zeichen für das Substantiv aufweist.</span><span class="sxs-lookup"><span data-stu-id="479cc-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="479cc-121">Fügen Sie nach Bedarf weitere Zeichen hinzu, um den Alias eindeutig zu machen.</span><span class="sxs-lookup"><span data-stu-id="479cc-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="479cc-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="479cc-122">See Also</span></span>

[<span data-ttu-id="479cc-123">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="479cc-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
