---
title: Cmdlet-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068401"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="9f5ca-102">Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="9f5ca-102">Cmdlet Parameters</span></span>

<span data-ttu-id="9f5ca-103">Cmdlet-Parameter angeben, den Mechanismus, der ein Cmdlet Eingaben akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="9f5ca-104">Parameter können Eingaben direkt über die Befehlszeile oder von Objekten, die an das Cmdlet übergeben, über die Pipeline, die Argumente akzeptieren (auch bekannt als *Werte*) für diese Parameter können angeben, die Eingabe, die das Cmdlet akzeptiert, wie die Cmdlet sollte seine Aktionen und die Daten, die das Cmdlet gibt zurück, an die Pipeline ausführen.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9f5ca-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="9f5ca-105">In This Section</span></span>

<span data-ttu-id="9f5ca-106">[Deklarieren von Eigenschaften, die als Parameter](./declaring-properties-as-parameters.md) enthält grundlegende Informationen Sie verstehen müssen, bevor Sie mit die Parametern eines Cmdlets deklarieren.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="9f5ca-107">[Typen von Parametern des Cmdlets](./types-of-cmdlet-parameters.md) beschreibt die verschiedenen Typen von Parametern, die Sie in Cmdlets deklarieren können.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="9f5ca-108">[Cmdlet-Parameternamen und Funktionalität Richtlinien](./standard-cmdlet-parameter-names-and-types.md) Erörtern Sie die Namen der empfohlen wird, Datentyp und die Funktionen der standard-Parameter.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="9f5ca-109">[Parameteraliase](./parameter-aliases.md) wird erläutert, die Aliase, die Sie für Parameter definieren können.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="9f5ca-110">[Allgemeine Parameternamen](./common-parameter-names.md) in diesem Thema wird beschrieben, die Parameter, die Windows PowerShell-Cmdlets hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="9f5ca-111">[-Cmdlet-Parameter wird](./cmdlet-parameter-sets.md) wird erläutert, wie Parametersätze ermöglichen es Ihnen, ein einzelnes Cmdlet schreiben, die für verschiedene Szenarien verschiedene Aktionen ausführen können.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="9f5ca-112">[Dynamische Cmdletparameter](./cmdlet-dynamic-parameters.md) wird erläutert, Parameter, die für den Benutzer unter speziellen Bedingungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="9f5ca-113">[Unterstützung von Platzhalterzeichen in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md) wird beschrieben, wie in der Unterstützung für Platzhalterzeichen beim Entwerfen eines Cmdlets, die für eine Gruppe von Ressourcen ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="9f5ca-114">[Überprüfen der Parametereingabe](./validating-parameter-input.md) wird beschrieben, wie Windows PowerShell-Cmdlet-Parameter übergebenen Argumente überprüft.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="9f5ca-115">[Geben Sie Filterparameter](./input-filter-parameters.md) behandelt die `Filter`, `Include`, und `Exclude` Parameter, die den Satz von Eingabeobjekten zu filtern, die das Cmdlet wirkt sich auf.</span><span class="sxs-lookup"><span data-stu-id="9f5ca-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9f5ca-116">Verwandte Abschnitte</span><span class="sxs-lookup"><span data-stu-id="9f5ca-116">Related Sections</span></span>

[<span data-ttu-id="9f5ca-117">Gewusst wie: Überprüfen der Parametereingabe</span><span class="sxs-lookup"><span data-stu-id="9f5ca-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="9f5ca-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9f5ca-118">See Also</span></span>

[<span data-ttu-id="9f5ca-119">Parameterdeklaration-Attribut</span><span class="sxs-lookup"><span data-stu-id="9f5ca-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="9f5ca-120">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="9f5ca-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
