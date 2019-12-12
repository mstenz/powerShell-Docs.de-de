---
title: Cmdlet-Klassen Deklaration | Microsoft-Dokumentation
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
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363519"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="5d592-102">Deklaration der Cmdlet-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d592-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="5d592-103">Eine Microsoft .NET Framework-Klasse wird als Cmdlet deklariert, indem das **Cmdlet** -Attribut als Metadaten für die-Klasse angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5d592-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="5d592-104">(Das **Cmdlet** -Attribut ist das einzige erforderliche Attribut für alle Cmdlets).</span><span class="sxs-lookup"><span data-stu-id="5d592-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="5d592-105">Wenn Sie das **Cmdlet** -Attribut angeben, müssen Sie das Verb-und-Substantiv-Paar angeben, das das Cmdlet für den Benutzer identifiziert.</span><span class="sxs-lookup"><span data-stu-id="5d592-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="5d592-106">Und Sie müssen die Windows PowerShell-Funktionalität beschreiben, die vom Cmdlet unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="5d592-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="5d592-107">Weitere Informationen zur Deklarations Syntax, die zum Angeben des **Cmdlet** -Attributs verwendet wird, finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5d592-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5d592-108">Das **Cmdlet** -Attribut wird von der [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="5d592-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="5d592-109">Die Eigenschaften dieser Klasse entsprechen den Deklarations Parametern, die beim Deklarieren des Attributs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d592-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="5d592-110">Nomen</span><span class="sxs-lookup"><span data-stu-id="5d592-110">Nouns</span></span>

<span data-ttu-id="5d592-111">Das Substantiv des Cmdlets gibt die Ressourcen an, auf die das Cmdlet angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="5d592-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="5d592-112">Das Substantiv unterscheidet Ihre Cmdlets von anderen Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5d592-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="5d592-113">Nomen in Cmdlet-Namen müssen spezifisch sein, und im Fall von generischen Substantiven, wie z. b. *Server*, ist es am besten, ein kurzes Präfix hinzuzufügen, das Ihre Ressource von anderen ähnlichen Ressourcen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="5d592-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="5d592-114">Beispielsweise ist ein Cmdlet-Name, der ein Substantiv mit einem Präfix enthält, `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="5d592-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="5d592-115">Die Kombination eines bestimmten Substantiv mit einem allgemeineren Verb ermöglicht dem Benutzer, das Cmdlet anhand seiner Aktion schnell zu finden und dann das Cmdlet anhand seiner Ressource zu identifizieren, während unnötige Cmdlet-namens Duplikate vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="5d592-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="5d592-116">Eine Liste von Sonderzeichen, die in Cmdlet-Namen nicht verwendet werden können, finden Sie unter [erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="5d592-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="5d592-117">Verben</span><span class="sxs-lookup"><span data-stu-id="5d592-117">Verbs</span></span>

<span data-ttu-id="5d592-118">Wenn Sie ein Verb angeben, müssen Sie für die Entwicklungs Richtlinien eines der vordefinierten Verben verwenden, die von Windows PowerShell bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5d592-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="5d592-119">Wenn Sie eines dieser vordefinierten Verben verwenden, gewährleisten Sie die Konsistenz zwischen den Cmdlets, die Sie schreiben, und den Cmdlets, die von Microsoft und anderen geschrieben wurden.</span><span class="sxs-lookup"><span data-stu-id="5d592-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="5d592-120">Beispielsweise wird das Verb "Get" für Cmdlets verwendet, mit denen Daten abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="5d592-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="5d592-121">Weitere Informationen zu den Richtlinien für Verben finden [Sie unter Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="5d592-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="5d592-122">Eine Liste von Sonderzeichen, die in Cmdlet-Namen nicht verwendet werden können, finden Sie unter [erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="5d592-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="5d592-123">Unterstützung der Windows PowerShell-Funktionalität</span><span class="sxs-lookup"><span data-stu-id="5d592-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="5d592-124">Mit dem **Cmdlet** -Attribut können Sie auch angeben, dass das Cmdlet einige der allgemeinen Funktionen unterstützt, die von Windows PowerShell bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5d592-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="5d592-125">Dies umfasst die Unterstützung allgemeiner Funktionen, wie z. b. die Bestätigung von Benutzer Feedback (als Unterstützung für die Funktion "Schulter verarbeiten" bezeichnet) und die Unterstützung von Transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5d592-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="5d592-126">(Die Unterstützung für Transaktionen wurde in Windows PowerShell 2,0 eingeführt.)</span><span class="sxs-lookup"><span data-stu-id="5d592-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="5d592-127">Weitere Informationen zur Deklarations Syntax, die zum Angeben des **Cmdlet** -Attributs verwendet wird, finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5d592-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="5d592-128">Cmdlet-Klassendefinition</span><span class="sxs-lookup"><span data-stu-id="5d592-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="5d592-129">Der folgende Code ist die Definition für eine getproc-Cmdlet-Klasse.</span><span class="sxs-lookup"><span data-stu-id="5d592-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="5d592-130">Beachten Sie, dass die Pascal-Schreibweise verwendet wird und dass der Name der Klasse das Verb und das Substantiv des Cmdlets enthält.</span><span class="sxs-lookup"><span data-stu-id="5d592-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="5d592-131">Pascal-Schreibweise</span><span class="sxs-lookup"><span data-stu-id="5d592-131">Pascal Casing</span></span>

<span data-ttu-id="5d592-132">Wenn Sie Cmdlets benennen, verwenden Sie die Pascal-Schreibweise.</span><span class="sxs-lookup"><span data-stu-id="5d592-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="5d592-133">Die Cmdlets `Get-Item` und `Get-ItemProperty` zeigen z. b. die richtige Methode für die Verwendung von Groß-und Kleinschreibung, wenn Sie Cmdlets benennen.</span><span class="sxs-lookup"><span data-stu-id="5d592-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d592-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5d592-134">See Also</span></span>

[<span data-ttu-id="5d592-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="5d592-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="5d592-136">CmdletAttribute-Deklaration</span><span class="sxs-lookup"><span data-stu-id="5d592-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="5d592-137">Cmdlet-Verb Namen</span><span class="sxs-lookup"><span data-stu-id="5d592-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="5d592-138">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="5d592-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="5d592-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5d592-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
