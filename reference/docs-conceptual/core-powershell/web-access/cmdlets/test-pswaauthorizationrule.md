---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Testen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 1b480b68c7ce2064f42281d8c5d76156a39e0222
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2017
---
#  <a name="test-pswaauthorizationrule"></a><span data-ttu-id="16588-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="16588-103">Test-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="16588-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="16588-104">SYNOPSIS</span></span>

<span data-ttu-id="16588-105">Überprüft, ob eine Regel für einen angegebenen Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="16588-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="16588-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="16588-106">SYNTAX</span></span>

###  <a name="computername"></a><span data-ttu-id="16588-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="16588-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

###  <a name="connectionuri"></a><span data-ttu-id="16588-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="16588-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="16588-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="16588-109">DESCRIPTION</span></span>

<span data-ttu-id="16588-110">Das Cmdlet **Test-PswaAuthorizationRule** überprüft, ob eine Regel für einen bestimmten Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="16588-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="16588-111">Dieses Cmdlet kann auch zum Testen von Autorisierungsregeln verwendet werden, um zu überprüfen, ob die Zugriffsanforderung eines bestimmten Benutzers, Computers oder Endpunkts autorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="16588-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="16588-112">Dieses Cmdlet wertet standardmäßig alle Regeln in der Autorisierungsdatei aus.</span><span class="sxs-lookup"><span data-stu-id="16588-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="16588-113">Sie können jedoch eine Teilmenge von zu testenden Regeln angeben.</span><span class="sxs-lookup"><span data-stu-id="16588-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="16588-114">Sie können dieses Cmdlet für die Problembehandlung von Authentifizierungsfehlern verwenden.</span><span class="sxs-lookup"><span data-stu-id="16588-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="16588-115">Die Parameter dieses Cmdlets entsprechen den Feldern auf der Windows PowerShell® Web Access-Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="16588-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="16588-116">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="16588-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="16588-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="16588-118">Gibt den Namen des zu testenden Computers an.</span><span class="sxs-lookup"><span data-stu-id="16588-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="16588-119">Aliase</span><span class="sxs-lookup"><span data-stu-id="16588-119">Aliases</span></span>                              | <span data-ttu-id="16588-120">keine</span><span class="sxs-lookup"><span data-stu-id="16588-120">none</span></span>                                 |
| <span data-ttu-id="16588-121">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="16588-121">Required?</span></span>                            | <span data-ttu-id="16588-122">wahr</span><span class="sxs-lookup"><span data-stu-id="16588-122">true</span></span>                                 |
| <span data-ttu-id="16588-123">Position?</span><span class="sxs-lookup"><span data-stu-id="16588-123">Position?</span></span>                            | <span data-ttu-id="16588-124">2</span><span class="sxs-lookup"><span data-stu-id="16588-124">2</span></span>                                    |
| <span data-ttu-id="16588-125">Standardwert</span><span class="sxs-lookup"><span data-stu-id="16588-125">Default Value</span></span>                        | <span data-ttu-id="16588-126">keine</span><span class="sxs-lookup"><span data-stu-id="16588-126">none</span></span>                                 |
| <span data-ttu-id="16588-127">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="16588-128">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-128">false</span></span>                                |
| <span data-ttu-id="16588-129">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="16588-130">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="16588-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="16588-132">Gibt den Namen einer zu testenden Windows PowerShell-Sitzungskonfiguration (auch als Endpunkt oder Runspaces bezeichnet) an.</span><span class="sxs-lookup"><span data-stu-id="16588-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="16588-133">Aliase</span><span class="sxs-lookup"><span data-stu-id="16588-133">Aliases</span></span>                              | <span data-ttu-id="16588-134">keine</span><span class="sxs-lookup"><span data-stu-id="16588-134">none</span></span>                                 |
| <span data-ttu-id="16588-135">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="16588-135">Required?</span></span>                            | <span data-ttu-id="16588-136">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-136">false</span></span>                                |
| <span data-ttu-id="16588-137">Position?</span><span class="sxs-lookup"><span data-stu-id="16588-137">Position?</span></span>                            | <span data-ttu-id="16588-138">3</span><span class="sxs-lookup"><span data-stu-id="16588-138">3</span></span>                                    |
| <span data-ttu-id="16588-139">Standardwert</span><span class="sxs-lookup"><span data-stu-id="16588-139">Default Value</span></span>                        | <span data-ttu-id="16588-140">keine</span><span class="sxs-lookup"><span data-stu-id="16588-140">none</span></span>                                 |
| <span data-ttu-id="16588-141">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="16588-142">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-142">false</span></span>                                |
| <span data-ttu-id="16588-143">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="16588-144">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="16588-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="16588-146">Gibt die zu testende Verbindungs-URI an.</span><span class="sxs-lookup"><span data-stu-id="16588-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="16588-147">Aliase</span><span class="sxs-lookup"><span data-stu-id="16588-147">Aliases</span></span>                              | <span data-ttu-id="16588-148">keine</span><span class="sxs-lookup"><span data-stu-id="16588-148">none</span></span>                                 |
| <span data-ttu-id="16588-149">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="16588-149">Required?</span></span>                            | <span data-ttu-id="16588-150">wahr</span><span class="sxs-lookup"><span data-stu-id="16588-150">true</span></span>                                 |
| <span data-ttu-id="16588-151">Position?</span><span class="sxs-lookup"><span data-stu-id="16588-151">Position?</span></span>                            | <span data-ttu-id="16588-152">2</span><span class="sxs-lookup"><span data-stu-id="16588-152">2</span></span>                                    |
| <span data-ttu-id="16588-153">Standardwert</span><span class="sxs-lookup"><span data-stu-id="16588-153">Default Value</span></span>                        | <span data-ttu-id="16588-154">keine</span><span class="sxs-lookup"><span data-stu-id="16588-154">none</span></span>                                 |
| <span data-ttu-id="16588-155">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="16588-156">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-156">false</span></span>                                |
| <span data-ttu-id="16588-157">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="16588-158">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="16588-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="16588-160">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Testen der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="16588-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="16588-161">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="16588-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="16588-162">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Testen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) aus.</span><span class="sxs-lookup"><span data-stu-id="16588-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="16588-163">Aliase</span><span class="sxs-lookup"><span data-stu-id="16588-163">Aliases</span></span>                              | <span data-ttu-id="16588-164">keine</span><span class="sxs-lookup"><span data-stu-id="16588-164">none</span></span>                                 |
| <span data-ttu-id="16588-165">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="16588-165">Required?</span></span>                            | <span data-ttu-id="16588-166">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-166">false</span></span>                                |
| <span data-ttu-id="16588-167">Position?</span><span class="sxs-lookup"><span data-stu-id="16588-167">Position?</span></span>                            | <span data-ttu-id="16588-168">benannt</span><span class="sxs-lookup"><span data-stu-id="16588-168">named</span></span>                                |
| <span data-ttu-id="16588-169">Standardwert</span><span class="sxs-lookup"><span data-stu-id="16588-169">Default Value</span></span>                        | <span data-ttu-id="16588-170">keine</span><span class="sxs-lookup"><span data-stu-id="16588-170">none</span></span>                                 |
| <span data-ttu-id="16588-171">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="16588-172">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-172">false</span></span>                                |
| <span data-ttu-id="16588-173">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="16588-174">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="16588-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="16588-176">Gibt eine Teilmenge der zu testenden Regeln an.</span><span class="sxs-lookup"><span data-stu-id="16588-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="16588-177">Wenn dieser Parameter nicht angegeben ist, testet dieses Cmdlet alle Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="16588-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="16588-178">Aliase</span><span class="sxs-lookup"><span data-stu-id="16588-178">Aliases</span></span>                              | <span data-ttu-id="16588-179">keine</span><span class="sxs-lookup"><span data-stu-id="16588-179">none</span></span>                                 |
| <span data-ttu-id="16588-180">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="16588-180">Required?</span></span>                            | <span data-ttu-id="16588-181">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-181">false</span></span>                                |
| <span data-ttu-id="16588-182">Position?</span><span class="sxs-lookup"><span data-stu-id="16588-182">Position?</span></span>                            | <span data-ttu-id="16588-183">benannt</span><span class="sxs-lookup"><span data-stu-id="16588-183">named</span></span>                                |
| <span data-ttu-id="16588-184">Standardwert</span><span class="sxs-lookup"><span data-stu-id="16588-184">Default Value</span></span>                        | <span data-ttu-id="16588-185">keine</span><span class="sxs-lookup"><span data-stu-id="16588-185">none</span></span>                                 |
| <span data-ttu-id="16588-186">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="16588-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="16588-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="16588-188">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="16588-189">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="16588-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="16588-191">Gibt den Namen des zu testenden Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="16588-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="16588-192">Aliase</span><span class="sxs-lookup"><span data-stu-id="16588-192">Aliases</span></span>                              | <span data-ttu-id="16588-193">keine</span><span class="sxs-lookup"><span data-stu-id="16588-193">none</span></span>                                 |
| <span data-ttu-id="16588-194">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="16588-194">Required?</span></span>                            | <span data-ttu-id="16588-195">wahr</span><span class="sxs-lookup"><span data-stu-id="16588-195">true</span></span>                                 |
| <span data-ttu-id="16588-196">Position?</span><span class="sxs-lookup"><span data-stu-id="16588-196">Position?</span></span>                            | <span data-ttu-id="16588-197">1</span><span class="sxs-lookup"><span data-stu-id="16588-197">1</span></span>                                    |
| <span data-ttu-id="16588-198">Standardwert</span><span class="sxs-lookup"><span data-stu-id="16588-198">Default Value</span></span>                        | <span data-ttu-id="16588-199">keine</span><span class="sxs-lookup"><span data-stu-id="16588-199">none</span></span>                                 |
| <span data-ttu-id="16588-200">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="16588-201">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-201">false</span></span>                                |
| <span data-ttu-id="16588-202">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="16588-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="16588-203">falsch</span><span class="sxs-lookup"><span data-stu-id="16588-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="16588-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="16588-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="16588-205">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="16588-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="16588-206">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="16588-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="16588-207">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="16588-207">INPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="16588-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="16588-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="16588-209">Dieses Cmdlet akzeptiert ein Array von „PswaAuthorizationRule“-Objekten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="16588-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="16588-210">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="16588-210">OUTPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="16588-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="16588-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="16588-212">Dieses Cmdlet stellt ein Array von „PswaAuthorizationRule“-Objekten als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="16588-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="16588-213">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="16588-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="16588-214">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="16588-214">EXAMPLE 1</span></span>

<span data-ttu-id="16588-215">In diesem Beispiel werden alle Autorisierungsregeln getestet, um alle Regeln anzuzeigen, die es dem Benutzer *contoso\\mhanson* ermöglichen, sich mit dem Computer *srv2* zu verbinden und eine Windows PowerShell-Sitzungskonfiguration namens *Test* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="16588-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="16588-216">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="16588-216">EXAMPLE 2</span></span>

<span data-ttu-id="16588-217">In diesem Beispiel werden alle Autorisierungsregeln getestet, um zu überprüfen, welche davon für den Benutzer *contoso\\mhanson* gelten.</span><span class="sxs-lookup"><span data-stu-id="16588-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

##  <a name="related-topics"></a><span data-ttu-id="16588-218">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="16588-218">Related topics</span></span>

-  [<span data-ttu-id="16588-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="16588-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="16588-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="16588-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="16588-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="16588-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="16588-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="16588-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
