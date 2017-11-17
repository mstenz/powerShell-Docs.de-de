---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Installieren von pswawebapplication
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="ab8f8-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ab8f8-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="ab8f8-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="ab8f8-104">SYNOPSIS</span></span>

<span data-ttu-id="ab8f8-105">Konfiguriert die Windows PowerShell® Web Access-Anwendung in IIS.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab8f8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab8f8-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="ab8f8-107">Standardwert</span><span class="sxs-lookup"><span data-stu-id="ab8f8-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ab8f8-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="ab8f8-108">DESCRIPTION</span></span>

<span data-ttu-id="ab8f8-109">Das Cmdlet **Install-PswaWebApplication** konfiguriert die Windows PowerShell Web Access-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="ab8f8-110">Dieser Befehl installiert die Webanwendung, ordnet sie einer Website zu und erstellt optional ein SSL-Testzertifikat mithilfe des Parameters **useTestCertificate**.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="ab8f8-111">Aus Sicherheitsgründen sollten Webadministratoren kein Testzertifikat für Produktionsumgebungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="ab8f8-112">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="ab8f8-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="ab8f8-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="ab8f8-113">-UseTestCertificate</span></span>

<span data-ttu-id="ab8f8-114">Gibt an, dass ein Testzertifikat erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="ab8f8-115">Wenn dieser Parameter auf „true“ festgelegt ist, erstellt dieses Cmdlet ein Testzertifikat und konfiguriert die Windows PowerShell Web Access-Webanwendung, damit das Zertifikat für HTTPS-Anforderungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="ab8f8-116">Wenn dieser Parameter auf „false“ festgelegt ist, wird kein Zertifikat bzw. keine Bindung erstellt.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="ab8f8-117">Legen Sie diesen Wert auf „false“ fest, wenn ein anderes Zertifikat für Windows PowerShell Web Access verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="ab8f8-118">Aliase</span><span class="sxs-lookup"><span data-stu-id="ab8f8-118">Aliases</span></span>                              | <span data-ttu-id="ab8f8-119">keine</span><span class="sxs-lookup"><span data-stu-id="ab8f8-119">none</span></span>                                 |
| <span data-ttu-id="ab8f8-120">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-120">Required?</span></span>                            | <span data-ttu-id="ab8f8-121">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-121">false</span></span>                                |
| <span data-ttu-id="ab8f8-122">Position?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-122">Position?</span></span>                            | <span data-ttu-id="ab8f8-123">benannt</span><span class="sxs-lookup"><span data-stu-id="ab8f8-123">named</span></span>                                |
| <span data-ttu-id="ab8f8-124">Standardwert</span><span class="sxs-lookup"><span data-stu-id="ab8f8-124">Default Value</span></span>                        | <span data-ttu-id="ab8f8-125">wahr</span><span class="sxs-lookup"><span data-stu-id="ab8f8-125">true</span></span>                                 |
| <span data-ttu-id="ab8f8-126">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ab8f8-127">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-127">false</span></span>                                |
| <span data-ttu-id="ab8f8-128">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ab8f8-129">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="ab8f8-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ab8f8-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="ab8f8-131">Gibt den Namen Ihrer Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-131">Specifies the name for your web application.</span></span> <span data-ttu-id="ab8f8-132">Dieser wird als letzter Teil der Windows PowerShell Web Access-URL angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="ab8f8-133">Aliase</span><span class="sxs-lookup"><span data-stu-id="ab8f8-133">Aliases</span></span>                              | <span data-ttu-id="ab8f8-134">keine</span><span class="sxs-lookup"><span data-stu-id="ab8f8-134">none</span></span>                                 |
| <span data-ttu-id="ab8f8-135">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-135">Required?</span></span>                            | <span data-ttu-id="ab8f8-136">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-136">false</span></span>                                |
| <span data-ttu-id="ab8f8-137">Position?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-137">Position?</span></span>                            | <span data-ttu-id="ab8f8-138">1</span><span class="sxs-lookup"><span data-stu-id="ab8f8-138">1</span></span>                                    |
| <span data-ttu-id="ab8f8-139">Standardwert</span><span class="sxs-lookup"><span data-stu-id="ab8f8-139">Default Value</span></span>                        | <span data-ttu-id="ab8f8-140">pswa</span><span class="sxs-lookup"><span data-stu-id="ab8f8-140">pswa</span></span>                                 |
| <span data-ttu-id="ab8f8-141">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ab8f8-142">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-142">false</span></span>                                |
| <span data-ttu-id="ab8f8-143">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ab8f8-144">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="ab8f8-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ab8f8-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="ab8f8-146">Gibt den Namen der Website des Webservers (IIS) an, auf dem die Windows PowerShell Web Access-Webanwendung installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="ab8f8-147">Aliase</span><span class="sxs-lookup"><span data-stu-id="ab8f8-147">Aliases</span></span>                              | <span data-ttu-id="ab8f8-148">keine</span><span class="sxs-lookup"><span data-stu-id="ab8f8-148">none</span></span>                                 |
| <span data-ttu-id="ab8f8-149">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-149">Required?</span></span>                            | <span data-ttu-id="ab8f8-150">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-150">false</span></span>                                |
| <span data-ttu-id="ab8f8-151">Position?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-151">Position?</span></span>                            | <span data-ttu-id="ab8f8-152">benannt</span><span class="sxs-lookup"><span data-stu-id="ab8f8-152">named</span></span>                                |
| <span data-ttu-id="ab8f8-153">Standardwert</span><span class="sxs-lookup"><span data-stu-id="ab8f8-153">Default Value</span></span>                        | <span data-ttu-id="ab8f8-154">Standardwebsite</span><span class="sxs-lookup"><span data-stu-id="ab8f8-154">Default Web Site</span></span>                     |
| <span data-ttu-id="ab8f8-155">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ab8f8-156">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-156">false</span></span>                                |
| <span data-ttu-id="ab8f8-157">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ab8f8-158">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="ab8f8-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab8f8-159">-Confirm</span></span>

<span data-ttu-id="ab8f8-160">Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="ab8f8-161">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-161">Required?</span></span>                            | <span data-ttu-id="ab8f8-162">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-162">false</span></span>                                |
| <span data-ttu-id="ab8f8-163">Position?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-163">Position?</span></span>                            | <span data-ttu-id="ab8f8-164">benannt</span><span class="sxs-lookup"><span data-stu-id="ab8f8-164">named</span></span>                                |
| <span data-ttu-id="ab8f8-165">Standardwert</span><span class="sxs-lookup"><span data-stu-id="ab8f8-165">Default Value</span></span>                        | <span data-ttu-id="ab8f8-166">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-166">false</span></span>                                |
| <span data-ttu-id="ab8f8-167">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ab8f8-168">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-168">false</span></span>                                |
| <span data-ttu-id="ab8f8-169">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ab8f8-170">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="ab8f8-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab8f8-171">-WhatIf</span></span>

<span data-ttu-id="ab8f8-172">Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ab8f8-173">Das Cmdlet wird nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="ab8f8-174">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-174">Required?</span></span>                            | <span data-ttu-id="ab8f8-175">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-175">false</span></span>                                |
| <span data-ttu-id="ab8f8-176">Position?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-176">Position?</span></span>                            | <span data-ttu-id="ab8f8-177">benannt</span><span class="sxs-lookup"><span data-stu-id="ab8f8-177">named</span></span>                                |
| <span data-ttu-id="ab8f8-178">Standardwert</span><span class="sxs-lookup"><span data-stu-id="ab8f8-178">Default Value</span></span>                        | <span data-ttu-id="ab8f8-179">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-179">false</span></span>                                |
| <span data-ttu-id="ab8f8-180">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ab8f8-181">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-181">false</span></span>                                |
| <span data-ttu-id="ab8f8-182">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="ab8f8-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ab8f8-183">falsch</span><span class="sxs-lookup"><span data-stu-id="ab8f8-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ab8f8-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ab8f8-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ab8f8-185">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ab8f8-186">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ab8f8-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ab8f8-187">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="ab8f8-187">INPUTS</span></span>

<span data-ttu-id="ab8f8-188">Dieses Cmdlet unterstützt keine Eingabe.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="ab8f8-189">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="ab8f8-189">OUTPUTS</span></span>

<span data-ttu-id="ab8f8-190">Dieses Cmdlet erzeugt keine Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="ab8f8-191">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="ab8f8-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ab8f8-192">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="ab8f8-192">EXAMPLE 1</span></span>

<span data-ttu-id="ab8f8-193">In diesem Beispiel wird die PSWA-Webanwendung mithilfe der Standardwerte für die Parameter **WebApplicationName** (*pswa*) und **WebSiteName** (*Default Web Site*) installiert.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="ab8f8-194">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="ab8f8-194">EXAMPLE 2</span></span>

<span data-ttu-id="ab8f8-195">In diesem Beispiel wird die PSWA-Webanwendung mit einem Testzertifikat und den Standardwerten für die Parameter **WebApplicationName** und **WebSiteName** installiert.</span><span class="sxs-lookup"><span data-stu-id="ab8f8-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="ab8f8-196">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ab8f8-196">Related topics</span></span>

- [<span data-ttu-id="ab8f8-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ab8f8-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="ab8f8-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ab8f8-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="ab8f8-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ab8f8-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="ab8f8-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ab8f8-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
