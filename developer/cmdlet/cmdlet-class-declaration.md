---
title: Cmdlet-Klassendeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068639"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="ad28a-102">Deklaration der Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="ad28a-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="ad28a-103">Microsoft .NET Framework-Klasse ist als ein Cmdlet deklariert, durch Angabe der **Cmdlet** -Attribut als Metadaten für die Klasse.</span><span class="sxs-lookup"><span data-stu-id="ad28a-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="ad28a-104">(Die **Cmdlet** -Attribut ist das einzige erforderliche Attribut für alle Cmdlets).</span><span class="sxs-lookup"><span data-stu-id="ad28a-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="ad28a-105">Bei Angabe der **Cmdlet** -Attribut, müssen Sie das Verb-Substantiv-Paar, das das-Cmdlet für den Benutzer identifiziert angeben.</span><span class="sxs-lookup"><span data-stu-id="ad28a-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="ad28a-106">Und Sie müssen die Windows PowerShell-Funktionen, die das Cmdlet unterstützt beschreiben.</span><span class="sxs-lookup"><span data-stu-id="ad28a-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="ad28a-107">Weitere Informationen über die Syntax zum Deklarieren, die verwendet wird, an die **Cmdlet** Attribut, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ad28a-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ad28a-108">Die **Cmdlet** Attribut wird definiert, indem die [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="ad28a-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="ad28a-109">Die Eigenschaften dieser Klasse entsprechen den Parametern der Deklaration aus, die verwendet werden, wenn Sie das Attribut deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ad28a-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="ad28a-110">Nomen</span><span class="sxs-lookup"><span data-stu-id="ad28a-110">Nouns</span></span>

<span data-ttu-id="ad28a-111">Das Nomen "des Cmdlets" gibt an, die Ressourcen, die auf denen das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ad28a-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="ad28a-112">Das Nomen unterscheidet Ihre Cmdlets von anderen Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ad28a-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="ad28a-113">Nomen im Cmdlet-Namen muss spezifisch, und im Fall von generischen Nomen, z. B. *Server*, es wird empfohlen, ein kurzes Präfix hinzufügen, das die Ressource von anderen ähnlichen Ressourcen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="ad28a-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="ad28a-114">Ist Sie ein Cmdlet-Namen, die ein Substantiv mit einem Präfix enthält z. B. `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="ad28a-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="ad28a-115">Die Kombination aus einem bestimmten Nomen verbunden mit einem allgemeineren Verb ermöglicht den Benutzer schnell das-Cmdlet, durch die Aktion, und klicken Sie dann das Cmdlet mit der Ressourcen zu identifizieren, während die Vermeidung der mehrfachen Ausführung unnötige Cmdlet-Namen.</span><span class="sxs-lookup"><span data-stu-id="ad28a-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="ad28a-116">Eine Liste der Sonderzeichen, die in der Cmdlet-Namen verwendet werden können, finden Sie unter [Entwicklungsrichtlinien erforderlich](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="ad28a-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="ad28a-117">Verben</span><span class="sxs-lookup"><span data-stu-id="ad28a-117">Verbs</span></span>

<span data-ttu-id="ad28a-118">Wenn Sie ein Verb angeben, erfordern die Richtlinien für die Entwicklung Sie eine der vordefinierten bereitgestellten, die von Windows PowerShell-Verben verwenden.</span><span class="sxs-lookup"><span data-stu-id="ad28a-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="ad28a-119">Mithilfe einer dieser vordefinierten Verben, sorgt Sie Konsistenz zwischen den Cmdlets, die Sie schreiben und die Cmdlets, die von Microsoft und von anderen Benutzern geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="ad28a-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="ad28a-120">Beispielsweise wird das Verb "Get" für Cmdlets verwendet, die Daten abrufen.</span><span class="sxs-lookup"><span data-stu-id="ad28a-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="ad28a-121">Weitere Informationen zu Richtlinien für die Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ad28a-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="ad28a-122">Eine Liste der Sonderzeichen, die in der Cmdlet-Namen verwendet werden können, finden Sie unter [Entwicklungsrichtlinien erforderlich](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="ad28a-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="ad28a-123">Unterstützung von Windows PowerShell-Funktionen</span><span class="sxs-lookup"><span data-stu-id="ad28a-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="ad28a-124">Die **Cmdlet** Attribut auch können Sie angeben, dass Ihr Cmdlet einige gemeinsame Funktionen unterstützt, die von Windows PowerShell bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="ad28a-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="ad28a-125">Dies schließt Unterstützung für allgemeine Funktionen wie z. B. Benutzer-Feedback-Bestätigung (als Unterstützung für die ShouldProcess-Funktion bezeichnet) und Unterstützung für Transaktionen.</span><span class="sxs-lookup"><span data-stu-id="ad28a-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="ad28a-126">(Unterstützung für Transaktionen wurde in Windows PowerShell 2.0 eingeführt).</span><span class="sxs-lookup"><span data-stu-id="ad28a-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="ad28a-127">Weitere Informationen über die Syntax zum Deklarieren, die verwendet wird, an die **Cmdlet** Attribut, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ad28a-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="ad28a-128">Cmdlet-Klassendefinition</span><span class="sxs-lookup"><span data-stu-id="ad28a-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="ad28a-129">Der folgende Code ist die Definition für eine GetProc Cmdlet-Klasse.</span><span class="sxs-lookup"><span data-stu-id="ad28a-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="ad28a-130">Beachten Sie, Pascal-Schreibweise verwendet wird, und dass der Name der Klasse die Verb- und des-Cmdlets enthält.</span><span class="sxs-lookup"><span data-stu-id="ad28a-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="ad28a-131">Pascal-Schreibweise</span><span class="sxs-lookup"><span data-stu-id="ad28a-131">Pascal Casing</span></span>

<span data-ttu-id="ad28a-132">Wenn Sie Cmdlets Namen verwenden, verwenden Sie die Pascal-Schreibweise zur Groß-und Kleinschreibung.</span><span class="sxs-lookup"><span data-stu-id="ad28a-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="ad28a-133">Z. B. die `Get-Item` und `Get-ItemProperty` Cmdlets anzuzeigen, die richtige Vorgehensweise Groß/Kleinschreibung zu verwenden, wenn Sie Cmdlets benennen.</span><span class="sxs-lookup"><span data-stu-id="ad28a-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad28a-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ad28a-134">See Also</span></span>

[<span data-ttu-id="ad28a-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="ad28a-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="ad28a-136">CmdletAttribute-Deklaration</span><span class="sxs-lookup"><span data-stu-id="ad28a-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="ad28a-137">-Cmdlet Verbnamen</span><span class="sxs-lookup"><span data-stu-id="ad28a-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="ad28a-138">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ad28a-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="ad28a-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ad28a-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
