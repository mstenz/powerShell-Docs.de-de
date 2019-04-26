---
title: Geben Sie Filterparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067687"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="a6219-102">Eingabe von Filterparametern</span><span class="sxs-lookup"><span data-stu-id="a6219-102">Input Filter Parameters</span></span>

<span data-ttu-id="a6219-103">Ein Cmdlet definieren `Filter`, `Include`, und `Exclude` Parameter, die den Satz von Eingabeobjekten zu filtern, die das Cmdlet wirkt sich auf.</span><span class="sxs-lookup"><span data-stu-id="a6219-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="a6219-104">In der Regel wird der Satz von Eingabeobjekten angegeben, indem ein `InputObject`, `Path`, oder `Name` Parameter.</span><span class="sxs-lookup"><span data-stu-id="a6219-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="a6219-105">Beispielsweise kann ein Cmdlet haben eine `Path` Parameter, der mehreren Pfaden akzeptiert wird, mithilfe von Platzhalterzeichen und jeder Pfad verweist auf ein Eingabeobjekt.</span><span class="sxs-lookup"><span data-stu-id="a6219-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="a6219-106">Zusammen verwendet, die `Filter`, `Include`, und `Exclude` weitere Parameter qualifizieren Sie die Pfade, die das Cmdlet funktioniert in jedem Aufruf erfolgte.</span><span class="sxs-lookup"><span data-stu-id="a6219-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="a6219-107">Einschließen und Ausschließen von Parametern</span><span class="sxs-lookup"><span data-stu-id="a6219-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="a6219-108">Die `Include` und `Exclude` Parameter zu identifizieren, die Objekte, die aufgenommen werden oder nicht aus dem Satz von Eingabeobjekten an das Cmdlet übergeben.</span><span class="sxs-lookup"><span data-stu-id="a6219-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="a6219-109">Verwenden Sie diese Parameter aus, wenn der Filter in der standard-Platzhalter-Sprache ausgedrückt werden kann.</span><span class="sxs-lookup"><span data-stu-id="a6219-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="a6219-110">(Weitere Informationen zu Platzhalterzeichen finden Sie unter [unterstützen Platzhalter in der Cmdlet-Parameter](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Die `Include` Parameter enthält alle Objekte, deren Namen den Filter einschließen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="a6219-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="a6219-111">Die `Exclude` Parameter schließt alle Objekte, deren Namen mit den Filter übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="a6219-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="a6219-112">Filter-Parameter</span><span class="sxs-lookup"><span data-stu-id="a6219-112">Filter Parameter</span></span>

<span data-ttu-id="a6219-113">Die `Filter` Parameter gibt einen Filter, der nicht ausgedrückt wird, in der standard-Platzhalter-Sprache.</span><span class="sxs-lookup"><span data-stu-id="a6219-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="a6219-114">Z. B. für die Active Directory Service Interfaces (ADSI) oder SQL-Filter übergeben werden können, an das Cmdlet über die `Filter` Parameter.</span><span class="sxs-lookup"><span data-stu-id="a6219-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="a6219-115">In den Cmdlets, die von Windows PowerShell bereitgestellt wird werden diese Filter durch die Windows PowerShell-Anbieter angegeben, die mit dem-Cmdlet zu verwenden, um einen Datenspeicher zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a6219-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="a6219-116">Jeder Anbieter definiert in der Regel einen eigenen Filter.</span><span class="sxs-lookup"><span data-stu-id="a6219-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="a6219-117">Filtern, wenn kein Satz von Eingabeobjekten des Typs angegeben wird</span><span class="sxs-lookup"><span data-stu-id="a6219-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="a6219-118">Wenn kein Satz von Eingabeobjekten des Typs angegeben wird, bedeutet dies in der Regel für alle Objekte zu filtern.</span><span class="sxs-lookup"><span data-stu-id="a6219-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="a6219-119">Weitere Informationen finden Sie unter[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="a6219-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6219-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a6219-120">See Also</span></span>

[<span data-ttu-id="a6219-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a6219-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)