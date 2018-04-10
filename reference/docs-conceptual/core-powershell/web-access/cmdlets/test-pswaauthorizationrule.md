---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Testen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="8e0fa-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e0fa-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="8e0fa-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="8e0fa-104">SYNOPSIS</span></span>

<span data-ttu-id="8e0fa-105">Überprüft, ob eine Regel für einen angegebenen Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e0fa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8e0fa-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="8e0fa-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="8e0fa-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="8e0fa-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8e0fa-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="8e0fa-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="8e0fa-109">DESCRIPTION</span></span>

<span data-ttu-id="8e0fa-110">Das Cmdlet **Test-PswaAuthorizationRule** überprüft, ob eine Regel für einen bestimmten Benutzer, Computer oder Endpunkt vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="8e0fa-111">Dieses Cmdlet kann auch zum Testen von Autorisierungsregeln verwendet werden, um zu überprüfen, ob die Zugriffsanforderung eines bestimmten Benutzers, Computers oder Endpunkts autorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="8e0fa-112">Dieses Cmdlet wertet standardmäßig alle Regeln in der Autorisierungsdatei aus.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="8e0fa-113">Sie können jedoch eine Teilmenge von zu testenden Regeln angeben.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="8e0fa-114">Sie können dieses Cmdlet für die Problembehandlung von Authentifizierungsfehlern verwenden.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="8e0fa-115">Die Parameter dieses Cmdlets entsprechen den Feldern auf der Windows PowerShell® Web Access-Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="8e0fa-116">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="8e0fa-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="8e0fa-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="8e0fa-118">Gibt den Namen des zu testenden Computers an.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8e0fa-119">Aliase</span><span class="sxs-lookup"><span data-stu-id="8e0fa-119">Aliases</span></span>                              | <span data-ttu-id="8e0fa-120">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-120">none</span></span>                                 |
| <span data-ttu-id="8e0fa-121">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-121">Required?</span></span>                            | <span data-ttu-id="8e0fa-122">wahr</span><span class="sxs-lookup"><span data-stu-id="8e0fa-122">true</span></span>                                 |
| <span data-ttu-id="8e0fa-123">Position?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-123">Position?</span></span>                            | <span data-ttu-id="8e0fa-124">2</span><span class="sxs-lookup"><span data-stu-id="8e0fa-124">2</span></span>                                    |
| <span data-ttu-id="8e0fa-125">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8e0fa-125">Default Value</span></span>                        | <span data-ttu-id="8e0fa-126">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-126">none</span></span>                                 |
| <span data-ttu-id="8e0fa-127">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e0fa-128">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-128">false</span></span>                                |
| <span data-ttu-id="8e0fa-129">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e0fa-130">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="8e0fa-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="8e0fa-132">Gibt den Namen einer zu testenden Windows PowerShell-Sitzungskonfiguration (auch als Endpunkt oder Runspaces bezeichnet) an.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8e0fa-133">Aliase</span><span class="sxs-lookup"><span data-stu-id="8e0fa-133">Aliases</span></span>                              | <span data-ttu-id="8e0fa-134">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-134">none</span></span>                                 |
| <span data-ttu-id="8e0fa-135">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-135">Required?</span></span>                            | <span data-ttu-id="8e0fa-136">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-136">false</span></span>                                |
| <span data-ttu-id="8e0fa-137">Position?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-137">Position?</span></span>                            | <span data-ttu-id="8e0fa-138">3</span><span class="sxs-lookup"><span data-stu-id="8e0fa-138">3</span></span>                                    |
| <span data-ttu-id="8e0fa-139">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8e0fa-139">Default Value</span></span>                        | <span data-ttu-id="8e0fa-140">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-140">none</span></span>                                 |
| <span data-ttu-id="8e0fa-141">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e0fa-142">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-142">false</span></span>                                |
| <span data-ttu-id="8e0fa-143">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e0fa-144">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="8e0fa-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="8e0fa-146">Gibt die zu testende Verbindungs-URI an.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8e0fa-147">Aliase</span><span class="sxs-lookup"><span data-stu-id="8e0fa-147">Aliases</span></span>                              | <span data-ttu-id="8e0fa-148">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-148">none</span></span>                                 |
| <span data-ttu-id="8e0fa-149">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-149">Required?</span></span>                            | <span data-ttu-id="8e0fa-150">wahr</span><span class="sxs-lookup"><span data-stu-id="8e0fa-150">true</span></span>                                 |
| <span data-ttu-id="8e0fa-151">Position?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-151">Position?</span></span>                            | <span data-ttu-id="8e0fa-152">2</span><span class="sxs-lookup"><span data-stu-id="8e0fa-152">2</span></span>                                    |
| <span data-ttu-id="8e0fa-153">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8e0fa-153">Default Value</span></span>                        | <span data-ttu-id="8e0fa-154">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-154">none</span></span>                                 |
| <span data-ttu-id="8e0fa-155">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e0fa-156">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-156">false</span></span>                                |
| <span data-ttu-id="8e0fa-157">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e0fa-158">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="8e0fa-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="8e0fa-160">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Testen der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="8e0fa-161">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="8e0fa-162">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Testen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) aus.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="8e0fa-163">Aliase</span><span class="sxs-lookup"><span data-stu-id="8e0fa-163">Aliases</span></span>                              | <span data-ttu-id="8e0fa-164">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-164">none</span></span>                                 |
| <span data-ttu-id="8e0fa-165">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-165">Required?</span></span>                            | <span data-ttu-id="8e0fa-166">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-166">false</span></span>                                |
| <span data-ttu-id="8e0fa-167">Position?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-167">Position?</span></span>                            | <span data-ttu-id="8e0fa-168">benannt</span><span class="sxs-lookup"><span data-stu-id="8e0fa-168">named</span></span>                                |
| <span data-ttu-id="8e0fa-169">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8e0fa-169">Default Value</span></span>                        | <span data-ttu-id="8e0fa-170">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-170">none</span></span>                                 |
| <span data-ttu-id="8e0fa-171">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e0fa-172">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-172">false</span></span>                                |
| <span data-ttu-id="8e0fa-173">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e0fa-174">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="8e0fa-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="8e0fa-176">Gibt eine Teilmenge der zu testenden Regeln an.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="8e0fa-177">Wenn dieser Parameter nicht angegeben ist, testet dieses Cmdlet alle Autorisierungsregeln.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="8e0fa-178">Aliase</span><span class="sxs-lookup"><span data-stu-id="8e0fa-178">Aliases</span></span>                              | <span data-ttu-id="8e0fa-179">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-179">none</span></span>                                 |
| <span data-ttu-id="8e0fa-180">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-180">Required?</span></span>                            | <span data-ttu-id="8e0fa-181">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-181">false</span></span>                                |
| <span data-ttu-id="8e0fa-182">Position?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-182">Position?</span></span>                            | <span data-ttu-id="8e0fa-183">benannt</span><span class="sxs-lookup"><span data-stu-id="8e0fa-183">named</span></span>                                |
| <span data-ttu-id="8e0fa-184">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8e0fa-184">Default Value</span></span>                        | <span data-ttu-id="8e0fa-185">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-185">none</span></span>                                 |
| <span data-ttu-id="8e0fa-186">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e0fa-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="8e0fa-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="8e0fa-188">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e0fa-189">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="8e0fa-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="8e0fa-191">Gibt den Namen des zu testenden Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8e0fa-192">Aliase</span><span class="sxs-lookup"><span data-stu-id="8e0fa-192">Aliases</span></span>                              | <span data-ttu-id="8e0fa-193">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-193">none</span></span>                                 |
| <span data-ttu-id="8e0fa-194">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-194">Required?</span></span>                            | <span data-ttu-id="8e0fa-195">wahr</span><span class="sxs-lookup"><span data-stu-id="8e0fa-195">true</span></span>                                 |
| <span data-ttu-id="8e0fa-196">Position?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-196">Position?</span></span>                            | <span data-ttu-id="8e0fa-197">1</span><span class="sxs-lookup"><span data-stu-id="8e0fa-197">1</span></span>                                    |
| <span data-ttu-id="8e0fa-198">Standardwert</span><span class="sxs-lookup"><span data-stu-id="8e0fa-198">Default Value</span></span>                        | <span data-ttu-id="8e0fa-199">keine</span><span class="sxs-lookup"><span data-stu-id="8e0fa-199">none</span></span>                                 |
| <span data-ttu-id="8e0fa-200">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8e0fa-201">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-201">false</span></span>                                |
| <span data-ttu-id="8e0fa-202">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="8e0fa-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8e0fa-203">falsch</span><span class="sxs-lookup"><span data-stu-id="8e0fa-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="8e0fa-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="8e0fa-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="8e0fa-205">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="8e0fa-206">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8e0fa-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="8e0fa-207">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="8e0fa-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8e0fa-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8e0fa-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8e0fa-209">Dieses Cmdlet akzeptiert ein Array von „PswaAuthorizationRule“-Objekten als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="8e0fa-210">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="8e0fa-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8e0fa-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8e0fa-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8e0fa-212">Dieses Cmdlet stellt ein Array von „PswaAuthorizationRule“-Objekten als Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="8e0fa-213">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="8e0fa-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="8e0fa-214">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="8e0fa-214">EXAMPLE 1</span></span>

<span data-ttu-id="8e0fa-215">In diesem Beispiel werden alle Autorisierungsregeln getestet, um alle Regeln anzuzeigen, die es dem Benutzer *contoso\\mhanson* ermöglichen, sich mit dem Computer *srv2* zu verbinden und eine Windows PowerShell-Sitzungskonfiguration namens *Test* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="8e0fa-216">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="8e0fa-216">EXAMPLE 2</span></span>

<span data-ttu-id="8e0fa-217">In diesem Beispiel werden alle Autorisierungsregeln getestet, um zu überprüfen, welche davon für den Benutzer *contoso\\mhanson* gelten.</span><span class="sxs-lookup"><span data-stu-id="8e0fa-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="8e0fa-218">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8e0fa-218">Related topics</span></span>

- [<span data-ttu-id="8e0fa-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e0fa-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="8e0fa-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e0fa-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="8e0fa-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8e0fa-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="8e0fa-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e0fa-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)