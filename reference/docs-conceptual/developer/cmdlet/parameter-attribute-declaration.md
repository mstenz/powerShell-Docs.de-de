---
title: Deklaration des Parameter Attributs | Microsoft-Dokumentation
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
ms.openlocfilehash: 7482690c44cdaabf23b886107ac5d112c0fa5c9d
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692390"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="1f4b4-102">Attributdeklaration: Parameter</span><span class="sxs-lookup"><span data-stu-id="1f4b4-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="1f4b4-103">Das Parameter Attribut identifiziert eine öffentliche Eigenschaft der Cmdlet-Klasse als Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f4b4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f4b4-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="1f4b4-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="1f4b4-105">Parameters</span></span>

<span data-ttu-id="1f4b4-106">`Mandatory`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1f4b4-107">`True`Gibt an, dass der Cmdlet-Parameter erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="1f4b4-108">Wenn ein erforderlicher Parameter nicht bereitgestellt wird, wenn das Cmdlet aufgerufen wird, fordert Windows PowerShell den Benutzer auf, einen Parameterwert einzugeben.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="1f4b4-109">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-109">The default is `false`.</span></span>

<span data-ttu-id="1f4b4-110">`ParameterSetName`([System. String](/dotnet/api/System.String)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="1f4b4-111">Gibt den Parametersatz an, zu dem dieser Cmdlet-Parameter gehört.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="1f4b4-112">Wenn kein Parametersatz angegeben wird, gehört der Parameter zu allen Parametersätzen.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="1f4b4-113">`Position`([System. Int32](/dotnet/api/System.Int32)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="1f4b4-114">Gibt die Position des Parameters innerhalb eines Windows PowerShell-Befehls an.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="1f4b4-115">`ValueFromPipeline`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1f4b4-116">`True`Gibt an, dass der Cmdlet-Parameter seinen Wert von einem Pipeline Objekt annimmt.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="1f4b4-117">Geben Sie dieses Schlüsselwort an, wenn das Cmdlet auf das gesamte Objekt zugreift, nicht nur auf eine Eigenschaft des Objekts.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="1f4b4-118">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-118">The default is `false`.</span></span>

<span data-ttu-id="1f4b4-119">`ValueFromPipelineByPropertyName`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1f4b4-120">`True`Gibt an, dass der Cmdlet-Parameter seinen Wert von einer Eigenschaft eines Pipeline Objekts annimmt, das entweder denselben Namen oder denselben Alias wie dieser Parameter hat.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="1f4b4-121">Wenn das Cmdlet beispielsweise über einen `Name` -Parameter verfügt und das Pipeline Objekt auch über eine- `Name` Eigenschaft verfügt, wird der Wert der-Eigenschaft dem- `Name` `Name` Parameter des Cmdlets zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="1f4b4-122">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-122">The default is `false`.</span></span>

<span data-ttu-id="1f4b4-123">`ValueFromRemainingArguments`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="1f4b4-124">`True`Gibt an, dass der Cmdlet-Parameter alle verbleibenden Argumente annimmt, die an das Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="1f4b4-125">Der Standardwert ist `false`.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-125">The default is `false`.</span></span>

<span data-ttu-id="1f4b4-126">`HelpMessage`Optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="1f4b4-127">Gibt eine kurze Beschreibung des Parameters an.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="1f4b4-128">Windows PowerShell zeigt diese Meldung an, wenn ein Cmdlet ausgeführt wird und kein obligatorischer Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="1f4b4-129">`HelpMessageBaseName`Optionaler benannter Parameter. Gibt den Speicherort der Ressourcen Bezeichner an.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="1f4b4-130">Mit diesem Parameter kann z. b. eine Ressourcenassembly angegeben werden, die Hilfe Meldungen enthält, die Sie lokalisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="1f4b4-131">`HelpMessageResourceId`Optionaler benannter Parameter. Gibt den Ressourcen Bezeichner für eine Hilfe Nachricht an.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f4b4-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1f4b4-132">Remarks</span></span>

- <span data-ttu-id="1f4b4-133">Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Deklarieren von Cmdlet-Parametern](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1f4b4-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="1f4b4-134">Ein Cmdlet kann eine beliebige Anzahl von Parametern aufweisen.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="1f4b4-135">Um jedoch eine bessere Benutzer Leistung zu erzielen, begrenzen Sie die Anzahl der Parameter.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="1f4b4-136">Parameter müssen für öffentliche, nicht statische Felder oder Eigenschaften deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="1f4b4-137">Parameter sollten in Eigenschaften deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="1f4b4-138">Die-Eigenschaft muss über einen öffentlichen Set-Accessor verfügen, und wenn das- `ValueFromPipeline` oder- `ValueFromPipelineByPropertyName` Schlüsselwort angegeben ist, muss die-Eigenschaft über einen öffentlichen get-Accessor verfügen.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="1f4b4-139">Wenn Sie Positions Parameter angeben, begrenzen Sie die Anzahl der positionellen Parameter in einem Parameter, der auf weniger als fünf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="1f4b4-140">Und Positions Parameter müssen nicht zusammenhängend sein.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="1f4b4-141">Die Positionen 5, 100 und 250 funktionieren identisch mit den Positionen 0, 1 und 2.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="1f4b4-142">Wenn das `Position` Schlüsselwort nicht angegeben wird, muss der Name des Cmdlet-Parameters referenziert werden.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="1f4b4-143">Beachten Sie bei der Verwendung von Parametersätzen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="1f4b4-143">When you use parameter sets, note the following:</span></span>

  - <span data-ttu-id="1f4b4-144">Jeder Parametersatz muss mindestens einen eindeutigen Parameter aufweisen.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="1f4b4-145">Ein gutes Cmdlet-Design gibt an, dass dieser eindeutige Parameter nach Möglichkeit auch obligatorisch sein sollte.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="1f4b4-146">Wenn das Cmdlet ohne Parameter ausgeführt werden soll, kann der Unique-Parameter nicht obligatorisch sein.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

  - <span data-ttu-id="1f4b4-147">Kein Parametersatz sollte mehr als einen positionellen Parameter mit der gleichen Position enthalten.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

  - <span data-ttu-id="1f4b4-148">Nur ein Parameter in einem Parametersatz muss deklarieren `ValueFromPipeline = true` .</span><span class="sxs-lookup"><span data-stu-id="1f4b4-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="1f4b4-149">Mehrere Parameter können definieren `ValueFromPipelineByPropertyName = true` .</span><span class="sxs-lookup"><span data-stu-id="1f4b4-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

  - <span data-ttu-id="1f4b4-150">Mehrere Parameter können definieren `ValueFromPipelineByPropertyName = true` .</span><span class="sxs-lookup"><span data-stu-id="1f4b4-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="1f4b4-151">Weitere Informationen zu den Richtlinien für Parameternamen finden [Sie unter Cmdlet-Parameternamen](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="1f4b4-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="1f4b4-152">Das Parameter Attribut wird von der [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="1f4b4-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f4b4-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1f4b4-153">See Also</span></span>

[<span data-ttu-id="1f4b4-154">System. Management. Automation. ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="1f4b4-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="1f4b4-155">Cmdlet-Parameter Namen</span><span class="sxs-lookup"><span data-stu-id="1f4b4-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="1f4b4-156">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1f4b4-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
