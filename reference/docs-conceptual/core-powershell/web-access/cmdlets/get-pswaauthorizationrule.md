---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Abrufen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 43997320ec7ab779b2061a0af88f97db0b7e93d6
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2017
---
#  <a name="get-pswaauthorizationrule"></a><span data-ttu-id="315a1-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="315a1-103">Get-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="315a1-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="315a1-104">SYNOPSIS</span></span>

<span data-ttu-id="315a1-105">Gibt einen Satz von Windows PowerShell® Web Access-Autorisierungsregeln zurück.</span><span class="sxs-lookup"><span data-stu-id="315a1-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

##  <a name="syntax"></a><span data-ttu-id="315a1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="315a1-106">Syntax</span></span>

###  <a name="id"></a><span data-ttu-id="315a1-107">ID</span><span class="sxs-lookup"><span data-stu-id="315a1-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

###  <a name="name"></a><span data-ttu-id="315a1-108">Name</span><span class="sxs-lookup"><span data-stu-id="315a1-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="315a1-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="315a1-109">DESCRIPTION</span></span>

<span data-ttu-id="315a1-110">Das Cmdlet **Get-PswaAuthorizationRule** gibt einen Satz von Windows PowerShell® Web Access-Autorisierungsregeln zurück.</span><span class="sxs-lookup"><span data-stu-id="315a1-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="315a1-111">Wenn weder der **Id**-Parameter noch der **RuleName**-Parameter angegeben ist, listet dieses Cmdlet alle Regeln auf.</span><span class="sxs-lookup"><span data-stu-id="315a1-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="315a1-112">Der **Id**-Parameter kann zum Filtern der Ergebnisse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="315a1-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="315a1-113">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="315a1-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="315a1-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="315a1-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="315a1-115">Gibt die Bezeichner (IDs) der Regeln an, die dieses Cmdlet erhalten soll.</span><span class="sxs-lookup"><span data-stu-id="315a1-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="315a1-116">Wenn keine IDs angegeben werden, gibt dieses Cmdlet alle Autorisierungsregeln zurück.</span><span class="sxs-lookup"><span data-stu-id="315a1-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="315a1-117">Aliase</span><span class="sxs-lookup"><span data-stu-id="315a1-117">Aliases</span></span>                              | <span data-ttu-id="315a1-118">keine</span><span class="sxs-lookup"><span data-stu-id="315a1-118">none</span></span>                                 |
| <span data-ttu-id="315a1-119">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="315a1-119">Required?</span></span>                            | <span data-ttu-id="315a1-120">falsch</span><span class="sxs-lookup"><span data-stu-id="315a1-120">false</span></span>                                |
| <span data-ttu-id="315a1-121">Position?</span><span class="sxs-lookup"><span data-stu-id="315a1-121">Position?</span></span>                            | <span data-ttu-id="315a1-122">2</span><span class="sxs-lookup"><span data-stu-id="315a1-122">2</span></span>                                    |
| <span data-ttu-id="315a1-123">Standardwert</span><span class="sxs-lookup"><span data-stu-id="315a1-123">Default Value</span></span>                        | <span data-ttu-id="315a1-124">keine</span><span class="sxs-lookup"><span data-stu-id="315a1-124">none</span></span>                                 |
| <span data-ttu-id="315a1-125">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="315a1-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="315a1-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="315a1-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="315a1-127">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="315a1-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="315a1-128">falsch</span><span class="sxs-lookup"><span data-stu-id="315a1-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="315a1-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="315a1-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="315a1-130">Gibt die Namen der abzurufenden Autorisierungsregeln an.</span><span class="sxs-lookup"><span data-stu-id="315a1-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="315a1-131">Dieser Parameter gibt alle Regeln zurück, die exakt mit den Regelnamen der Zeichenfolgen in diesem Array übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="315a1-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="315a1-132">Aliase</span><span class="sxs-lookup"><span data-stu-id="315a1-132">Aliases</span></span>                              | <span data-ttu-id="315a1-133">keine</span><span class="sxs-lookup"><span data-stu-id="315a1-133">none</span></span>                                 |
| <span data-ttu-id="315a1-134">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="315a1-134">Required?</span></span>                            | <span data-ttu-id="315a1-135">wahr</span><span class="sxs-lookup"><span data-stu-id="315a1-135">true</span></span>                                 |
| <span data-ttu-id="315a1-136">Position?</span><span class="sxs-lookup"><span data-stu-id="315a1-136">Position?</span></span>                            | <span data-ttu-id="315a1-137">2</span><span class="sxs-lookup"><span data-stu-id="315a1-137">2</span></span>                                    |
| <span data-ttu-id="315a1-138">Standardwert</span><span class="sxs-lookup"><span data-stu-id="315a1-138">Default Value</span></span>                        | <span data-ttu-id="315a1-139">keine</span><span class="sxs-lookup"><span data-stu-id="315a1-139">none</span></span>                                 |
| <span data-ttu-id="315a1-140">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="315a1-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="315a1-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="315a1-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="315a1-142">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="315a1-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="315a1-143">falsch</span><span class="sxs-lookup"><span data-stu-id="315a1-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="315a1-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="315a1-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="315a1-145">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="315a1-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="315a1-146">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="315a1-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="315a1-147">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="315a1-147">INPUTS</span></span>

###  <a name="int"></a><span data-ttu-id="315a1-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="315a1-148">int\[\]</span></span>

<span data-ttu-id="315a1-149">Dieses Cmdlet akzeptiert ein Array von Ganzzahlen oder ein Array von Zeichenfolgenwerten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="315a1-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

###  <a name="string"></a><span data-ttu-id="315a1-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="315a1-150">String\[\]</span></span>

<span data-ttu-id="315a1-151">Dieses Cmdlet akzeptiert ein Array von Ganzzahlen oder ein Array von Zeichenfolgenwerten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="315a1-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="315a1-152">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="315a1-152">OUTPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="315a1-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="315a1-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="315a1-154">Dieses Cmdlet erstellt ein „PswaAuthorizationRule“ als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="315a1-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="315a1-155">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="315a1-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="315a1-156">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="315a1-156">EXAMPLE 1</span></span>

<span data-ttu-id="315a1-157">In diesem Beispiel werden alle Regeln abgerufen.</span><span class="sxs-lookup"><span data-stu-id="315a1-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="315a1-158">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="315a1-158">EXAMPLE 2</span></span>

<span data-ttu-id="315a1-159">In diesem Beispiel wird eine Regel mit der ID *2* erstellt.</span><span class="sxs-lookup"><span data-stu-id="315a1-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="315a1-160">BEISPIEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="315a1-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="315a1-161">In diesem Beispiel wird veranschaulicht, wie das Cmdlet einen Wert aus der Pipeline akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="315a1-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="315a1-162">In diesem Cmdlet werden eine Regel-ID und ein Regelname übergeben.</span><span class="sxs-lookup"><span data-stu-id="315a1-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

##  <a name="related-topics"></a><span data-ttu-id="315a1-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="315a1-163">Related topics</span></span>

-  [<span data-ttu-id="315a1-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="315a1-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="315a1-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="315a1-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
-  [<span data-ttu-id="315a1-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="315a1-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
-  [<span data-ttu-id="315a1-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="315a1-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
