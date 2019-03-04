---
title: Parameter-Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863616"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="aac29-102">Attributdeklaration: Parameter</span><span class="sxs-lookup"><span data-stu-id="aac29-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="aac29-103">Der Parameter-Attribut identifiziert eine öffentliche Eigenschaft von der Cmdlet-Klasse als Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="aac29-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aac29-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="aac29-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="aac29-105">Parameters</span></span>

<span data-ttu-id="aac29-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="aac29-107">`True` Gibt an, dass die Cmdlet-Parameter erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="aac29-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="aac29-108">Wenn ein erforderlicher Parameter nicht angegeben wird, wenn das-Cmdlet aufgerufen wird, fordert Windows PowerShell den Benutzer einen Parameterwert an.</span><span class="sxs-lookup"><span data-stu-id="aac29-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="aac29-109">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="aac29-109">The default is `false`.</span></span>

<span data-ttu-id="aac29-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="aac29-111">Gibt an, dass der Parameter festgelegt, dass dieses Cmdlet-Parameter gehört.</span><span class="sxs-lookup"><span data-stu-id="aac29-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="aac29-112">Wenn kein Parametersatz angegeben wird, gehört der Parameter alle Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="aac29-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="aac29-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="aac29-114">Gibt die Position des Parameters in einem Windows PowerShell-Befehl.</span><span class="sxs-lookup"><span data-stu-id="aac29-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="aac29-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="aac29-116">`True` Gibt an, dass es sich bei der Cmdlet-Parameter den Wert von einem Pipelineobjekt akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="aac29-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="aac29-117">Geben Sie dieses Schlüsselwort ein, wenn das Cmdlet die vollständige greift auf Objekt "," nicht nur eine Eigenschaft des Objekts.</span><span class="sxs-lookup"><span data-stu-id="aac29-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="aac29-118">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="aac29-118">The default is `false`.</span></span>

<span data-ttu-id="aac29-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="aac29-120">`True` Gibt an, dass der Cmdlet-Parameter den Wert aus einer Eigenschaft eines Objekts der Pipeline annimmt, der den gleichen Namen oder den gleichen Alias als dieser Parameter aufweist.</span><span class="sxs-lookup"><span data-stu-id="aac29-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="aac29-121">Wenn das-Cmdlet hat beispielsweise eine `Name` Parameter und das Pipelineobjekt verfügt auch über eine `Name` -Eigenschaft wird der Wert des der `Name` Eigenschaft zugewiesen wird der `Name` -Parameter des Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="aac29-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="aac29-122">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="aac29-122">The default is `false`.</span></span>

<span data-ttu-id="aac29-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="aac29-124">`True` Gibt an, dass die Cmdlet-Parameter. alle übrigen Argumente akzeptiert, die an das Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="aac29-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="aac29-125">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="aac29-125">The default is `false`.</span></span>

<span data-ttu-id="aac29-126">`HelpMessage` Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="aac29-127">Gibt eine kurze Beschreibung des Parameters an.</span><span class="sxs-lookup"><span data-stu-id="aac29-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="aac29-128">Windows PowerShell zeigt diese an, wenn ein Cmdlet ausgeführt wird, und ein obligatorischen Parameter nicht angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="aac29-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="aac29-129">`HelpMessageBaseName` Optional benannter Parameter. Gibt den Speicherort, in dem Ressourcen-IDs gespeichert.</span><span class="sxs-lookup"><span data-stu-id="aac29-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="aac29-130">Dieser Parameter kann beispielsweise eine Ressourcenassembly angeben, die Hilfe zu Meldungen enthält, die Sie lokalisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="aac29-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="aac29-131">`HelpMessageResourceId` Optional benannter Parameter. Gibt den Ressourcenbezeichner für eine hilfemeldung an.</span><span class="sxs-lookup"><span data-stu-id="aac29-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="aac29-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="aac29-132">Remarks</span></span>

- <span data-ttu-id="aac29-133">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Cmdlet-Parametern deklarieren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aac29-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="aac29-134">Ein Cmdlet kann eine beliebige Anzahl von Parametern haben.</span><span class="sxs-lookup"><span data-stu-id="aac29-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="aac29-135">Allerdings für eine bessere benutzererfahrung, begrenzen Sie die Anzahl von Parametern an.</span><span class="sxs-lookup"><span data-stu-id="aac29-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="aac29-136">Parameter müssen auf öffentlichen nicht statischen Felder oder Eigenschaften deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="aac29-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="aac29-137">Parameter sollten Eigenschaften deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="aac29-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="aac29-138">Die Eigenschaft muss einen öffentlichen Set-Accessor, haben und wenn die `ValueFromPipeline` oder `ValueFromPipelineByPropertyName` -Schlüsselwort angegeben ist, die Eigenschaft muss einen öffentlichen Get-Accessor haben.</span><span class="sxs-lookup"><span data-stu-id="aac29-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="aac29-139">Wenn Sie positionelle Parameter angeben, die Anzahl von Positionsparametern, die in einem Parameter, die auf weniger als fünf festlegen.</span><span class="sxs-lookup"><span data-stu-id="aac29-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="aac29-140">Und Positionsparameter müssen nicht zusammenhängend sein.</span><span class="sxs-lookup"><span data-stu-id="aac29-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="aac29-141">Positionen 5, 100 und 250 funktionieren genauso wie die Positionen 0, 1 und 2.</span><span class="sxs-lookup"><span data-stu-id="aac29-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="aac29-142">Wenn die `Position` -Schlüsselwort ist nicht angegeben, die der Cmdlet-Parameter muss mit seinem Namen verwiesen werden.</span><span class="sxs-lookup"><span data-stu-id="aac29-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="aac29-143">Wenn Sie Parameter verwenden, beachten Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="aac29-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="aac29-144">Jeder Parametersatz müssen mindestens eine unique-Parameter.</span><span class="sxs-lookup"><span data-stu-id="aac29-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="aac29-145">Gute Cmdlet-Design gibt an, dass dieser eindeutige Parameter auch nach Möglichkeit obligatorisch sein soll.</span><span class="sxs-lookup"><span data-stu-id="aac29-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="aac29-146">Wenn Ihr Cmdlet ohne Parameter ausgeführt werden soll, darf nicht der unique-Parameter erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="aac29-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="aac29-147">Keine Parametersatz sollte mehr als eine positionelle Parameter mit der gleichen Position enthalten.</span><span class="sxs-lookup"><span data-stu-id="aac29-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="aac29-148">Sollte nur einen Parameter in einem Parametersatz deklarieren `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="aac29-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="aac29-149">Es können mehrere Parameter definieren `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="aac29-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="aac29-150">Es können mehrere Parameter definieren `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="aac29-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="aac29-151">Weitere Informationen zu den Richtlinien für Parameternamen verwendet, finden Sie unter [Cmdlet-Parameternamen](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="aac29-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="aac29-152">Der Parameter-Attribut wird definiert, durch die [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="aac29-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="aac29-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aac29-153">See Also</span></span>

[<span data-ttu-id="aac29-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="aac29-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="aac29-155">Cmdlet-Parameternamen</span><span class="sxs-lookup"><span data-stu-id="aac29-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="aac29-156">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="aac29-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
