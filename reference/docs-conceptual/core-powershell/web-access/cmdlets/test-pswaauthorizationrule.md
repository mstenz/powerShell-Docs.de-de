---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Testen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: fb2937397616160c70b056e412e42fb8ff4c2f27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="b39f9-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b39f9-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="b39f9-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="b39f9-104">SYNOPSIS</span></span>

<span data-ttu-id="b39f9-105">Überprüft, ob eine Regel für einen angegebenen Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b39f9-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="b39f9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b39f9-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="b39f9-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="b39f9-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="b39f9-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="b39f9-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b39f9-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="b39f9-109">DESCRIPTION</span></span>

<span data-ttu-id="b39f9-110">Das Cmdlet **Test-PswaAuthorizationRule** überprüft, ob eine Regel für einen bestimmten Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b39f9-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="b39f9-111">Dieses Cmdlet kann auch zum Testen von Autorisierungsregeln verwendet werden, um zu überprüfen, ob die Zugriffsanforderung eines bestimmten Benutzers, Computers oder Endpunkts autorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="b39f9-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="b39f9-112">Dieses Cmdlet wertet standardmäßig alle Regeln in der Autorisierungsdatei aus.</span><span class="sxs-lookup"><span data-stu-id="b39f9-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="b39f9-113">Sie können jedoch eine Teilmenge von zu testenden Regeln angeben.</span><span class="sxs-lookup"><span data-stu-id="b39f9-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="b39f9-114">Sie können dieses Cmdlet für die Problembehandlung von Authentifizierungsfehlern verwenden.</span><span class="sxs-lookup"><span data-stu-id="b39f9-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="b39f9-115">Die Parameter dieses Cmdlets entsprechen den Feldern auf der Windows PowerShell® Web Access-Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="b39f9-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="b39f9-116">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="b39f9-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="b39f9-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="b39f9-118">Gibt den Namen des zu testenden Computers an.</span><span class="sxs-lookup"><span data-stu-id="b39f9-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="b39f9-119">Aliase</span><span class="sxs-lookup"><span data-stu-id="b39f9-119">Aliases</span></span>                              | <span data-ttu-id="b39f9-120">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-120">none</span></span>                                 |
| <span data-ttu-id="b39f9-121">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b39f9-121">Required?</span></span>                            | <span data-ttu-id="b39f9-122">wahr</span><span class="sxs-lookup"><span data-stu-id="b39f9-122">true</span></span>                                 |
| <span data-ttu-id="b39f9-123">Position?</span><span class="sxs-lookup"><span data-stu-id="b39f9-123">Position?</span></span>                            | <span data-ttu-id="b39f9-124">2</span><span class="sxs-lookup"><span data-stu-id="b39f9-124">2</span></span>                                    |
| <span data-ttu-id="b39f9-125">Standardwert</span><span class="sxs-lookup"><span data-stu-id="b39f9-125">Default Value</span></span>                        | <span data-ttu-id="b39f9-126">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-126">none</span></span>                                 |
| <span data-ttu-id="b39f9-127">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b39f9-128">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-128">false</span></span>                                |
| <span data-ttu-id="b39f9-129">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b39f9-130">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="b39f9-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="b39f9-132">Gibt den Namen einer zu testenden Windows PowerShell-Sitzungskonfiguration (auch als Endpunkt oder Runspaces bezeichnet) an.</span><span class="sxs-lookup"><span data-stu-id="b39f9-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="b39f9-133">Aliase</span><span class="sxs-lookup"><span data-stu-id="b39f9-133">Aliases</span></span>                              | <span data-ttu-id="b39f9-134">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-134">none</span></span>                                 |
| <span data-ttu-id="b39f9-135">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b39f9-135">Required?</span></span>                            | <span data-ttu-id="b39f9-136">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-136">false</span></span>                                |
| <span data-ttu-id="b39f9-137">Position?</span><span class="sxs-lookup"><span data-stu-id="b39f9-137">Position?</span></span>                            | <span data-ttu-id="b39f9-138">3</span><span class="sxs-lookup"><span data-stu-id="b39f9-138">3</span></span>                                    |
| <span data-ttu-id="b39f9-139">Standardwert</span><span class="sxs-lookup"><span data-stu-id="b39f9-139">Default Value</span></span>                        | <span data-ttu-id="b39f9-140">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-140">none</span></span>                                 |
| <span data-ttu-id="b39f9-141">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b39f9-142">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-142">false</span></span>                                |
| <span data-ttu-id="b39f9-143">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b39f9-144">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="b39f9-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="b39f9-146">Gibt die zu testende Verbindungs-URI an.</span><span class="sxs-lookup"><span data-stu-id="b39f9-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="b39f9-147">Aliase</span><span class="sxs-lookup"><span data-stu-id="b39f9-147">Aliases</span></span>                              | <span data-ttu-id="b39f9-148">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-148">none</span></span>                                 |
| <span data-ttu-id="b39f9-149">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b39f9-149">Required?</span></span>                            | <span data-ttu-id="b39f9-150">wahr</span><span class="sxs-lookup"><span data-stu-id="b39f9-150">true</span></span>                                 |
| <span data-ttu-id="b39f9-151">Position?</span><span class="sxs-lookup"><span data-stu-id="b39f9-151">Position?</span></span>                            | <span data-ttu-id="b39f9-152">2</span><span class="sxs-lookup"><span data-stu-id="b39f9-152">2</span></span>                                    |
| <span data-ttu-id="b39f9-153">Standardwert</span><span class="sxs-lookup"><span data-stu-id="b39f9-153">Default Value</span></span>                        | <span data-ttu-id="b39f9-154">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-154">none</span></span>                                 |
| <span data-ttu-id="b39f9-155">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b39f9-156">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-156">false</span></span>                                |
| <span data-ttu-id="b39f9-157">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b39f9-158">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="b39f9-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="b39f9-160">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Testen der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b39f9-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="b39f9-161">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="b39f9-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="b39f9-162">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Testen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) aus.</span><span class="sxs-lookup"><span data-stu-id="b39f9-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="b39f9-163">Aliase</span><span class="sxs-lookup"><span data-stu-id="b39f9-163">Aliases</span></span>                              | <span data-ttu-id="b39f9-164">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-164">none</span></span>                                 |
| <span data-ttu-id="b39f9-165">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b39f9-165">Required?</span></span>                            | <span data-ttu-id="b39f9-166">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-166">false</span></span>                                |
| <span data-ttu-id="b39f9-167">Position?</span><span class="sxs-lookup"><span data-stu-id="b39f9-167">Position?</span></span>                            | <span data-ttu-id="b39f9-168">benannt</span><span class="sxs-lookup"><span data-stu-id="b39f9-168">named</span></span>                                |
| <span data-ttu-id="b39f9-169">Standardwert</span><span class="sxs-lookup"><span data-stu-id="b39f9-169">Default Value</span></span>                        | <span data-ttu-id="b39f9-170">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-170">none</span></span>                                 |
| <span data-ttu-id="b39f9-171">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b39f9-172">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-172">false</span></span>                                |
| <span data-ttu-id="b39f9-173">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b39f9-174">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="b39f9-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="b39f9-176">Gibt eine Teilmenge der zu testenden Regeln an.</span><span class="sxs-lookup"><span data-stu-id="b39f9-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="b39f9-177">Wenn dieser Parameter nicht angegeben ist, testet dieses Cmdlet alle Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="b39f9-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="b39f9-178">Aliase</span><span class="sxs-lookup"><span data-stu-id="b39f9-178">Aliases</span></span>                              | <span data-ttu-id="b39f9-179">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-179">none</span></span>                                 |
| <span data-ttu-id="b39f9-180">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b39f9-180">Required?</span></span>                            | <span data-ttu-id="b39f9-181">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-181">false</span></span>                                |
| <span data-ttu-id="b39f9-182">Position?</span><span class="sxs-lookup"><span data-stu-id="b39f9-182">Position?</span></span>                            | <span data-ttu-id="b39f9-183">benannt</span><span class="sxs-lookup"><span data-stu-id="b39f9-183">named</span></span>                                |
| <span data-ttu-id="b39f9-184">Standardwert</span><span class="sxs-lookup"><span data-stu-id="b39f9-184">Default Value</span></span>                        | <span data-ttu-id="b39f9-185">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-185">none</span></span>                                 |
| <span data-ttu-id="b39f9-186">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b39f9-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="b39f9-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="b39f9-188">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b39f9-189">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="b39f9-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="b39f9-191">Gibt den Namen des zu testenden Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="b39f9-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="b39f9-192">Aliase</span><span class="sxs-lookup"><span data-stu-id="b39f9-192">Aliases</span></span>                              | <span data-ttu-id="b39f9-193">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-193">none</span></span>                                 |
| <span data-ttu-id="b39f9-194">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="b39f9-194">Required?</span></span>                            | <span data-ttu-id="b39f9-195">wahr</span><span class="sxs-lookup"><span data-stu-id="b39f9-195">true</span></span>                                 |
| <span data-ttu-id="b39f9-196">Position?</span><span class="sxs-lookup"><span data-stu-id="b39f9-196">Position?</span></span>                            | <span data-ttu-id="b39f9-197">1</span><span class="sxs-lookup"><span data-stu-id="b39f9-197">1</span></span>                                    |
| <span data-ttu-id="b39f9-198">Standardwert</span><span class="sxs-lookup"><span data-stu-id="b39f9-198">Default Value</span></span>                        | <span data-ttu-id="b39f9-199">keine</span><span class="sxs-lookup"><span data-stu-id="b39f9-199">none</span></span>                                 |
| <span data-ttu-id="b39f9-200">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b39f9-201">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-201">false</span></span>                                |
| <span data-ttu-id="b39f9-202">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="b39f9-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b39f9-203">falsch</span><span class="sxs-lookup"><span data-stu-id="b39f9-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b39f9-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b39f9-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b39f9-205">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b39f9-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b39f9-206">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b39f9-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b39f9-207">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="b39f9-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="b39f9-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="b39f9-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="b39f9-209">Dieses Cmdlet akzeptiert ein Array von „PswaAuthorizationRule“-Objekten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="b39f9-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="b39f9-210">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="b39f9-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="b39f9-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="b39f9-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="b39f9-212">Dieses Cmdlet stellt ein Array von „PswaAuthorizationRule“-Objekten als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="b39f9-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="b39f9-213">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="b39f9-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b39f9-214">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="b39f9-214">EXAMPLE 1</span></span>

<span data-ttu-id="b39f9-215">In diesem Beispiel werden alle Autorisierungsregeln getestet, um alle Regeln anzuzeigen, die es dem Benutzer *contoso\\mhanson* ermöglichen, sich mit dem Computer *srv2* zu verbinden und eine Windows PowerShell-Sitzungskonfiguration namens *Test* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b39f9-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="b39f9-216">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="b39f9-216">EXAMPLE 2</span></span>

<span data-ttu-id="b39f9-217">In diesem Beispiel werden alle Autorisierungsregeln getestet, um zu überprüfen, welche davon für den Benutzer *contoso\\mhanson* gelten.</span><span class="sxs-lookup"><span data-stu-id="b39f9-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="b39f9-218">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b39f9-218">Related topics</span></span>

- [<span data-ttu-id="b39f9-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b39f9-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b39f9-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b39f9-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b39f9-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b39f9-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="b39f9-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b39f9-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
