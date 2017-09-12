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
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="8b20e-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b20e-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="8b20e-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="8b20e-104">SYNOPSIS</span></span>

<span data-ttu-id="8b20e-105">Überprüft, ob eine Regel für einen angegebenen Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8b20e-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b20e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b20e-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="8b20e-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="8b20e-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="8b20e-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8b20e-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="8b20e-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="8b20e-109">DESCRIPTION</span></span>

<span data-ttu-id="8b20e-110">Das Cmdlet **Test-PswaAuthorizationRule** überprüft, ob eine Regel für einen bestimmten Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8b20e-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="8b20e-111">Dieses Cmdlet kann auch zum Testen von Autorisierungsregeln verwendet werden, um zu überprüfen, ob die Zugriffsanforderung eines bestimmten Benutzers, Computers oder Endpunkts autorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="8b20e-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="8b20e-112">Dieses Cmdlet wertet standardmäßig alle Regeln in der Autorisierungsdatei aus.</span><span class="sxs-lookup"><span data-stu-id="8b20e-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="8b20e-113">Sie können jedoch eine Teilmenge von zu testenden Regeln angeben.</span><span class="sxs-lookup"><span data-stu-id="8b20e-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="8b20e-114">Sie können dieses Cmdlet für die Problembehandlung von Authentifizierungsfehlern verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b20e-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="8b20e-115">Die Parameter dieses Cmdlets entsprechen den Feldern auf der Windows PowerShell® Web Access-Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="8b20e-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="8b20e-116">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="8b20e-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="8b20e-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="8b20e-118">Gibt den Namen des zu testenden Computers an.</span><span class="sxs-lookup"><span data-stu-id="8b20e-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8b20e-119">Aliase</span><span class="sxs-lookup"><span data-stu-id="8b20e-119">Aliases</span></span>                              | <span data-ttu-id="8b20e-120">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-120">none</span></span>                                 |
| <span data-ttu-id="8b20e-121">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8b20e-121">Required?</span></span>                            | <span data-ttu-id="8b20e-122">wahr</span><span class="sxs-lookup"><span data-stu-id="8b20e-122">true</span></span>                                 |
| <span data-ttu-id="8b20e-123">Position?</span><span class="sxs-lookup"><span data-stu-id="8b20e-123">Position?</span></span>                            | <span data-ttu-id="8b20e-124">2</span><span class="sxs-lookup"><span data-stu-id="8b20e-124">2</span></span>                                    |
| <span data-ttu-id="8b20e-125">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b20e-125">Default Value</span></span>                        | <span data-ttu-id="8b20e-126">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-126">none</span></span>                                 |
| <span data-ttu-id="8b20e-127">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8b20e-128">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-128">false</span></span>                                |
| <span data-ttu-id="8b20e-129">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8b20e-130">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="8b20e-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="8b20e-132">Gibt den Namen einer zu testenden Windows PowerShell-Sitzungskonfiguration (auch als Endpunkt oder Runspaces bezeichnet) an.</span><span class="sxs-lookup"><span data-stu-id="8b20e-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8b20e-133">Aliase</span><span class="sxs-lookup"><span data-stu-id="8b20e-133">Aliases</span></span>                              | <span data-ttu-id="8b20e-134">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-134">none</span></span>                                 |
| <span data-ttu-id="8b20e-135">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8b20e-135">Required?</span></span>                            | <span data-ttu-id="8b20e-136">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-136">false</span></span>                                |
| <span data-ttu-id="8b20e-137">Position?</span><span class="sxs-lookup"><span data-stu-id="8b20e-137">Position?</span></span>                            | <span data-ttu-id="8b20e-138">3</span><span class="sxs-lookup"><span data-stu-id="8b20e-138">3</span></span>                                    |
| <span data-ttu-id="8b20e-139">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b20e-139">Default Value</span></span>                        | <span data-ttu-id="8b20e-140">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-140">none</span></span>                                 |
| <span data-ttu-id="8b20e-141">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8b20e-142">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-142">false</span></span>                                |
| <span data-ttu-id="8b20e-143">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8b20e-144">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="8b20e-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="8b20e-146">Gibt die zu testende Verbindungs-URI an.</span><span class="sxs-lookup"><span data-stu-id="8b20e-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8b20e-147">Aliase</span><span class="sxs-lookup"><span data-stu-id="8b20e-147">Aliases</span></span>                              | <span data-ttu-id="8b20e-148">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-148">none</span></span>                                 |
| <span data-ttu-id="8b20e-149">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8b20e-149">Required?</span></span>                            | <span data-ttu-id="8b20e-150">wahr</span><span class="sxs-lookup"><span data-stu-id="8b20e-150">true</span></span>                                 |
| <span data-ttu-id="8b20e-151">Position?</span><span class="sxs-lookup"><span data-stu-id="8b20e-151">Position?</span></span>                            | <span data-ttu-id="8b20e-152">2</span><span class="sxs-lookup"><span data-stu-id="8b20e-152">2</span></span>                                    |
| <span data-ttu-id="8b20e-153">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b20e-153">Default Value</span></span>                        | <span data-ttu-id="8b20e-154">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-154">none</span></span>                                 |
| <span data-ttu-id="8b20e-155">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8b20e-156">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-156">false</span></span>                                |
| <span data-ttu-id="8b20e-157">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8b20e-158">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="8b20e-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="8b20e-160">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Testen der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8b20e-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="8b20e-161">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="8b20e-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="8b20e-162">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Testen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) aus.</span><span class="sxs-lookup"><span data-stu-id="8b20e-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="8b20e-163">Aliase</span><span class="sxs-lookup"><span data-stu-id="8b20e-163">Aliases</span></span>                              | <span data-ttu-id="8b20e-164">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-164">none</span></span>                                 |
| <span data-ttu-id="8b20e-165">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8b20e-165">Required?</span></span>                            | <span data-ttu-id="8b20e-166">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-166">false</span></span>                                |
| <span data-ttu-id="8b20e-167">Position?</span><span class="sxs-lookup"><span data-stu-id="8b20e-167">Position?</span></span>                            | <span data-ttu-id="8b20e-168">benannt</span><span class="sxs-lookup"><span data-stu-id="8b20e-168">named</span></span>                                |
| <span data-ttu-id="8b20e-169">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b20e-169">Default Value</span></span>                        | <span data-ttu-id="8b20e-170">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-170">none</span></span>                                 |
| <span data-ttu-id="8b20e-171">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8b20e-172">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-172">false</span></span>                                |
| <span data-ttu-id="8b20e-173">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8b20e-174">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="8b20e-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="8b20e-176">Gibt eine Teilmenge der zu testenden Regeln an.</span><span class="sxs-lookup"><span data-stu-id="8b20e-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="8b20e-177">Wenn dieser Parameter nicht angegeben ist, testet dieses Cmdlet alle Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="8b20e-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="8b20e-178">Aliase</span><span class="sxs-lookup"><span data-stu-id="8b20e-178">Aliases</span></span>                              | <span data-ttu-id="8b20e-179">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-179">none</span></span>                                 |
| <span data-ttu-id="8b20e-180">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8b20e-180">Required?</span></span>                            | <span data-ttu-id="8b20e-181">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-181">false</span></span>                                |
| <span data-ttu-id="8b20e-182">Position?</span><span class="sxs-lookup"><span data-stu-id="8b20e-182">Position?</span></span>                            | <span data-ttu-id="8b20e-183">benannt</span><span class="sxs-lookup"><span data-stu-id="8b20e-183">named</span></span>                                |
| <span data-ttu-id="8b20e-184">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b20e-184">Default Value</span></span>                        | <span data-ttu-id="8b20e-185">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-185">none</span></span>                                 |
| <span data-ttu-id="8b20e-186">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8b20e-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="8b20e-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="8b20e-188">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8b20e-189">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="8b20e-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="8b20e-191">Gibt den Namen des zu testenden Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="8b20e-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="8b20e-192">Aliase</span><span class="sxs-lookup"><span data-stu-id="8b20e-192">Aliases</span></span>                              | <span data-ttu-id="8b20e-193">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-193">none</span></span>                                 |
| <span data-ttu-id="8b20e-194">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8b20e-194">Required?</span></span>                            | <span data-ttu-id="8b20e-195">wahr</span><span class="sxs-lookup"><span data-stu-id="8b20e-195">true</span></span>                                 |
| <span data-ttu-id="8b20e-196">Position?</span><span class="sxs-lookup"><span data-stu-id="8b20e-196">Position?</span></span>                            | <span data-ttu-id="8b20e-197">1</span><span class="sxs-lookup"><span data-stu-id="8b20e-197">1</span></span>                                    |
| <span data-ttu-id="8b20e-198">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8b20e-198">Default Value</span></span>                        | <span data-ttu-id="8b20e-199">keine</span><span class="sxs-lookup"><span data-stu-id="8b20e-199">none</span></span>                                 |
| <span data-ttu-id="8b20e-200">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8b20e-201">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-201">false</span></span>                                |
| <span data-ttu-id="8b20e-202">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8b20e-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8b20e-203">falsch</span><span class="sxs-lookup"><span data-stu-id="8b20e-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="8b20e-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="8b20e-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="8b20e-205">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="8b20e-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="8b20e-206">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8b20e-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="8b20e-207">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="8b20e-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8b20e-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8b20e-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8b20e-209">Dieses Cmdlet akzeptiert ein Array von „PswaAuthorizationRule“-Objekten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="8b20e-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="8b20e-210">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="8b20e-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8b20e-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8b20e-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8b20e-212">Dieses Cmdlet stellt ein Array von „PswaAuthorizationRule“-Objekten als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="8b20e-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="8b20e-213">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="8b20e-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="8b20e-214">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="8b20e-214">EXAMPLE 1</span></span>

<span data-ttu-id="8b20e-215">In diesem Beispiel werden alle Autorisierungsregeln getestet, um alle Regeln anzuzeigen, die es dem Benutzer *contoso\\mhanson* ermöglichen, sich mit dem Computer *srv2* zu verbinden und eine Windows PowerShell-Sitzungskonfiguration namens *Test* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b20e-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="8b20e-216">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="8b20e-216">EXAMPLE 2</span></span>

<span data-ttu-id="8b20e-217">In diesem Beispiel werden alle Autorisierungsregeln getestet, um zu überprüfen, welche davon für den Benutzer *contoso\\mhanson* gelten.</span><span class="sxs-lookup"><span data-stu-id="8b20e-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="8b20e-218">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8b20e-218">Related topics</span></span>

- [<span data-ttu-id="8b20e-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b20e-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="8b20e-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b20e-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="8b20e-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8b20e-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="8b20e-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8b20e-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
