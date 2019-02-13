---
title: Supportlebenszyklus von PowerShell Core
description: Richtlinien für die Unterstützung von PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: cb1daf953b11ffba8f39bcc05a8b122350c497eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679453"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="5db2d-103">Supportlebenszyklus von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5db2d-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="5db2d-104">PowerShell Core ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="5db2d-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="5db2d-105">PowerShell Core ist daher nicht in die Windows 7/8.1/10 oder Windows Server-Lizenzbedingungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="5db2d-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="5db2d-106">PowerShell Core wird jedoch von herkömmlichen Microsoft-Supportvereinbarungen unterstützt, einschließlich [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="5db2d-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="5db2d-107">Sie können auch Hilfe bei der kostenpflichtigen [unterstützten Support][] für PowerShell Core anfordern.</span><span class="sxs-lookup"><span data-stu-id="5db2d-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="5db2d-108">Auf GitHub wird Ihnen auch [Communitysupport][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.</span><span class="sxs-lookup"><span data-stu-id="5db2d-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="5db2d-109">Darüber hinaus können Sie Hilfe von anderen Mitgliedern der Community finden Sie auf der Seite Allgemein [Microsoft Community][] oder der Microsoft [PowerShell Tech Community][].</span><span class="sxs-lookup"><span data-stu-id="5db2d-109">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="5db2d-110">Wir bieten keine Garantie, dass die Community zu beheben oder Ihr Problem zu, rechtzeitig beheben wird.</span><span class="sxs-lookup"><span data-stu-id="5db2d-110">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="5db2d-111">Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.</span><span class="sxs-lookup"><span data-stu-id="5db2d-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="5db2d-112">Lebenszyklus von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5db2d-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="5db2d-113">PowerShell Core übernimmt die [Modern Lifecycle-Richtlinie von Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="5db2d-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="5db2d-114">Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.</span><span class="sxs-lookup"><span data-stu-id="5db2d-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="5db2d-115">Branch von Version 6.x von PowerShell Core wird ungefähr alle sechs Monate aktualisiert (Beispiele: 6.0, 6.1, 6.2, usw..)</span><span class="sxs-lookup"><span data-stu-id="5db2d-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5db2d-116">Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5db2d-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="5db2d-117">Z. B. Wenn Sie PowerShell Core 6.1 am 1. Juli 2018 veröffentlicht wird würde von Ihnen erwartet werden zum Aktualisieren von auf PowerShell Core 6.1 am 1. Januar 2019 um Support zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5db2d-117">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

![Lebenszyklus des PowerShell Core-Branchs][lifecycle-chart]

<span data-ttu-id="5db2d-119">Modern Lifecycle-Richtlinie erfordert auch, dass Microsoft Kunden 12 Monate im Voraus geben vor, stellt die Unterstützung für ein Produkt (d.h. PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="5db2d-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="5db2d-120">Schließlich wir erwarten, dass PowerShell Core übernimmt der "langfristigen Wartung" Ansatz.</span><span class="sxs-lookup"><span data-stu-id="5db2d-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="5db2d-121">Bei diesem Ansatz servicing müssten wir nur Wartungs- und Sicherheitsupdates Updates, bei der Unterstützung von einer bestimmten Branch/Version von 6.x aufrecht zu bleiben.</span><span class="sxs-lookup"><span data-stu-id="5db2d-121">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="5db2d-122">Unterstützte Plattformen</span><span class="sxs-lookup"><span data-stu-id="5db2d-122">Supported platforms</span></span>

<span data-ttu-id="5db2d-123">Auf welcher Plattform, die Sie verwenden die Version von PowerShell Core finden in der folgende Tabelle wird offiziell unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5db2d-123">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="5db2d-124">Unsere Community hat außerdem Pakete für einige Plattformen beigesteuert, die jedoch nicht offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="5db2d-124">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="5db2d-125">Diese Pakete sind in der Tabelle mit `Community` gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="5db2d-125">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="5db2d-126">Plattformen, die als `Experimental` gekennzeichnet sind, werden nicht offiziell unterstützt, stehen aber aus Test- und Feedbackzwecken zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="5db2d-126">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="5db2d-127">6.0</span><span class="sxs-lookup"><span data-stu-id="5db2d-127">6.0</span></span>         | <span data-ttu-id="5db2d-128">6.1</span><span class="sxs-lookup"><span data-stu-id="5db2d-128">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="5db2d-129">Windows 7, 8.1 und 10</span><span class="sxs-lookup"><span data-stu-id="5db2d-129">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="5db2d-130">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-130">Supported</span></span>   | <span data-ttu-id="5db2d-131">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-131">Supported</span></span>   |
| <span data-ttu-id="5db2d-132">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="5db2d-132">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="5db2d-133">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-133">Supported</span></span>   | <span data-ttu-id="5db2d-134">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-134">Supported</span></span>   |
| <span data-ttu-id="5db2d-135">[Halbjährlicher Kanal von Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="5db2d-135">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="5db2d-136">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-136">Supported</span></span>   | <span data-ttu-id="5db2d-137">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-137">Supported</span></span>   |
| <span data-ttu-id="5db2d-138">Ubuntu 14.04 und 16.04</span><span class="sxs-lookup"><span data-stu-id="5db2d-138">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="5db2d-139">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-139">Supported</span></span>   | <span data-ttu-id="5db2d-140">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-140">Supported</span></span>   |
| <span data-ttu-id="5db2d-141">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5db2d-141">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="5db2d-142">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-142">Supported</span></span>   |
| <span data-ttu-id="5db2d-143">Ubuntu 18.10 (über Snap-Pakete)</span><span class="sxs-lookup"><span data-stu-id="5db2d-143">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="5db2d-144">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-144">Community</span></span>   |
| <span data-ttu-id="5db2d-145">Debian 9</span><span class="sxs-lookup"><span data-stu-id="5db2d-145">Debian 9</span></span>                                          | <span data-ttu-id="5db2d-146">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-146">Supported</span></span>   | <span data-ttu-id="5db2d-147">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-147">Supported</span></span>   |
| <span data-ttu-id="5db2d-148">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5db2d-148">CentOS 7</span></span>                                          | <span data-ttu-id="5db2d-149">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-149">Supported</span></span>   | <span data-ttu-id="5db2d-150">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-150">Supported</span></span>   |
| <span data-ttu-id="5db2d-151">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="5db2d-151">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="5db2d-152">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-152">Supported</span></span>   | <span data-ttu-id="5db2d-153">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-153">Supported</span></span>   |
| <span data-ttu-id="5db2d-154">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="5db2d-154">openSUSE 42.3</span></span>                                     | <span data-ttu-id="5db2d-155">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-155">Supported</span></span>   | <span data-ttu-id="5db2d-156">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-156">Supported</span></span>   |
| <span data-ttu-id="5db2d-157">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5db2d-157">Fedora 28</span></span>                                         |             | <span data-ttu-id="5db2d-158">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-158">Supported</span></span>   |
| <span data-ttu-id="5db2d-159">macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="5db2d-159">macOS 10.12+</span></span>                                      | <span data-ttu-id="5db2d-160">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-160">Supported</span></span>   | <span data-ttu-id="5db2d-161">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5db2d-161">Supported</span></span>   |
| <span data-ttu-id="5db2d-162">Arch</span><span class="sxs-lookup"><span data-stu-id="5db2d-162">Arch</span></span>                                              | <span data-ttu-id="5db2d-163">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-163">Community</span></span>   | <span data-ttu-id="5db2d-164">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-164">Community</span></span>   |
| <span data-ttu-id="5db2d-165">Raspbian</span><span class="sxs-lookup"><span data-stu-id="5db2d-165">Raspbian</span></span>                                          | <span data-ttu-id="5db2d-166">Experimentell</span><span class="sxs-lookup"><span data-stu-id="5db2d-166">Experimental</span></span>| <span data-ttu-id="5db2d-167">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-167">Community</span></span>   |
| <span data-ttu-id="5db2d-168">Kali</span><span class="sxs-lookup"><span data-stu-id="5db2d-168">Kali</span></span>                                              | <span data-ttu-id="5db2d-169">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-169">Community</span></span>   | <span data-ttu-id="5db2d-170">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-170">Community</span></span>   |
| <span data-ttu-id="5db2d-171">AppImage (funktioniert auf verschiedenen Linux-Plattformen)</span><span class="sxs-lookup"><span data-stu-id="5db2d-171">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="5db2d-172">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-172">Community</span></span>   | <span data-ttu-id="5db2d-173">Community</span><span class="sxs-lookup"><span data-stu-id="5db2d-173">Community</span></span>   |
| [<span data-ttu-id="5db2d-174">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="5db2d-174">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="5db2d-175">Siehe Hinweis</span><span class="sxs-lookup"><span data-stu-id="5db2d-175">See note</span></span>    | <span data-ttu-id="5db2d-176">Siehe Hinweis</span><span class="sxs-lookup"><span data-stu-id="5db2d-176">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="5db2d-177">Die Verwendung von Snap-Paketen wird für einen gewissen Zeitraum getestet.</span><span class="sxs-lookup"><span data-stu-id="5db2d-177">Snap packages will be experimental for a period.</span></span>
> <span data-ttu-id="5db2d-178">Nach dieser Testphase sollten Snap-Pakete nicht zu neuen Supportanfragen führen. Die Unterstützung richtet sich nach der Distribution, auf der Sie das Paket ausführen.</span><span class="sxs-lookup"><span data-stu-id="5db2d-178">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="5db2d-179">PowerShell Version Ende ihrer Lebensdauer</span><span class="sxs-lookup"><span data-stu-id="5db2d-179">PowerShell release end of life</span></span>

<span data-ttu-id="5db2d-180">Basierend auf [Lebenszyklus von PowerShell Core](#lifecycle-of-powershell-core), die folgende Tabelle enthält die Datumsangaben, die bei verschiedenen Version wird nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5db2d-180">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="5db2d-181">Version</span><span class="sxs-lookup"><span data-stu-id="5db2d-181">Version</span></span> | <span data-ttu-id="5db2d-182">Ende der Lebensdauer</span><span class="sxs-lookup"><span data-stu-id="5db2d-182">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="5db2d-183">6.0</span><span class="sxs-lookup"><span data-stu-id="5db2d-183">6.0</span></span>     | <span data-ttu-id="5db2d-184">13 Februar 2019</span><span class="sxs-lookup"><span data-stu-id="5db2d-184">February 13, 2019</span></span>             |
| <span data-ttu-id="5db2d-185">6.1</span><span class="sxs-lookup"><span data-stu-id="5db2d-185">6.1</span></span>     | <span data-ttu-id="5db2d-186">6 Monate nach 6.2-Versionen</span><span class="sxs-lookup"><span data-stu-id="5db2d-186">6 Months after 6.2 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="5db2d-187">Plattformen, die nicht mehr unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="5db2d-187">Platforms, which are out of support</span></span>

<span data-ttu-id="5db2d-188">Wenn eine Version der End-of-Life-erreicht, gemäß der durch den Besitzer der Plattform, beendet auch PowerShell Core unterstützt diese Plattformversion.</span><span class="sxs-lookup"><span data-stu-id="5db2d-188">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="5db2d-189">Bereits veröffentlichte Pakete bleiben weiterhin für Kunden verfügbar, die Zugriff benötigen. Die formelle Unterstützung und reguläre Updates jeglicher Art werden nicht mehr veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="5db2d-189">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="5db2d-190">Die Besitzer der Verteilung wird also beendet die Unterstützung für die folgenden Versionen und werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5db2d-190">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="5db2d-191">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="5db2d-191">OS</span></span>       | <span data-ttu-id="5db2d-192">Version</span><span class="sxs-lookup"><span data-stu-id="5db2d-192">Version</span></span> | <span data-ttu-id="5db2d-193">Ende der Lebensdauer</span><span class="sxs-lookup"><span data-stu-id="5db2d-193">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="5db2d-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="5db2d-194">Fedora</span></span>   | <span data-ttu-id="5db2d-195">24</span><span class="sxs-lookup"><span data-stu-id="5db2d-195">24</span></span>      | [<span data-ttu-id="5db2d-196">August 2017</span><span class="sxs-lookup"><span data-stu-id="5db2d-196">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="5db2d-197">Fedora</span><span class="sxs-lookup"><span data-stu-id="5db2d-197">Fedora</span></span>   | <span data-ttu-id="5db2d-198">25</span><span class="sxs-lookup"><span data-stu-id="5db2d-198">25</span></span>      | [<span data-ttu-id="5db2d-199">Dezember 2017</span><span class="sxs-lookup"><span data-stu-id="5db2d-199">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="5db2d-200">Fedora</span><span class="sxs-lookup"><span data-stu-id="5db2d-200">Fedora</span></span>   | <span data-ttu-id="5db2d-201">26</span><span class="sxs-lookup"><span data-stu-id="5db2d-201">26</span></span>      | [<span data-ttu-id="5db2d-202">Mai 2018</span><span class="sxs-lookup"><span data-stu-id="5db2d-202">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="5db2d-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5db2d-203">openSUSE</span></span> | <span data-ttu-id="5db2d-204">42.1</span><span class="sxs-lookup"><span data-stu-id="5db2d-204">42.1</span></span>    | [<span data-ttu-id="5db2d-205">Mai 2017</span><span class="sxs-lookup"><span data-stu-id="5db2d-205">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="5db2d-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5db2d-206">openSUSE</span></span> | <span data-ttu-id="5db2d-207">42.2</span><span class="sxs-lookup"><span data-stu-id="5db2d-207">42.2</span></span>    | [<span data-ttu-id="5db2d-208">Januar 2018</span><span class="sxs-lookup"><span data-stu-id="5db2d-208">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="5db2d-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5db2d-209">Ubuntu</span></span>   | <span data-ttu-id="5db2d-210">16.10</span><span class="sxs-lookup"><span data-stu-id="5db2d-210">16.10</span></span>   | [<span data-ttu-id="5db2d-211">Juli 2017</span><span class="sxs-lookup"><span data-stu-id="5db2d-211">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="5db2d-212">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5db2d-212">Ubuntu</span></span>   | <span data-ttu-id="5db2d-213">17.04</span><span class="sxs-lookup"><span data-stu-id="5db2d-213">17.04</span></span>   | [<span data-ttu-id="5db2d-214">Januar 2018</span><span class="sxs-lookup"><span data-stu-id="5db2d-214">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="5db2d-215">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5db2d-215">Ubuntu</span></span>   | <span data-ttu-id="5db2d-216">17.10</span><span class="sxs-lookup"><span data-stu-id="5db2d-216">17.10</span></span>   | [<span data-ttu-id="5db2d-217">Juli 2018</span><span class="sxs-lookup"><span data-stu-id="5db2d-217">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="5db2d-218">Debian</span><span class="sxs-lookup"><span data-stu-id="5db2d-218">Debian</span></span>   | <span data-ttu-id="5db2d-219">8</span><span class="sxs-lookup"><span data-stu-id="5db2d-219">8</span></span>       | [<span data-ttu-id="5db2d-220">Juni 2018</span><span class="sxs-lookup"><span data-stu-id="5db2d-220">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="5db2d-221">Fedora</span><span class="sxs-lookup"><span data-stu-id="5db2d-221">Fedora</span></span>   | <span data-ttu-id="5db2d-222">27</span><span class="sxs-lookup"><span data-stu-id="5db2d-222">27</span></span>      | [<span data-ttu-id="5db2d-223">November 2018</span><span class="sxs-lookup"><span data-stu-id="5db2d-223">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |

## <a name="notes-on-licensing"></a><span data-ttu-id="5db2d-224">Hinweise zur Lizenzierung</span><span class="sxs-lookup"><span data-stu-id="5db2d-224">Notes on licensing</span></span>

<span data-ttu-id="5db2d-225">PowerShell Core wird unter der [MIT-Lizenz][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="5db2d-225">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="5db2d-226">Unter dieser Lizenz und ohne einer kostenpflichtigen supportvereinbarung, sind Benutzer auf [Communitysupport][].</span><span class="sxs-lookup"><span data-stu-id="5db2d-226">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="5db2d-227">Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="5db2d-227">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="5db2d-228">Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="5db2d-228">Windows PowerShell Module</span></span>

<span data-ttu-id="5db2d-229">Unterstützung für PowerShell Core die Produktmodule, es sei denn, diese Module PowerShell Core ausdrücklich unterstützen nicht enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="5db2d-229">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="5db2d-230">Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5db2d-230">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="5db2d-231">Allerdings können auch Module, die PowerShell Core nicht explizit unterstützen, in manchen Fällen kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="5db2d-231">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="5db2d-232">Durch die Installation der [ `WindowsPSModulePath` ][] -Modul können Sie die Windows PowerShell hinzufügen `PSModulePath` in Ihre PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="5db2d-232">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="5db2d-233">Installieren Sie zunächst das `WindowsPSModulePath`-Modul aus dem PowerShell-Katalog:</span><span class="sxs-lookup"><span data-stu-id="5db2d-233">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="5db2d-234">Führen Sie nach der Installation dieses Moduls das Cmdlet `Add-WindowsPSModulePath` aus, um `PSModulePath` aus Windows PowerShell zu PowerShell Core hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="5db2d-234">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Communitysupport]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[unterstützten Support]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-Lizenz]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
