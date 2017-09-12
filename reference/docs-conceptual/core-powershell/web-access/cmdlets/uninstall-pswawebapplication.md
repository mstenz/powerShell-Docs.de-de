---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Deinstallieren von pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 5fe608b3bfbb90f842f16c1f5a8c51879589cf6d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="72991-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="72991-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="72991-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="72991-104">SYNOPSIS</span></span>

<span data-ttu-id="72991-105">Deinstalliert die Windows PowerShell®-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="72991-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="72991-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="72991-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="72991-107">Standardwert</span><span class="sxs-lookup"><span data-stu-id="72991-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="72991-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="72991-108">DESCRIPTION</span></span>

<span data-ttu-id="72991-109">Das Cmdlet **Uninstall-PswaWebApplication** deinstalliert die Windows PowerShell-Webanwendung und entfernt die Website aus IIS.</span><span class="sxs-lookup"><span data-stu-id="72991-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="72991-110">Durch das Cmdlet werden IIS oder andere installierte Features nicht deinstalliert, da sie für das Ausführen von Windows PowerShell erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="72991-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="72991-111">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="72991-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="72991-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="72991-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="72991-113">Gibt an, dass die Testzertifikate, die mit dem Cmdlet **Install\_PswaWebApplication** (mit dem Parameter **UseTestCertificate**) erstellt wurden, gelöscht wurden.</span><span class="sxs-lookup"><span data-stu-id="72991-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="72991-114">Nur das Testzertifikat, das den gleichen Namen wie das hat, das mit dem Cmdlet **Install-PswaWebApplication** erstellt wurde, wurde gelöscht.</span><span class="sxs-lookup"><span data-stu-id="72991-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="72991-115">Aliase</span><span class="sxs-lookup"><span data-stu-id="72991-115">Aliases</span></span>                              | <span data-ttu-id="72991-116">keine</span><span class="sxs-lookup"><span data-stu-id="72991-116">none</span></span>                                 |
| <span data-ttu-id="72991-117">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="72991-117">Required?</span></span>                            | <span data-ttu-id="72991-118">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-118">false</span></span>                                |
| <span data-ttu-id="72991-119">Position?</span><span class="sxs-lookup"><span data-stu-id="72991-119">Position?</span></span>                            | <span data-ttu-id="72991-120">benannt</span><span class="sxs-lookup"><span data-stu-id="72991-120">named</span></span>                                |
| <span data-ttu-id="72991-121">Standardwert</span><span class="sxs-lookup"><span data-stu-id="72991-121">Default Value</span></span>                        | <span data-ttu-id="72991-122">wahr</span><span class="sxs-lookup"><span data-stu-id="72991-122">true</span></span>                                 |
| <span data-ttu-id="72991-123">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="72991-124">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-124">false</span></span>                                |
| <span data-ttu-id="72991-125">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="72991-126">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="72991-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="72991-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="72991-128">Gibt den Namen der zu deinstallierenden Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="72991-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="72991-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="72991-129">Aliases</span></span>                              | <span data-ttu-id="72991-130">keine</span><span class="sxs-lookup"><span data-stu-id="72991-130">none</span></span>                                 |
| <span data-ttu-id="72991-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="72991-131">Required?</span></span>                            | <span data-ttu-id="72991-132">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-132">false</span></span>                                |
| <span data-ttu-id="72991-133">Position?</span><span class="sxs-lookup"><span data-stu-id="72991-133">Position?</span></span>                            | <span data-ttu-id="72991-134">1</span><span class="sxs-lookup"><span data-stu-id="72991-134">1</span></span>                                    |
| <span data-ttu-id="72991-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="72991-135">Default Value</span></span>                        | <span data-ttu-id="72991-136">pswa</span><span class="sxs-lookup"><span data-stu-id="72991-136">pswa</span></span>                                 |
| <span data-ttu-id="72991-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="72991-138">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-138">false</span></span>                                |
| <span data-ttu-id="72991-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="72991-140">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="72991-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="72991-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="72991-142">Gibt den Namen der Website an, auf der die Webanwendung installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="72991-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="72991-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="72991-143">Aliases</span></span>                              | <span data-ttu-id="72991-144">keine</span><span class="sxs-lookup"><span data-stu-id="72991-144">none</span></span>                                 |
| <span data-ttu-id="72991-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="72991-145">Required?</span></span>                            | <span data-ttu-id="72991-146">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-146">false</span></span>                                |
| <span data-ttu-id="72991-147">Position?</span><span class="sxs-lookup"><span data-stu-id="72991-147">Position?</span></span>                            | <span data-ttu-id="72991-148">benannt</span><span class="sxs-lookup"><span data-stu-id="72991-148">named</span></span>                                |
| <span data-ttu-id="72991-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="72991-149">Default Value</span></span>                        | <span data-ttu-id="72991-150">Standardwebsite</span><span class="sxs-lookup"><span data-stu-id="72991-150">Default Web Site</span></span>                     |
| <span data-ttu-id="72991-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="72991-152">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-152">false</span></span>                                |
| <span data-ttu-id="72991-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="72991-154">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="72991-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="72991-155">-Confirm</span></span>

<span data-ttu-id="72991-156">Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="72991-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="72991-157">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="72991-157">Required?</span></span>                            | <span data-ttu-id="72991-158">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-158">false</span></span>                                |
| <span data-ttu-id="72991-159">Position?</span><span class="sxs-lookup"><span data-stu-id="72991-159">Position?</span></span>                            | <span data-ttu-id="72991-160">benannt</span><span class="sxs-lookup"><span data-stu-id="72991-160">named</span></span>                                |
| <span data-ttu-id="72991-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="72991-161">Default Value</span></span>                        | <span data-ttu-id="72991-162">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-162">false</span></span>                                |
| <span data-ttu-id="72991-163">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="72991-164">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-164">false</span></span>                                |
| <span data-ttu-id="72991-165">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="72991-166">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="72991-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="72991-167">-WhatIf</span></span>

<span data-ttu-id="72991-168">Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="72991-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="72991-169">Das Cmdlet wird nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="72991-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="72991-170">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="72991-170">Required?</span></span>                            | <span data-ttu-id="72991-171">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-171">false</span></span>                                |
| <span data-ttu-id="72991-172">Position?</span><span class="sxs-lookup"><span data-stu-id="72991-172">Position?</span></span>                            | <span data-ttu-id="72991-173">benannt</span><span class="sxs-lookup"><span data-stu-id="72991-173">named</span></span>                                |
| <span data-ttu-id="72991-174">Standardwert</span><span class="sxs-lookup"><span data-stu-id="72991-174">Default Value</span></span>                        | <span data-ttu-id="72991-175">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-175">false</span></span>                                |
| <span data-ttu-id="72991-176">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="72991-177">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-177">false</span></span>                                |
| <span data-ttu-id="72991-178">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="72991-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="72991-179">falsch</span><span class="sxs-lookup"><span data-stu-id="72991-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="72991-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="72991-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="72991-181">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="72991-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="72991-182">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="72991-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="72991-183">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="72991-183">INPUTS</span></span>

<span data-ttu-id="72991-184">Dieses Cmdlet unterstützt keine Eingabe.</span><span class="sxs-lookup"><span data-stu-id="72991-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="72991-185">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="72991-185">OUTPUTS</span></span>

<span data-ttu-id="72991-186">Dieses Cmdlet gibt keine Ausgabe zurück.</span><span class="sxs-lookup"><span data-stu-id="72991-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="72991-187">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="72991-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="72991-188">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="72991-188">EXAMPLE 1</span></span>

<span data-ttu-id="72991-189">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="72991-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="72991-190">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert haben.</span><span class="sxs-lookup"><span data-stu-id="72991-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="72991-191">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="72991-191">EXAMPLE 2</span></span>

<span data-ttu-id="72991-192">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung und löscht das der Anwendung zugeordnete Testzertifikat.</span><span class="sxs-lookup"><span data-stu-id="72991-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="72991-193">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert und ein Testzertifikat erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="72991-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="72991-194">BEISPIEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="72991-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="72991-195">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung, wenn während der Installation eine benutzerdefinierte Website und Anwendung angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="72991-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="72991-196">Dieser Befehl entfernt die Website namens *MySite* und die Anwendung namens *TestApplication*. Außerdem gibt er an, dass die der Anwendung zugeordneten Testzertifikate ebenfalls gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="72991-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="72991-197">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="72991-197">Related topics</span></span>

- [<span data-ttu-id="72991-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="72991-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="72991-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="72991-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="72991-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="72991-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="72991-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="72991-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="72991-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="72991-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
