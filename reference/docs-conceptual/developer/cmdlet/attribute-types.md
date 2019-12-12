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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364579"
---
# <a name="attribute-types"></a><span data-ttu-id="5c416-102">Attributtypen</span><span class="sxs-lookup"><span data-stu-id="5c416-102">Attribute Types</span></span>

<span data-ttu-id="5c416-103">Cmdlet-Attribute können nach Funktionalität gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="5c416-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="5c416-104">In den folgenden Abschnitten werden die verfügbaren Attribute beschrieben, und es wird beschrieben, was die Laufzeit bewirkt, wenn das Attribut aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="5c416-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="5c416-105">Cmdlet-Attribute</span><span class="sxs-lookup"><span data-stu-id="5c416-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="5c416-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5c416-106">Cmdlet</span></span>

<span data-ttu-id="5c416-107">Identifiziert eine .NET Framework Klasse als Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5c416-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="5c416-108">Dies ist das erforderliche Basis Attribut.</span><span class="sxs-lookup"><span data-stu-id="5c416-108">This is the required base attribute.</span></span>
<span data-ttu-id="5c416-109">Weitere Informationen finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="5c416-110">Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="5c416-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="5c416-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="5c416-111">Parameter</span></span>

<span data-ttu-id="5c416-112">Identifiziert eine öffentliche Eigenschaft in der Cmdlet-Klasse als Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="5c416-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="5c416-113">Weitere Informationen finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="5c416-114">Alias</span><span class="sxs-lookup"><span data-stu-id="5c416-114">Alias</span></span>

<span data-ttu-id="5c416-115">Gibt mindestens einen Alias für einen Parameter an.</span><span class="sxs-lookup"><span data-stu-id="5c416-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="5c416-116">Weitere Informationen finden Sie unter [Alias Attribut Deklaration](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="5c416-117">Argument Validierungs Attribute</span><span class="sxs-lookup"><span data-stu-id="5c416-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="5c416-118">Validatecount</span><span class="sxs-lookup"><span data-stu-id="5c416-118">ValidateCount</span></span>

<span data-ttu-id="5c416-119">Gibt die minimale und maximale Anzahl von Argumenten an, die für einen Cmdlet-Parameter zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="5c416-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="5c416-120">Weitere Informationen finden Sie unter [validatecount-Attribut Deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="5c416-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="5c416-121">ValidateLength</span></span>

<span data-ttu-id="5c416-122">Gibt eine minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter Argument an.</span><span class="sxs-lookup"><span data-stu-id="5c416-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="5c416-123">Weitere Informationen finden Sie unter [validateLength-Attribut Deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="5c416-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="5c416-124">ValidatePattern</span></span>

<span data-ttu-id="5c416-125">Gibt ein Muster für einen regulären Ausdruck an, dem das Cmdlet-Parameter Argument entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="5c416-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="5c416-126">Weitere Informationen finden Sie unter [validatepattern-Attribut Deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="5c416-127">Validaterange</span><span class="sxs-lookup"><span data-stu-id="5c416-127">ValidateRange</span></span>

<span data-ttu-id="5c416-128">Gibt die minimalen und maximalen Werte für ein Cmdlet-Parameter Argument an.</span><span class="sxs-lookup"><span data-stu-id="5c416-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="5c416-129">Weitere Informationen finden Sie unter [validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="5c416-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="5c416-130">ValidateSet</span></span>

<span data-ttu-id="5c416-131">Gibt einen Satz gültiger Werte für das Cmdlet-Parameter Argument an.</span><span class="sxs-lookup"><span data-stu-id="5c416-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="5c416-132">Weitere Informationen finden Sie unter [validateset-Attribut Deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5c416-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5c416-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5c416-133">See Also</span></span>

[<span data-ttu-id="5c416-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5c416-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
