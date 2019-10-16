---
title: Eingabe Filter Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364389"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="7d901-102">Eingabe von Filterparametern</span><span class="sxs-lookup"><span data-stu-id="7d901-102">Input Filter Parameters</span></span>

<span data-ttu-id="7d901-103">Ein Cmdlet kann die Parameter "`Filter`", "`Include`" und "`Exclude`" definieren, die den Satz von Eingabe Objekten filtern, auf die das Cmdlet wirkt.</span><span class="sxs-lookup"><span data-stu-id="7d901-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="7d901-104">In der Regel wird der Satz von Eingabe Objekten von einem `InputObject`-, `Path`-oder `Name`-Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="7d901-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="7d901-105">Beispielsweise kann ein Cmdlet über einen `Path`-Parameter verfügen, der mehrere Pfade mithilfe von Platzhalter Zeichen annimmt, und jeder Pfad verweist auf ein Eingabe Objekt.</span><span class="sxs-lookup"><span data-stu-id="7d901-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="7d901-106">Wenn die Parameter "`Filter`", "`Include`" und "`Exclude`" zusammen verwendet werden, qualifizieren Sie die Pfade, die das Cmdlet bei jedem Aufruf verwendet.</span><span class="sxs-lookup"><span data-stu-id="7d901-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="7d901-107">Einschließen und Ausschließen von Parametern</span><span class="sxs-lookup"><span data-stu-id="7d901-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="7d901-108">Mit den Parametern "`Include`" und "`Exclude`" werden die Objekte identifiziert, die in den an das Cmdlet weiter gegebenen Satz von Eingabe Objekten eingeschlossen oder ausgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="7d901-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="7d901-109">Verwenden Sie diese Parameter, wenn der Filter in der standardmäßigen Platzhalter Sprache ausgedrückt werden kann.</span><span class="sxs-lookup"><span data-stu-id="7d901-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="7d901-110">(Weitere Informationen zu Platzhalter Zeichen finden Sie [unter unterstützen von Platzhaltern in Cmdlet-Parametern](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Der `Include`-Parameter schließt alle Objekte ein, deren Namen dem Inklusions Filter entsprechen.</span><span class="sxs-lookup"><span data-stu-id="7d901-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="7d901-111">Der Parameter "`Exclude`" schließt alle Objekte aus, deren Namen dem Filter entsprechen.</span><span class="sxs-lookup"><span data-stu-id="7d901-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="7d901-112">Filter Parameter</span><span class="sxs-lookup"><span data-stu-id="7d901-112">Filter Parameter</span></span>

<span data-ttu-id="7d901-113">Der Parameter "`Filter`" gibt einen Filter an, der nicht in der standardmäßigen Platzhalter Sprache ausgedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="7d901-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="7d901-114">Beispielsweise können Active Directory-Dienst Schnittstellen (ADSI) oder SQL-Filter über den `Filter`-Parameter an das Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="7d901-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="7d901-115">In den Cmdlets, die von Windows PowerShell bereitgestellt werden, werden diese Filter von den Windows PowerShell-Anbietern angegeben, die das Cmdlet für den Zugriff auf einen Datenspeicher verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d901-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="7d901-116">Jeder Anbieter definiert in der Regel seinen eigenen Filter.</span><span class="sxs-lookup"><span data-stu-id="7d901-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="7d901-117">Filterung, wenn kein Satz von Eingabe Objekten angegeben ist</span><span class="sxs-lookup"><span data-stu-id="7d901-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="7d901-118">Wenn kein Satz von Eingabe Objekten angegeben ist, bedeutet dies normalerweise, dass alle Objekte gefiltert werden.</span><span class="sxs-lookup"><span data-stu-id="7d901-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="7d901-119">Weitere Informationen finden Sie unter[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="7d901-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d901-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7d901-120">See Also</span></span>

[<span data-ttu-id="7d901-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="7d901-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)