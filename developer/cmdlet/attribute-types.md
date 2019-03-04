---
title: Attributtypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863806"
---
# <a name="attribute-types"></a><span data-ttu-id="be44c-102">Attributtypen</span><span class="sxs-lookup"><span data-stu-id="be44c-102">Attribute Types</span></span>

<span data-ttu-id="be44c-103">Cmdlet-Attribute können nach Funktionalität gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="be44c-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="be44c-104">Die folgenden Abschnitte beschreiben die verfügbaren Attribute und beschreiben, was das Laufzeitmodul erledigt, wenn das Attribut aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="be44c-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="be44c-105">Cmdlet-Attribute</span><span class="sxs-lookup"><span data-stu-id="be44c-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="be44c-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="be44c-106">Cmdlet</span></span>

<span data-ttu-id="be44c-107">Identifiziert eine .NET Framework-Klasse als ein Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be44c-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="be44c-108">Dies ist das erforderliche base-Attribut.</span><span class="sxs-lookup"><span data-stu-id="be44c-108">This is the required base attribute.</span></span>
<span data-ttu-id="be44c-109">Weitere Informationen finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="be44c-110">Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="be44c-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="be44c-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="be44c-111">Parameter</span></span>

<span data-ttu-id="be44c-112">Identifiziert eine öffentliche Eigenschaft in der Cmdlet-Klasse als Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="be44c-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="be44c-113">Weitere Informationen finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="be44c-114">Alias</span><span class="sxs-lookup"><span data-stu-id="be44c-114">Alias</span></span>

<span data-ttu-id="be44c-115">Gibt einen oder mehrere Aliase für einen Parameter an.</span><span class="sxs-lookup"><span data-stu-id="be44c-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="be44c-116">Weitere Informationen finden Sie unter [Alias Attributdeklaration](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="be44c-117">Validierungsattribute Argument</span><span class="sxs-lookup"><span data-stu-id="be44c-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="be44c-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="be44c-118">ValidateCount</span></span>

<span data-ttu-id="be44c-119">Gibt die minimale und maximale Anzahl von Argumenten, die für einen Cmdlet-Parameter zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="be44c-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="be44c-120">Weitere Informationen finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="be44c-121">ValidateLength auf</span><span class="sxs-lookup"><span data-stu-id="be44c-121">ValidateLength</span></span>

<span data-ttu-id="be44c-122">Gibt eine minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter-Argument.</span><span class="sxs-lookup"><span data-stu-id="be44c-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="be44c-123">Weitere Informationen finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="be44c-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="be44c-124">ValidatePattern</span></span>

<span data-ttu-id="be44c-125">Gibt an, das Muster eines regulären Ausdrucks, das das Argument der Cmdlet-Parameter übereinstimmen muss.</span><span class="sxs-lookup"><span data-stu-id="be44c-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="be44c-126">Weitere Informationen finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="be44c-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="be44c-127">ValidateRange</span></span>

<span data-ttu-id="be44c-128">Gibt die minimalen und maximalen Werte für ein Cmdlet-Parameter-Argument.</span><span class="sxs-lookup"><span data-stu-id="be44c-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="be44c-129">Weitere Informationen finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="be44c-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="be44c-130">ValidateSet</span></span>

<span data-ttu-id="be44c-131">Gibt einen Satz gültiger Werte für das Argument der Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="be44c-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="be44c-132">Weitere Informationen finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="be44c-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be44c-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="be44c-133">See Also</span></span>

[<span data-ttu-id="be44c-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="be44c-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
