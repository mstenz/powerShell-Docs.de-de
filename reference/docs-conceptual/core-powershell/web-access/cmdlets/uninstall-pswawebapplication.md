---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Deinstallieren von pswawebapplication
ms.technology: powershell
ms.openlocfilehash: cc54c94426d754ff2d3bf658e3e92083f02cd6c7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="60b0b-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="60b0b-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="60b0b-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="60b0b-104">SYNOPSIS</span></span>

<span data-ttu-id="60b0b-105">Deinstalliert die Windows PowerShell®-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="60b0b-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="60b0b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="60b0b-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="60b0b-107">Standardwert</span><span class="sxs-lookup"><span data-stu-id="60b0b-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="60b0b-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="60b0b-108">DESCRIPTION</span></span>

<span data-ttu-id="60b0b-109">Das Cmdlet **Uninstall-PswaWebApplication** deinstalliert die Windows PowerShell-Webanwendung und entfernt die Website aus IIS.</span><span class="sxs-lookup"><span data-stu-id="60b0b-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="60b0b-110">Durch das Cmdlet werden IIS oder andere installierte Features nicht deinstalliert, da sie für das Ausführen von Windows PowerShell erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="60b0b-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="60b0b-111">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="60b0b-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="60b0b-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="60b0b-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="60b0b-113">Gibt an, dass die Testzertifikate, die mit dem Cmdlet **Install\_PswaWebApplication** (mit dem Parameter **UseTestCertificate**) erstellt wurden, gelöscht wurden.</span><span class="sxs-lookup"><span data-stu-id="60b0b-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="60b0b-114">Nur das Testzertifikat, das den gleichen Namen wie das hat, das mit dem Cmdlet **Install-PswaWebApplication** erstellt wurde, wurde gelöscht.</span><span class="sxs-lookup"><span data-stu-id="60b0b-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="60b0b-115">Aliase</span><span class="sxs-lookup"><span data-stu-id="60b0b-115">Aliases</span></span>                              | <span data-ttu-id="60b0b-116">keine</span><span class="sxs-lookup"><span data-stu-id="60b0b-116">none</span></span>                                 |
| <span data-ttu-id="60b0b-117">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="60b0b-117">Required?</span></span>                            | <span data-ttu-id="60b0b-118">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-118">false</span></span>                                |
| <span data-ttu-id="60b0b-119">Position?</span><span class="sxs-lookup"><span data-stu-id="60b0b-119">Position?</span></span>                            | <span data-ttu-id="60b0b-120">benannt</span><span class="sxs-lookup"><span data-stu-id="60b0b-120">named</span></span>                                |
| <span data-ttu-id="60b0b-121">Standardwert</span><span class="sxs-lookup"><span data-stu-id="60b0b-121">Default Value</span></span>                        | <span data-ttu-id="60b0b-122">wahr</span><span class="sxs-lookup"><span data-stu-id="60b0b-122">true</span></span>                                 |
| <span data-ttu-id="60b0b-123">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="60b0b-124">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-124">false</span></span>                                |
| <span data-ttu-id="60b0b-125">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="60b0b-126">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="60b0b-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="60b0b-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="60b0b-128">Gibt den Namen der zu deinstallierenden Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="60b0b-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="60b0b-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="60b0b-129">Aliases</span></span>                              | <span data-ttu-id="60b0b-130">keine</span><span class="sxs-lookup"><span data-stu-id="60b0b-130">none</span></span>                                 |
| <span data-ttu-id="60b0b-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="60b0b-131">Required?</span></span>                            | <span data-ttu-id="60b0b-132">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-132">false</span></span>                                |
| <span data-ttu-id="60b0b-133">Position?</span><span class="sxs-lookup"><span data-stu-id="60b0b-133">Position?</span></span>                            | <span data-ttu-id="60b0b-134">1</span><span class="sxs-lookup"><span data-stu-id="60b0b-134">1</span></span>                                    |
| <span data-ttu-id="60b0b-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="60b0b-135">Default Value</span></span>                        | <span data-ttu-id="60b0b-136">pswa</span><span class="sxs-lookup"><span data-stu-id="60b0b-136">pswa</span></span>                                 |
| <span data-ttu-id="60b0b-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="60b0b-138">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-138">false</span></span>                                |
| <span data-ttu-id="60b0b-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="60b0b-140">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="60b0b-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="60b0b-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="60b0b-142">Gibt den Namen der Website an, auf der die Webanwendung installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="60b0b-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="60b0b-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="60b0b-143">Aliases</span></span>                              | <span data-ttu-id="60b0b-144">keine</span><span class="sxs-lookup"><span data-stu-id="60b0b-144">none</span></span>                                 |
| <span data-ttu-id="60b0b-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="60b0b-145">Required?</span></span>                            | <span data-ttu-id="60b0b-146">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-146">false</span></span>                                |
| <span data-ttu-id="60b0b-147">Position?</span><span class="sxs-lookup"><span data-stu-id="60b0b-147">Position?</span></span>                            | <span data-ttu-id="60b0b-148">benannt</span><span class="sxs-lookup"><span data-stu-id="60b0b-148">named</span></span>                                |
| <span data-ttu-id="60b0b-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="60b0b-149">Default Value</span></span>                        | <span data-ttu-id="60b0b-150">Standardwebsite</span><span class="sxs-lookup"><span data-stu-id="60b0b-150">Default Web Site</span></span>                     |
| <span data-ttu-id="60b0b-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="60b0b-152">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-152">false</span></span>                                |
| <span data-ttu-id="60b0b-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="60b0b-154">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="60b0b-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="60b0b-155">-Confirm</span></span>

<span data-ttu-id="60b0b-156">Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="60b0b-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="60b0b-157">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="60b0b-157">Required?</span></span>                            | <span data-ttu-id="60b0b-158">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-158">false</span></span>                                |
| <span data-ttu-id="60b0b-159">Position?</span><span class="sxs-lookup"><span data-stu-id="60b0b-159">Position?</span></span>                            | <span data-ttu-id="60b0b-160">benannt</span><span class="sxs-lookup"><span data-stu-id="60b0b-160">named</span></span>                                |
| <span data-ttu-id="60b0b-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="60b0b-161">Default Value</span></span>                        | <span data-ttu-id="60b0b-162">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-162">false</span></span>                                |
| <span data-ttu-id="60b0b-163">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="60b0b-164">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-164">false</span></span>                                |
| <span data-ttu-id="60b0b-165">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="60b0b-166">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="60b0b-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="60b0b-167">-WhatIf</span></span>

<span data-ttu-id="60b0b-168">Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="60b0b-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="60b0b-169">Das Cmdlet wird nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="60b0b-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="60b0b-170">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="60b0b-170">Required?</span></span>                            | <span data-ttu-id="60b0b-171">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-171">false</span></span>                                |
| <span data-ttu-id="60b0b-172">Position?</span><span class="sxs-lookup"><span data-stu-id="60b0b-172">Position?</span></span>                            | <span data-ttu-id="60b0b-173">benannt</span><span class="sxs-lookup"><span data-stu-id="60b0b-173">named</span></span>                                |
| <span data-ttu-id="60b0b-174">Standardwert</span><span class="sxs-lookup"><span data-stu-id="60b0b-174">Default Value</span></span>                        | <span data-ttu-id="60b0b-175">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-175">false</span></span>                                |
| <span data-ttu-id="60b0b-176">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="60b0b-177">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-177">false</span></span>                                |
| <span data-ttu-id="60b0b-178">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="60b0b-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="60b0b-179">falsch</span><span class="sxs-lookup"><span data-stu-id="60b0b-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="60b0b-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="60b0b-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="60b0b-181">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="60b0b-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="60b0b-182">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="60b0b-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="60b0b-183">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="60b0b-183">INPUTS</span></span>

<span data-ttu-id="60b0b-184">Dieses Cmdlet unterstützt keine Eingabe.</span><span class="sxs-lookup"><span data-stu-id="60b0b-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="60b0b-185">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="60b0b-185">OUTPUTS</span></span>

<span data-ttu-id="60b0b-186">Dieses Cmdlet gibt keine Ausgabe zurück.</span><span class="sxs-lookup"><span data-stu-id="60b0b-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="60b0b-187">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="60b0b-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="60b0b-188">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="60b0b-188">EXAMPLE 1</span></span>

<span data-ttu-id="60b0b-189">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="60b0b-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="60b0b-190">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert haben.</span><span class="sxs-lookup"><span data-stu-id="60b0b-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="60b0b-191">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="60b0b-191">EXAMPLE 2</span></span>

<span data-ttu-id="60b0b-192">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung und löscht das der Anwendung zugeordnete Testzertifikat.</span><span class="sxs-lookup"><span data-stu-id="60b0b-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="60b0b-193">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert und ein Testzertifikat erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="60b0b-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="60b0b-194">BEISPIEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="60b0b-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="60b0b-195">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung, wenn während der Installation eine benutzerdefinierte Website und Anwendung angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="60b0b-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="60b0b-196">Dieser Befehl entfernt die Website namens *MySite* und die Anwendung namens *TestApplication*. Außerdem gibt er an, dass die der Anwendung zugeordneten Testzertifikate ebenfalls gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="60b0b-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="60b0b-197">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="60b0b-197">Related topics</span></span>

- [<span data-ttu-id="60b0b-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="60b0b-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="60b0b-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="60b0b-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="60b0b-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="60b0b-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="60b0b-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="60b0b-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="60b0b-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="60b0b-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
