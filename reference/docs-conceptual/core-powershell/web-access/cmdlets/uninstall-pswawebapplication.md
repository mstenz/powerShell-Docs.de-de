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
ms.openlocfilehash: 64d546427e44d7bd284da8f682a7218afbadd0ad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2017
---
#  <a name="uninstall-pswawebapplication"></a><span data-ttu-id="1b162-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="1b162-103">Uninstall-PswaWebApplication</span></span>

##  <a name="synopsis"></a><span data-ttu-id="1b162-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="1b162-104">SYNOPSIS</span></span>

<span data-ttu-id="1b162-105">Deinstalliert die Windows PowerShell®-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="1b162-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b162-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b162-106">SYNTAX</span></span>

###  <a name="default"></a><span data-ttu-id="1b162-107">Standardwert</span><span class="sxs-lookup"><span data-stu-id="1b162-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1b162-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="1b162-108">DESCRIPTION</span></span>

<span data-ttu-id="1b162-109">Das Cmdlet **Uninstall-PswaWebApplication** deinstalliert die Windows PowerShell-Webanwendung und entfernt die Website aus IIS.</span><span class="sxs-lookup"><span data-stu-id="1b162-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="1b162-110">Durch das Cmdlet werden IIS oder andere installierte Features nicht deinstalliert, da sie für das Ausführen von Windows PowerShell erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="1b162-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="1b162-111">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="1b162-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="1b162-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="1b162-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="1b162-113">Gibt an, dass die Testzertifikate, die mit dem Cmdlet **Install\_PswaWebApplication** (mit dem Parameter **UseTestCertificate**) erstellt wurden, gelöscht wurden.</span><span class="sxs-lookup"><span data-stu-id="1b162-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="1b162-114">Nur das Testzertifikat, das den gleichen Namen wie das hat, das mit dem Cmdlet **Install-PswaWebApplication** erstellt wurde, wurde gelöscht.</span><span class="sxs-lookup"><span data-stu-id="1b162-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="1b162-115">Aliase</span><span class="sxs-lookup"><span data-stu-id="1b162-115">Aliases</span></span>                              | <span data-ttu-id="1b162-116">keine</span><span class="sxs-lookup"><span data-stu-id="1b162-116">none</span></span>                                 |
| <span data-ttu-id="1b162-117">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="1b162-117">Required?</span></span>                            | <span data-ttu-id="1b162-118">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-118">false</span></span>                                |
| <span data-ttu-id="1b162-119">Position?</span><span class="sxs-lookup"><span data-stu-id="1b162-119">Position?</span></span>                            | <span data-ttu-id="1b162-120">benannt</span><span class="sxs-lookup"><span data-stu-id="1b162-120">named</span></span>                                |
| <span data-ttu-id="1b162-121">Standardwert</span><span class="sxs-lookup"><span data-stu-id="1b162-121">Default Value</span></span>                        | <span data-ttu-id="1b162-122">wahr</span><span class="sxs-lookup"><span data-stu-id="1b162-122">true</span></span>                                 |
| <span data-ttu-id="1b162-123">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1b162-124">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-124">false</span></span>                                |
| <span data-ttu-id="1b162-125">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1b162-126">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="1b162-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1b162-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="1b162-128">Gibt den Namen der zu deinstallierenden Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="1b162-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="1b162-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="1b162-129">Aliases</span></span>                              | <span data-ttu-id="1b162-130">keine</span><span class="sxs-lookup"><span data-stu-id="1b162-130">none</span></span>                                 |
| <span data-ttu-id="1b162-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="1b162-131">Required?</span></span>                            | <span data-ttu-id="1b162-132">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-132">false</span></span>                                |
| <span data-ttu-id="1b162-133">Position?</span><span class="sxs-lookup"><span data-stu-id="1b162-133">Position?</span></span>                            | <span data-ttu-id="1b162-134">1</span><span class="sxs-lookup"><span data-stu-id="1b162-134">1</span></span>                                    |
| <span data-ttu-id="1b162-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="1b162-135">Default Value</span></span>                        | <span data-ttu-id="1b162-136">pswa</span><span class="sxs-lookup"><span data-stu-id="1b162-136">pswa</span></span>                                 |
| <span data-ttu-id="1b162-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1b162-138">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-138">false</span></span>                                |
| <span data-ttu-id="1b162-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1b162-140">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="1b162-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1b162-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="1b162-142">Gibt den Namen der Website an, auf der die Webanwendung installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="1b162-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="1b162-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="1b162-143">Aliases</span></span>                              | <span data-ttu-id="1b162-144">keine</span><span class="sxs-lookup"><span data-stu-id="1b162-144">none</span></span>                                 |
| <span data-ttu-id="1b162-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="1b162-145">Required?</span></span>                            | <span data-ttu-id="1b162-146">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-146">false</span></span>                                |
| <span data-ttu-id="1b162-147">Position?</span><span class="sxs-lookup"><span data-stu-id="1b162-147">Position?</span></span>                            | <span data-ttu-id="1b162-148">benannt</span><span class="sxs-lookup"><span data-stu-id="1b162-148">named</span></span>                                |
| <span data-ttu-id="1b162-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="1b162-149">Default Value</span></span>                        | <span data-ttu-id="1b162-150">Standardwebsite</span><span class="sxs-lookup"><span data-stu-id="1b162-150">Default Web Site</span></span>                     |
| <span data-ttu-id="1b162-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1b162-152">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-152">false</span></span>                                |
| <span data-ttu-id="1b162-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1b162-154">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="1b162-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1b162-155">-Confirm</span></span>

<span data-ttu-id="1b162-156">Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="1b162-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="1b162-157">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="1b162-157">Required?</span></span>                            | <span data-ttu-id="1b162-158">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-158">false</span></span>                                |
| <span data-ttu-id="1b162-159">Position?</span><span class="sxs-lookup"><span data-stu-id="1b162-159">Position?</span></span>                            | <span data-ttu-id="1b162-160">benannt</span><span class="sxs-lookup"><span data-stu-id="1b162-160">named</span></span>                                |
| <span data-ttu-id="1b162-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="1b162-161">Default Value</span></span>                        | <span data-ttu-id="1b162-162">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-162">false</span></span>                                |
| <span data-ttu-id="1b162-163">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1b162-164">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-164">false</span></span>                                |
| <span data-ttu-id="1b162-165">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1b162-166">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="1b162-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1b162-167">-WhatIf</span></span>

<span data-ttu-id="1b162-168">Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1b162-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1b162-169">Das Cmdlet wird nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1b162-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="1b162-170">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="1b162-170">Required?</span></span>                            | <span data-ttu-id="1b162-171">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-171">false</span></span>                                |
| <span data-ttu-id="1b162-172">Position?</span><span class="sxs-lookup"><span data-stu-id="1b162-172">Position?</span></span>                            | <span data-ttu-id="1b162-173">benannt</span><span class="sxs-lookup"><span data-stu-id="1b162-173">named</span></span>                                |
| <span data-ttu-id="1b162-174">Standardwert</span><span class="sxs-lookup"><span data-stu-id="1b162-174">Default Value</span></span>                        | <span data-ttu-id="1b162-175">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-175">false</span></span>                                |
| <span data-ttu-id="1b162-176">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1b162-177">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-177">false</span></span>                                |
| <span data-ttu-id="1b162-178">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="1b162-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1b162-179">falsch</span><span class="sxs-lookup"><span data-stu-id="1b162-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1b162-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1b162-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1b162-181">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="1b162-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1b162-182">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1b162-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="1b162-183">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="1b162-183">INPUTS</span></span>

<span data-ttu-id="1b162-184">Dieses Cmdlet unterstützt keine Eingabe.</span><span class="sxs-lookup"><span data-stu-id="1b162-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="1b162-185">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="1b162-185">OUTPUTS</span></span>

<span data-ttu-id="1b162-186">Dieses Cmdlet gibt keine Ausgabe zurück.</span><span class="sxs-lookup"><span data-stu-id="1b162-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="1b162-187">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="1b162-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1b162-188">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="1b162-188">EXAMPLE 1</span></span>

<span data-ttu-id="1b162-189">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="1b162-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="1b162-190">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert haben.</span><span class="sxs-lookup"><span data-stu-id="1b162-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="1b162-191">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="1b162-191">EXAMPLE 2</span></span>

<span data-ttu-id="1b162-192">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung und löscht das der Anwendung zugeordnete Testzertifikat.</span><span class="sxs-lookup"><span data-stu-id="1b162-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="1b162-193">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert und ein Testzertifikat erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="1b162-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="1b162-194">BEISPIEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="1b162-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="1b162-195">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung, wenn während der Installation eine benutzerdefinierte Website und Anwendung angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="1b162-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="1b162-196">Dieser Befehl entfernt die Website namens *MySite* und die Anwendung namens *TestApplication*. Außerdem gibt er an, dass die der Anwendung zugeordneten Testzertifikate ebenfalls gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="1b162-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

##  <a name="related-topics"></a><span data-ttu-id="1b162-197">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1b162-197">Related topics</span></span>

-  [<span data-ttu-id="1b162-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1b162-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="1b162-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1b162-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="1b162-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="1b162-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="1b162-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1b162-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
-  [<span data-ttu-id="1b162-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1b162-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
