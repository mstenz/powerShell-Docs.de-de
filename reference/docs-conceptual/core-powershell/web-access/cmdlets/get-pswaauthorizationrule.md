---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Abrufen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 003195457660a18b9bbed065181b6d8c23835348
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="055cc-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="055cc-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="055cc-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="055cc-104">SYNOPSIS</span></span>

<span data-ttu-id="055cc-105">Gibt einen Satz von Windows PowerShell® Web Access-Autorisierungsregeln zurück.</span><span class="sxs-lookup"><span data-stu-id="055cc-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="055cc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="055cc-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="055cc-107">ID</span><span class="sxs-lookup"><span data-stu-id="055cc-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="055cc-108">Name</span><span class="sxs-lookup"><span data-stu-id="055cc-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="055cc-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="055cc-109">DESCRIPTION</span></span>

<span data-ttu-id="055cc-110">Das Cmdlet **Get-PswaAuthorizationRule** gibt einen Satz von Windows PowerShell® Web Access-Autorisierungsregeln zurück.</span><span class="sxs-lookup"><span data-stu-id="055cc-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="055cc-111">Wenn weder der **Id**-Parameter noch der **RuleName**-Parameter angegeben ist, listet dieses Cmdlet alle Regeln auf.</span><span class="sxs-lookup"><span data-stu-id="055cc-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="055cc-112">Der **Id**-Parameter kann zum Filtern der Ergebnisse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="055cc-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="055cc-113">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="055cc-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="055cc-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="055cc-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="055cc-115">Gibt die Bezeichner (IDs) der Regeln an, die dieses Cmdlet erhalten soll.</span><span class="sxs-lookup"><span data-stu-id="055cc-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="055cc-116">Wenn keine IDs angegeben werden, gibt dieses Cmdlet alle Autorisierungsregeln zurück.</span><span class="sxs-lookup"><span data-stu-id="055cc-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="055cc-117">Aliase</span><span class="sxs-lookup"><span data-stu-id="055cc-117">Aliases</span></span>                              | <span data-ttu-id="055cc-118">keine</span><span class="sxs-lookup"><span data-stu-id="055cc-118">none</span></span>                                 |
| <span data-ttu-id="055cc-119">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="055cc-119">Required?</span></span>                            | <span data-ttu-id="055cc-120">falsch</span><span class="sxs-lookup"><span data-stu-id="055cc-120">false</span></span>                                |
| <span data-ttu-id="055cc-121">Position?</span><span class="sxs-lookup"><span data-stu-id="055cc-121">Position?</span></span>                            | <span data-ttu-id="055cc-122">2</span><span class="sxs-lookup"><span data-stu-id="055cc-122">2</span></span>                                    |
| <span data-ttu-id="055cc-123">Standardwert</span><span class="sxs-lookup"><span data-stu-id="055cc-123">Default Value</span></span>                        | <span data-ttu-id="055cc-124">keine</span><span class="sxs-lookup"><span data-stu-id="055cc-124">none</span></span>                                 |
| <span data-ttu-id="055cc-125">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="055cc-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="055cc-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="055cc-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="055cc-127">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="055cc-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="055cc-128">falsch</span><span class="sxs-lookup"><span data-stu-id="055cc-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="055cc-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="055cc-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="055cc-130">Gibt die Namen der abzurufenden Autorisierungsregeln an.</span><span class="sxs-lookup"><span data-stu-id="055cc-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="055cc-131">Dieser Parameter gibt alle Regeln zurück, die exakt mit den Regelnamen der Zeichenfolgen in diesem Array übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="055cc-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="055cc-132">Aliase</span><span class="sxs-lookup"><span data-stu-id="055cc-132">Aliases</span></span>                              | <span data-ttu-id="055cc-133">keine</span><span class="sxs-lookup"><span data-stu-id="055cc-133">none</span></span>                                 |
| <span data-ttu-id="055cc-134">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="055cc-134">Required?</span></span>                            | <span data-ttu-id="055cc-135">wahr</span><span class="sxs-lookup"><span data-stu-id="055cc-135">true</span></span>                                 |
| <span data-ttu-id="055cc-136">Position?</span><span class="sxs-lookup"><span data-stu-id="055cc-136">Position?</span></span>                            | <span data-ttu-id="055cc-137">2</span><span class="sxs-lookup"><span data-stu-id="055cc-137">2</span></span>                                    |
| <span data-ttu-id="055cc-138">Standardwert</span><span class="sxs-lookup"><span data-stu-id="055cc-138">Default Value</span></span>                        | <span data-ttu-id="055cc-139">keine</span><span class="sxs-lookup"><span data-stu-id="055cc-139">none</span></span>                                 |
| <span data-ttu-id="055cc-140">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="055cc-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="055cc-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="055cc-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="055cc-142">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="055cc-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="055cc-143">falsch</span><span class="sxs-lookup"><span data-stu-id="055cc-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="055cc-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="055cc-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="055cc-145">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="055cc-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="055cc-146">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="055cc-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="055cc-147">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="055cc-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="055cc-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="055cc-148">int\[\]</span></span>

<span data-ttu-id="055cc-149">Dieses Cmdlet akzeptiert ein Array von Ganzzahlen oder ein Array von Zeichenfolgenwerten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="055cc-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="055cc-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="055cc-150">String\[\]</span></span>

<span data-ttu-id="055cc-151">Dieses Cmdlet akzeptiert ein Array von Ganzzahlen oder ein Array von Zeichenfolgenwerten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="055cc-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="055cc-152">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="055cc-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="055cc-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="055cc-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="055cc-154">Dieses Cmdlet erstellt ein „PswaAuthorizationRule“ als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="055cc-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="055cc-155">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="055cc-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="055cc-156">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="055cc-156">EXAMPLE 1</span></span>

<span data-ttu-id="055cc-157">In diesem Beispiel werden alle Regeln abgerufen.</span><span class="sxs-lookup"><span data-stu-id="055cc-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="055cc-158">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="055cc-158">EXAMPLE 2</span></span>

<span data-ttu-id="055cc-159">In diesem Beispiel wird eine Regel mit der ID *2* erstellt.</span><span class="sxs-lookup"><span data-stu-id="055cc-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="055cc-160">BEISPIEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="055cc-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="055cc-161">In diesem Beispiel wird veranschaulicht, wie das Cmdlet einen Wert aus der Pipeline akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="055cc-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="055cc-162">In diesem Cmdlet werden eine Regel-ID und ein Regelname übergeben.</span><span class="sxs-lookup"><span data-stu-id="055cc-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="055cc-163">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="055cc-163">Related topics</span></span>

- [<span data-ttu-id="055cc-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="055cc-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="055cc-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="055cc-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="055cc-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="055cc-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="055cc-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="055cc-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
