---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="236f3-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="236f3-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="236f3-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="236f3-104">SYNOPSIS</span></span>

<span data-ttu-id="236f3-105">Deinstalliert die Windows PowerShell®-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="236f3-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="236f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="236f3-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="236f3-107">Standardwert</span><span class="sxs-lookup"><span data-stu-id="236f3-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="236f3-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="236f3-108">DESCRIPTION</span></span>

<span data-ttu-id="236f3-109">Das Cmdlet **Uninstall-PswaWebApplication** deinstalliert die Windows PowerShell-Webanwendung und entfernt die Website aus IIS.</span><span class="sxs-lookup"><span data-stu-id="236f3-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="236f3-110">Durch das Cmdlet werden IIS oder andere installierte Features nicht deinstalliert, da sie für das Ausführen von Windows PowerShell erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="236f3-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="236f3-111">PARAMETER</span><span class="sxs-lookup"><span data-stu-id="236f3-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="236f3-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="236f3-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="236f3-113">Gibt an, dass die Testzertifikate, die mit dem Cmdlet **Install\_PswaWebApplication** (mit dem Parameter **UseTestCertificate**) erstellt wurden, gelöscht wurden.</span><span class="sxs-lookup"><span data-stu-id="236f3-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="236f3-114">Nur das Testzertifikat, das den gleichen Namen wie das hat, das mit dem Cmdlet **Install-PswaWebApplication** erstellt wurde, wurde gelöscht.</span><span class="sxs-lookup"><span data-stu-id="236f3-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="236f3-115">Aliase</span><span class="sxs-lookup"><span data-stu-id="236f3-115">Aliases</span></span>                              | <span data-ttu-id="236f3-116">keine</span><span class="sxs-lookup"><span data-stu-id="236f3-116">none</span></span>                                 |
| <span data-ttu-id="236f3-117">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="236f3-117">Required?</span></span>                            | <span data-ttu-id="236f3-118">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-118">false</span></span>                                |
| <span data-ttu-id="236f3-119">Position?</span><span class="sxs-lookup"><span data-stu-id="236f3-119">Position?</span></span>                            | <span data-ttu-id="236f3-120">benannt</span><span class="sxs-lookup"><span data-stu-id="236f3-120">named</span></span>                                |
| <span data-ttu-id="236f3-121">Standardwert</span><span class="sxs-lookup"><span data-stu-id="236f3-121">Default Value</span></span>                        | <span data-ttu-id="236f3-122">wahr</span><span class="sxs-lookup"><span data-stu-id="236f3-122">true</span></span>                                 |
| <span data-ttu-id="236f3-123">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="236f3-124">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-124">false</span></span>                                |
| <span data-ttu-id="236f3-125">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="236f3-126">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="236f3-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="236f3-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="236f3-128">Gibt den Namen der zu deinstallierenden Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="236f3-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="236f3-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="236f3-129">Aliases</span></span>                              | <span data-ttu-id="236f3-130">keine</span><span class="sxs-lookup"><span data-stu-id="236f3-130">none</span></span>                                 |
| <span data-ttu-id="236f3-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="236f3-131">Required?</span></span>                            | <span data-ttu-id="236f3-132">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-132">false</span></span>                                |
| <span data-ttu-id="236f3-133">Position?</span><span class="sxs-lookup"><span data-stu-id="236f3-133">Position?</span></span>                            | <span data-ttu-id="236f3-134">1</span><span class="sxs-lookup"><span data-stu-id="236f3-134">1</span></span>                                    |
| <span data-ttu-id="236f3-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="236f3-135">Default Value</span></span>                        | <span data-ttu-id="236f3-136">pswa</span><span class="sxs-lookup"><span data-stu-id="236f3-136">pswa</span></span>                                 |
| <span data-ttu-id="236f3-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="236f3-138">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-138">false</span></span>                                |
| <span data-ttu-id="236f3-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="236f3-140">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="236f3-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="236f3-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="236f3-142">Gibt den Namen der Website an, auf der die Webanwendung installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="236f3-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="236f3-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="236f3-143">Aliases</span></span>                              | <span data-ttu-id="236f3-144">keine</span><span class="sxs-lookup"><span data-stu-id="236f3-144">none</span></span>                                 |
| <span data-ttu-id="236f3-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="236f3-145">Required?</span></span>                            | <span data-ttu-id="236f3-146">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-146">false</span></span>                                |
| <span data-ttu-id="236f3-147">Position?</span><span class="sxs-lookup"><span data-stu-id="236f3-147">Position?</span></span>                            | <span data-ttu-id="236f3-148">benannt</span><span class="sxs-lookup"><span data-stu-id="236f3-148">named</span></span>                                |
| <span data-ttu-id="236f3-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="236f3-149">Default Value</span></span>                        | <span data-ttu-id="236f3-150">Standardwebsite</span><span class="sxs-lookup"><span data-stu-id="236f3-150">Default Web Site</span></span>                     |
| <span data-ttu-id="236f3-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="236f3-152">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-152">false</span></span>                                |
| <span data-ttu-id="236f3-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="236f3-154">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="236f3-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="236f3-155">-Confirm</span></span>

<span data-ttu-id="236f3-156">Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="236f3-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="236f3-157">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="236f3-157">Required?</span></span>                            | <span data-ttu-id="236f3-158">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-158">false</span></span>                                |
| <span data-ttu-id="236f3-159">Position?</span><span class="sxs-lookup"><span data-stu-id="236f3-159">Position?</span></span>                            | <span data-ttu-id="236f3-160">benannt</span><span class="sxs-lookup"><span data-stu-id="236f3-160">named</span></span>                                |
| <span data-ttu-id="236f3-161">Standardwert</span><span class="sxs-lookup"><span data-stu-id="236f3-161">Default Value</span></span>                        | <span data-ttu-id="236f3-162">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-162">false</span></span>                                |
| <span data-ttu-id="236f3-163">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="236f3-164">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-164">false</span></span>                                |
| <span data-ttu-id="236f3-165">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="236f3-166">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="236f3-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="236f3-167">-WhatIf</span></span>

<span data-ttu-id="236f3-168">Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="236f3-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="236f3-169">Das Cmdlet wird nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="236f3-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="236f3-170">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="236f3-170">Required?</span></span>                            | <span data-ttu-id="236f3-171">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-171">false</span></span>                                |
| <span data-ttu-id="236f3-172">Position?</span><span class="sxs-lookup"><span data-stu-id="236f3-172">Position?</span></span>                            | <span data-ttu-id="236f3-173">benannt</span><span class="sxs-lookup"><span data-stu-id="236f3-173">named</span></span>                                |
| <span data-ttu-id="236f3-174">Standardwert</span><span class="sxs-lookup"><span data-stu-id="236f3-174">Default Value</span></span>                        | <span data-ttu-id="236f3-175">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-175">false</span></span>                                |
| <span data-ttu-id="236f3-176">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="236f3-177">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-177">false</span></span>                                |
| <span data-ttu-id="236f3-178">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="236f3-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="236f3-179">falsch</span><span class="sxs-lookup"><span data-stu-id="236f3-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="236f3-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="236f3-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="236f3-181">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="236f3-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="236f3-182">Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="236f3-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="236f3-183">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="236f3-183">INPUTS</span></span>

<span data-ttu-id="236f3-184">Dieses Cmdlet unterstützt keine Eingabe.</span><span class="sxs-lookup"><span data-stu-id="236f3-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="236f3-185">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="236f3-185">OUTPUTS</span></span>

<span data-ttu-id="236f3-186">Dieses Cmdlet gibt keine Ausgabe zurück.</span><span class="sxs-lookup"><span data-stu-id="236f3-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="236f3-187">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="236f3-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="236f3-188">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="236f3-188">EXAMPLE 1</span></span>

<span data-ttu-id="236f3-189">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="236f3-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="236f3-190">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert haben.</span><span class="sxs-lookup"><span data-stu-id="236f3-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="236f3-191">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="236f3-191">EXAMPLE 2</span></span>

<span data-ttu-id="236f3-192">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung und löscht das der Anwendung zugeordnete Testzertifikat.</span><span class="sxs-lookup"><span data-stu-id="236f3-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="236f3-193">Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert und ein Testzertifikat erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="236f3-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="236f3-194">BEISPIEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="236f3-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="236f3-195">Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung, wenn während der Installation eine benutzerdefinierte Website und Anwendung angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="236f3-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="236f3-196">Dieser Befehl entfernt die Website namens *MySite* und die Anwendung namens *TestApplication*. Außerdem gibt er an, dass die der Anwendung zugeordneten Testzertifikate ebenfalls gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="236f3-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="236f3-197">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="236f3-197">Related topics</span></span>

- [<span data-ttu-id="236f3-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="236f3-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="236f3-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="236f3-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="236f3-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="236f3-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="236f3-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="236f3-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="236f3-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="236f3-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)