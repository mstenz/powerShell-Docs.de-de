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
ms.openlocfilehash: c1d8984f4aad7bae6f9be66a2222e2c74c8afa3d
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022211"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="7b15a-102">Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="7b15a-102">Cmdlet Parameters</span></span>

<span data-ttu-id="7b15a-103">Cmdlet-Parameter stellen den Mechanismus bereit, mit dem ein Cmdlet Eingaben akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="7b15a-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="7b15a-104">Parameter können Eingaben direkt von der Befehlszeile aus oder von Objekten, die an das Cmdlet über die Pipeline übergeben werden, annehmen. die Argumente (auch als " *Werte*" bezeichnet) können die Eingabe angeben, die das Cmdlet akzeptiert, wie das Cmdlet die Aktionen durchführt, und die Daten, die das Cmdlet an die Pipeline zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="7b15a-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7b15a-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="7b15a-105">In This Section</span></span>

<span data-ttu-id="7b15a-106">[Deklarieren von Eigenschaften als Parameter](./declaring-properties-as-parameters.md) Enthält grundlegende Informationen, die Sie kennen müssen, bevor Sie die Parameter eines Cmdlets deklarieren.</span><span class="sxs-lookup"><span data-stu-id="7b15a-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="7b15a-107">[Typen von Cmdlet-Parametern](./types-of-cmdlet-parameters.md) Beschreibt die verschiedenen Typen von Parametern, die Sie in Cmdlets deklarieren können.</span><span class="sxs-lookup"><span data-stu-id="7b15a-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="7b15a-108">[Cmdlet-Parameter Name und-Funktions Richtlinien](./standard-cmdlet-parameter-names-and-types.md) Erläutert die Namen, den empfohlenen Datentyp und die Funktionalität von Standardparametern.</span><span class="sxs-lookup"><span data-stu-id="7b15a-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="7b15a-109">[Parameter Aliase](./parameter-aliases.md) Erläutert die Aliase, die Sie für Parameter definieren können.</span><span class="sxs-lookup"><span data-stu-id="7b15a-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="7b15a-110">[Allgemeine Parameter Namen](./common-parameter-names.md) In diesem Thema werden die Parameter beschrieben, die von Windows PowerShell Cmdlets hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="7b15a-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="7b15a-111">[Cmdlet-Parameter Sätze](./cmdlet-parameter-sets.md) Erläutert, wie Parametersätze es Ihnen ermöglichen, ein einzelnes Cmdlet zu schreiben, das verschiedene Aktionen für verschiedene Szenarien ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="7b15a-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="7b15a-112">[Dynamische Cmdlet-Parameter](./cmdlet-dynamic-parameters.md) Erläutert Parameter, die für den Benutzer unter besonderen Bedingungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="7b15a-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="7b15a-113">[Unterstützende Platzhalter Zeichen in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md) Beschreibt das Bereitstellen von Unterstützung für Platzhalter Zeichen beim Entwerfen eines Cmdlets, das für eine Gruppe von Ressourcen ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7b15a-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="7b15a-114">Überprüfen der [Parameter Eingabe](./validating-parameter-input.md) Beschreibt, wie Windows PowerShell die an Cmdlet-Parameter übergebenen Argumente überprüft.</span><span class="sxs-lookup"><span data-stu-id="7b15a-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="7b15a-115">[Eingabe Filter Parameter](./input-filter-parameters.md) Erläutert die `Filter`, `Include`und `Exclude` Parameter, die den Satz von Eingabe Objekten filtern, auf die sich das Cmdlet auswirkt.</span><span class="sxs-lookup"><span data-stu-id="7b15a-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7b15a-116">Verwandte Abschnitte</span><span class="sxs-lookup"><span data-stu-id="7b15a-116">Related Sections</span></span>

[<span data-ttu-id="7b15a-117">Validieren von Parameter Eingaben</span><span class="sxs-lookup"><span data-stu-id="7b15a-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="7b15a-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7b15a-118">See Also</span></span>

[<span data-ttu-id="7b15a-119">Parameter Attribut Deklaration</span><span class="sxs-lookup"><span data-stu-id="7b15a-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="7b15a-120">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="7b15a-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
