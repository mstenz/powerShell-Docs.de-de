---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Entfernen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="de1b6-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="de1b6-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="de1b6-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="de1b6-104">SYNOPSIS</span></span>

<span data-ttu-id="de1b6-105">Entfernt eine angegebene Autorisierungsregel aus Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="de1b6-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="de1b6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de1b6-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="de1b6-107">Id</span><span class="sxs-lookup"><span data-stu-id="de1b6-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="de1b6-108">Regel</span><span class="sxs-lookup"><span data-stu-id="de1b6-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="de1b6-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="de1b6-109">DESCRIPTION</span></span>

<span data-ttu-id="de1b6-110">Entfernt eine angegebene Autorisierungsregel aus Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="de1b6-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="de1b6-111">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="de1b6-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="de1b6-112">-Force</span><span class="sxs-lookup"><span data-stu-id="de1b6-112">-Force</span></span>

<span data-ttu-id="de1b6-113">Führt das Cmdlet aus, ohne zur Bestätigung aufzufordern.</span><span class="sxs-lookup"><span data-stu-id="de1b6-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="de1b6-114">Das Cmdlet fordert standardmäßig eine Bestätigung, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="de1b6-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="de1b6-115">Aliase</span><span class="sxs-lookup"><span data-stu-id="de1b6-115">Aliases</span></span>                              | <span data-ttu-id="de1b6-116">keine</span><span class="sxs-lookup"><span data-stu-id="de1b6-116">none</span></span>                                 |
| <span data-ttu-id="de1b6-117">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="de1b6-117">Required?</span></span>                            | <span data-ttu-id="de1b6-118">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-118">false</span></span>                                |
| <span data-ttu-id="de1b6-119">Position?</span><span class="sxs-lookup"><span data-stu-id="de1b6-119">Position?</span></span>                            | <span data-ttu-id="de1b6-120">benannt</span><span class="sxs-lookup"><span data-stu-id="de1b6-120">named</span></span>                                |
| <span data-ttu-id="de1b6-121">Standardwert</span><span class="sxs-lookup"><span data-stu-id="de1b6-121">Default Value</span></span>                        | <span data-ttu-id="de1b6-122">keine</span><span class="sxs-lookup"><span data-stu-id="de1b6-122">none</span></span>                                 |
| <span data-ttu-id="de1b6-123">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="de1b6-124">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-124">false</span></span>                                |
| <span data-ttu-id="de1b6-125">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="de1b6-126">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="de1b6-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="de1b6-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="de1b6-128">Gibt den Bezeichner (ID) von einer oder mehrerer Regeln an, die entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="de1b6-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="de1b6-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="de1b6-129">Aliases</span></span>                              | <span data-ttu-id="de1b6-130">keine</span><span class="sxs-lookup"><span data-stu-id="de1b6-130">none</span></span>                                 |
| <span data-ttu-id="de1b6-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="de1b6-131">Required?</span></span>                            | <span data-ttu-id="de1b6-132">wahr</span><span class="sxs-lookup"><span data-stu-id="de1b6-132">true</span></span>                                 |
| <span data-ttu-id="de1b6-133">Position?</span><span class="sxs-lookup"><span data-stu-id="de1b6-133">Position?</span></span>                            | <span data-ttu-id="de1b6-134">2</span><span class="sxs-lookup"><span data-stu-id="de1b6-134">2</span></span>                                    |
| <span data-ttu-id="de1b6-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="de1b6-135">Default Value</span></span>                        | <span data-ttu-id="de1b6-136">keine</span><span class="sxs-lookup"><span data-stu-id="de1b6-136">none</span></span>                                 |
| <span data-ttu-id="de1b6-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="de1b6-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="de1b6-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="de1b6-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="de1b6-140">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="de1b6-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="de1b6-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="de1b6-142">Gibt die zu entfernenden Regeln an.</span><span class="sxs-lookup"><span data-stu-id="de1b6-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="de1b6-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="de1b6-143">Aliases</span></span>                              | <span data-ttu-id="de1b6-144">keine</span><span class="sxs-lookup"><span data-stu-id="de1b6-144">none</span></span>                                 |
| <span data-ttu-id="de1b6-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="de1b6-145">Required?</span></span>                            | <span data-ttu-id="de1b6-146">wahr</span><span class="sxs-lookup"><span data-stu-id="de1b6-146">true</span></span>                                 |
| <span data-ttu-id="de1b6-147">Position?</span><span class="sxs-lookup"><span data-stu-id="de1b6-147">Position?</span></span>                            | <span data-ttu-id="de1b6-148">2</span><span class="sxs-lookup"><span data-stu-id="de1b6-148">2</span></span>                                    |
| <span data-ttu-id="de1b6-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="de1b6-149">Default Value</span></span>                        | <span data-ttu-id="de1b6-150">keine</span><span class="sxs-lookup"><span data-stu-id="de1b6-150">none</span></span>                                 |
| <span data-ttu-id="de1b6-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="de1b6-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="de1b6-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="de1b6-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="de1b6-154">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="de1b6-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="de1b6-155">-Confirm</span></span>

<span data-ttu-id="de1b6-156">Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="de1b6-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="de1b6-157">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="de1b6-157">Required?</span></span>                            | <span data-ttu-id="de1b6-158">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-158">false</span></span>                                |
| <span data-ttu-id="de1b6-159">Position?</span><span class="sxs-lookup"><span data-stu-id="de1b6-159">Position?</span></span>                            | <span data-ttu-id="de1b6-160">benannt</span><span class="sxs-lookup"><span data-stu-id="de1b6-160">named</span></span>                                |
| <span data-ttu-id="de1b6-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="de1b6-161">Default Value</span></span>                        | <span data-ttu-id="de1b6-162">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-162">false</span></span>                                |
| <span data-ttu-id="de1b6-163">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="de1b6-164">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-164">false</span></span>                                |
| <span data-ttu-id="de1b6-165">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="de1b6-166">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="de1b6-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="de1b6-167">-WhatIf</span></span>

<span data-ttu-id="de1b6-168">Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="de1b6-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="de1b6-169">Das Cmdlet wird nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="de1b6-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="de1b6-170">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="de1b6-170">Required?</span></span>                            | <span data-ttu-id="de1b6-171">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-171">false</span></span>                                |
| <span data-ttu-id="de1b6-172">Position?</span><span class="sxs-lookup"><span data-stu-id="de1b6-172">Position?</span></span>                            | <span data-ttu-id="de1b6-173">benannt</span><span class="sxs-lookup"><span data-stu-id="de1b6-173">named</span></span>                                |
| <span data-ttu-id="de1b6-174">Standardwert</span><span class="sxs-lookup"><span data-stu-id="de1b6-174">Default Value</span></span>                        | <span data-ttu-id="de1b6-175">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-175">false</span></span>                                |
| <span data-ttu-id="de1b6-176">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="de1b6-177">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-177">false</span></span>                                |
| <span data-ttu-id="de1b6-178">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="de1b6-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="de1b6-179">falsch</span><span class="sxs-lookup"><span data-stu-id="de1b6-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="de1b6-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="de1b6-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="de1b6-181">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="de1b6-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="de1b6-182">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="de1b6-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="de1b6-183">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="de1b6-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="de1b6-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="de1b6-184">int\[\]</span></span>

<span data-ttu-id="de1b6-185">Dieses Cmdlet akzeptiert ein Array aus Ganzzahlen oder ein Array aus „PswaAuthorizationRule“-Objekten.</span><span class="sxs-lookup"><span data-stu-id="de1b6-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="de1b6-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="de1b6-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="de1b6-187">Dieses Cmdlet akzeptiert ein Array aus Ganzzahlen oder ein Array aus „PswaAuthorizationRule“-Objekten.</span><span class="sxs-lookup"><span data-stu-id="de1b6-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="de1b6-188">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="de1b6-188">OUTPUTS</span></span>

<span data-ttu-id="de1b6-189">Dieses Cmdlet erzeugt keine Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="de1b6-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="de1b6-190">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="de1b6-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="de1b6-191">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="de1b6-191">EXAMPLE 1</span></span>

<span data-ttu-id="de1b6-192">In diesem Beispiel wird die Autorisierungsregel mit der ID *2* entfernt.</span><span class="sxs-lookup"><span data-stu-id="de1b6-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="de1b6-193">BEISPIEL 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="de1b6-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="de1b6-194">In diesem Beispiel werden alle Autorisierungsregel entfernt, außerdem ist die Bestätigung durch den Benutzer erforderlich.</span><span class="sxs-lookup"><span data-stu-id="de1b6-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="de1b6-195">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="de1b6-195">Related topics</span></span>

- [<span data-ttu-id="de1b6-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="de1b6-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="de1b6-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="de1b6-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="de1b6-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="de1b6-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="de1b6-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="de1b6-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
