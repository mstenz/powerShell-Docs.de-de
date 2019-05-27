---
title: Supportlebenszyklus von PowerShell Core
description: Richtlinien für die Unterstützung von PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854377"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="5353d-103">Supportlebenszyklus von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5353d-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="5353d-104">PowerShell Core ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="5353d-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="5353d-105">PowerShell Core ist nicht in den Lizenzvereinbarungen für Windows 7/8.1/10 oder Windows Server enthalten.</span><span class="sxs-lookup"><span data-stu-id="5353d-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="5353d-106">PowerShell Core wird jedoch von herkömmlichen Microsoft-Supportvereinbarungen unterstützt, einschließlich [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="5353d-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="5353d-107">Sie können auch Hilfe bei der kostenpflichtigen [unterstützten Support][] für PowerShell Core anfordern.</span><span class="sxs-lookup"><span data-stu-id="5353d-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="5353d-108">Communitysupport</span><span class="sxs-lookup"><span data-stu-id="5353d-108">Community Support</span></span>

<span data-ttu-id="5353d-109">Auf GitHub wird Ihnen auch [Communitysupport][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.</span><span class="sxs-lookup"><span data-stu-id="5353d-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="5353d-110">Sie haben auch die Möglichkeit, sich von anderen Mitgliedern aus der allgemeinen [Microsoft Community][] oder der Microsoft [PowerShell Tech Community][] helfen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="5353d-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="5353d-111">Wir bieten keine Garantie, dass die Community Ihr Problem zügig behandelt oder behebt.</span><span class="sxs-lookup"><span data-stu-id="5353d-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="5353d-112">Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.</span><span class="sxs-lookup"><span data-stu-id="5353d-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="5353d-113">Lebenszyklus von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5353d-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="5353d-114">PowerShell Core übernimmt die [Modern Lifecycle-Richtlinie von Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="5353d-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="5353d-115">Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.</span><span class="sxs-lookup"><span data-stu-id="5353d-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="5353d-116">Der Branch von Version 6.x von PowerShell Core wird ungefähr alle sechs Monate aktualisiert (z.B. 6.0, 6.1, 6.2, etc.).</span><span class="sxs-lookup"><span data-stu-id="5353d-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5353d-117">Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5353d-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="5353d-118">Beispiel: Wenn PowerShell Core 6.1 am 1. Juli 2018 freigegeben wird, würde von Ihnen erwartet werden, dass Sie das Update auf PowerShell Core 6.1 bis zum 1. Januar 2019 ausgeführt haben, damit die Unterstützung aufrecht erhalten wird.</span><span class="sxs-lookup"><span data-stu-id="5353d-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5353d-119">Nach jeder Veröffentlichung einer neuen Patchversion müssen Sie PowerShell Core innerhalb von 30 Tagen aktualisieren, um weiterhin Unterstützung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5353d-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="5353d-120">Wenn Sie beispielsweise PowerShell Core 6.1 ausführen, und 6.1.3 wird am 19. Februar 2019 veröffentlicht, würde von Ihnen erwartet, PowerShell Core 6.1.3 bis zum 21. März 2019 zu aktualisieren – also 30 Tage nach der Veröffentlichung – um Support zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5353d-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="5353d-121">Als erforderlich eingestufte Fixes werden in unserem nächsten kumulativen Update veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="5353d-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="5353d-122">Die Modern Lifecycle-Richtlinie gibt auch vor, dass Microsoft 12 Monate im Voraus bekannt geben muss, wenn die Unterstützung eines Produkts (d.h. PowerShell Core) beendet wird.</span><span class="sxs-lookup"><span data-stu-id="5353d-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="5353d-123">Schließlich erwarten wir, dass für PowerShell Core der Ansatz der „langfristigen Wartung“ übernommen wird.</span><span class="sxs-lookup"><span data-stu-id="5353d-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="5353d-124">Dieser Ansatz würde nur Wartungs- und Sicherheitsupdates erfordern, um die Unterstützung eines bestimmten Branchs oder einer bestimmten Version von 6.x aufrecht zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5353d-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="5353d-125">Unterstützte Plattformen</span><span class="sxs-lookup"><span data-stu-id="5353d-125">Supported platforms</span></span>

<span data-ttu-id="5353d-126">In der folgenden Tabelle sehen Sie, welche Plattform für die Version von PowerShell Core, die Sie verwenden, offiziell unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="5353d-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="5353d-127">Unsere Community hat außerdem Pakete für einige Plattformen beigesteuert, die jedoch nicht offiziell unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="5353d-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="5353d-128">Diese Pakete sind in der Tabelle mit `Community` gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="5353d-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="5353d-129">Plattformen, die als `Experimental` gekennzeichnet sind, werden nicht offiziell unterstützt, stehen aber aus Test- und Feedbackzwecken zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="5353d-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="5353d-130">6.1</span><span class="sxs-lookup"><span data-stu-id="5353d-130">6.1</span></span>         | <span data-ttu-id="5353d-131">6.2</span><span class="sxs-lookup"><span data-stu-id="5353d-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="5353d-132">Windows 7, 8.1 und 10</span><span class="sxs-lookup"><span data-stu-id="5353d-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="5353d-133">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-133">Supported</span></span>   | <span data-ttu-id="5353d-134">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-134">Supported</span></span>   |
| <span data-ttu-id="5353d-135">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="5353d-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="5353d-136">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-136">Supported</span></span>   | <span data-ttu-id="5353d-137">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-137">Supported</span></span>   |
| <span data-ttu-id="5353d-138">[Halbjährlicher Kanal von Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="5353d-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="5353d-139">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-139">Supported</span></span>   | <span data-ttu-id="5353d-140">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-140">Supported</span></span>   |
| <span data-ttu-id="5353d-141">Ubuntu 16.04 und 18.04</span><span class="sxs-lookup"><span data-stu-id="5353d-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="5353d-142">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-142">Supported</span></span>   | <span data-ttu-id="5353d-143">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-143">Supported</span></span>   |
| <span data-ttu-id="5353d-144">Ubuntu 18.10 (über Snap-Pakete)</span><span class="sxs-lookup"><span data-stu-id="5353d-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="5353d-145">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-145">Community</span></span>   | <span data-ttu-id="5353d-146">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-146">Community</span></span>   |
| <span data-ttu-id="5353d-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="5353d-147">Debian 9</span></span>                                          | <span data-ttu-id="5353d-148">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-148">Supported</span></span>   | <span data-ttu-id="5353d-149">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-149">Supported</span></span>   |
| <span data-ttu-id="5353d-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5353d-150">CentOS 7</span></span>                                          | <span data-ttu-id="5353d-151">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-151">Supported</span></span>   | <span data-ttu-id="5353d-152">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-152">Supported</span></span>   |
| <span data-ttu-id="5353d-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="5353d-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="5353d-154">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-154">Supported</span></span>   | <span data-ttu-id="5353d-155">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-155">Supported</span></span>   |
| <span data-ttu-id="5353d-156">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="5353d-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="5353d-157">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-157">Supported</span></span>   | <span data-ttu-id="5353d-158">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-158">Supported</span></span>   |
| <span data-ttu-id="5353d-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5353d-159">Fedora 28</span></span>                                         | <span data-ttu-id="5353d-160">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-160">Supported</span></span>   | <span data-ttu-id="5353d-161">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-161">Supported</span></span>   |
| <span data-ttu-id="5353d-162">macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="5353d-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="5353d-163">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-163">Supported</span></span>   | <span data-ttu-id="5353d-164">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="5353d-164">Supported</span></span>   |
| <span data-ttu-id="5353d-165">Arch</span><span class="sxs-lookup"><span data-stu-id="5353d-165">Arch</span></span>                                              | <span data-ttu-id="5353d-166">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-166">Community</span></span>   | <span data-ttu-id="5353d-167">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-167">Community</span></span>   |
| <span data-ttu-id="5353d-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="5353d-168">Raspbian</span></span>                                          | <span data-ttu-id="5353d-169">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-169">Community</span></span>   | <span data-ttu-id="5353d-170">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-170">Community</span></span>   |
| <span data-ttu-id="5353d-171">Kali</span><span class="sxs-lookup"><span data-stu-id="5353d-171">Kali</span></span>                                              | <span data-ttu-id="5353d-172">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-172">Community</span></span>   | <span data-ttu-id="5353d-173">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-173">Community</span></span>   |
| <span data-ttu-id="5353d-174">AppImage (funktioniert auf verschiedenen Linux-Plattformen)</span><span class="sxs-lookup"><span data-stu-id="5353d-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="5353d-175">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-175">Community</span></span>   | <span data-ttu-id="5353d-176">Community</span><span class="sxs-lookup"><span data-stu-id="5353d-176">Community</span></span>   |
| [<span data-ttu-id="5353d-177">Snap-Paket</span><span class="sxs-lookup"><span data-stu-id="5353d-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="5353d-178">Siehe Hinweis</span><span class="sxs-lookup"><span data-stu-id="5353d-178">See note</span></span>    | <span data-ttu-id="5353d-179">Siehe Hinweis</span><span class="sxs-lookup"><span data-stu-id="5353d-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="5353d-180">Snap-Pakete werden genauso unterstützt wie die Distribution, auf der Sie das Paket ausführen.</span><span class="sxs-lookup"><span data-stu-id="5353d-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="5353d-181">Ende der Lebensdauer des PowerShell-Release</span><span class="sxs-lookup"><span data-stu-id="5353d-181">PowerShell release end of life</span></span>

<span data-ttu-id="5353d-182">Basierend auf [Lebenszyklus von PowerShell Core](#lifecycle-of-powershell-core) wird in der folgenden Tabelle für verschiedene Releases das Datum angegeben, ab dem sie nicht mehr unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="5353d-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="5353d-183">Version</span><span class="sxs-lookup"><span data-stu-id="5353d-183">Version</span></span> | <span data-ttu-id="5353d-184">Ende der Lebensdauer</span><span class="sxs-lookup"><span data-stu-id="5353d-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="5353d-185">6.0</span><span class="sxs-lookup"><span data-stu-id="5353d-185">6.0</span></span>     | <span data-ttu-id="5353d-186">13. Februar 2019</span><span class="sxs-lookup"><span data-stu-id="5353d-186">February 13, 2019</span></span>             |
| <span data-ttu-id="5353d-187">6.1</span><span class="sxs-lookup"><span data-stu-id="5353d-187">6.1</span></span>     | <span data-ttu-id="5353d-188">28. September 2019</span><span class="sxs-lookup"><span data-stu-id="5353d-188">September 28, 2019</span></span>            |
| <span data-ttu-id="5353d-189">6.2</span><span class="sxs-lookup"><span data-stu-id="5353d-189">6.2</span></span>     | <span data-ttu-id="5353d-190">6 Monate nach der Veröffentlichung von 7</span><span class="sxs-lookup"><span data-stu-id="5353d-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="5353d-191">Plattformen, die nicht mehr unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="5353d-191">Platforms, which are out of support</span></span>

<span data-ttu-id="5353d-192">Wenn eine Plattformversion das Ende ihrer Lebensdauer (wie vom Plattformbesitzer festgelegt) erreicht, endet auch die Unterstützung von PowerShell Core für diese Plattformversion.</span><span class="sxs-lookup"><span data-stu-id="5353d-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="5353d-193">Bereits veröffentlichte Pakete bleiben weiterhin für Kunden verfügbar, die Zugriff benötigen. Die formelle Unterstützung und reguläre Updates jeglicher Art werden nicht mehr veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="5353d-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="5353d-194">Deshalb haben die Distributionsbesitzer die Unterstützung für die folgenden Versionen beendet.</span><span class="sxs-lookup"><span data-stu-id="5353d-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="5353d-195">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="5353d-195">OS</span></span>       | <span data-ttu-id="5353d-196">Version</span><span class="sxs-lookup"><span data-stu-id="5353d-196">Version</span></span> | <span data-ttu-id="5353d-197">Ende der Lebensdauer</span><span class="sxs-lookup"><span data-stu-id="5353d-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="5353d-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="5353d-198">Fedora</span></span>   | <span data-ttu-id="5353d-199">24</span><span class="sxs-lookup"><span data-stu-id="5353d-199">24</span></span>      | [<span data-ttu-id="5353d-200">August 2017</span><span class="sxs-lookup"><span data-stu-id="5353d-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="5353d-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="5353d-201">Fedora</span></span>   | <span data-ttu-id="5353d-202">25</span><span class="sxs-lookup"><span data-stu-id="5353d-202">25</span></span>      | [<span data-ttu-id="5353d-203">Dezember 2017</span><span class="sxs-lookup"><span data-stu-id="5353d-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="5353d-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="5353d-204">Fedora</span></span>   | <span data-ttu-id="5353d-205">26</span><span class="sxs-lookup"><span data-stu-id="5353d-205">26</span></span>      | [<span data-ttu-id="5353d-206">Mai 2018</span><span class="sxs-lookup"><span data-stu-id="5353d-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="5353d-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5353d-207">openSUSE</span></span> | <span data-ttu-id="5353d-208">42.1</span><span class="sxs-lookup"><span data-stu-id="5353d-208">42.1</span></span>    | [<span data-ttu-id="5353d-209">Mai 2017</span><span class="sxs-lookup"><span data-stu-id="5353d-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="5353d-210">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5353d-210">openSUSE</span></span> | <span data-ttu-id="5353d-211">42.2</span><span class="sxs-lookup"><span data-stu-id="5353d-211">42.2</span></span>    | [<span data-ttu-id="5353d-212">Januar 2018</span><span class="sxs-lookup"><span data-stu-id="5353d-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="5353d-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5353d-213">Ubuntu</span></span>   | <span data-ttu-id="5353d-214">16.10</span><span class="sxs-lookup"><span data-stu-id="5353d-214">16.10</span></span>   | [<span data-ttu-id="5353d-215">Juli 2017</span><span class="sxs-lookup"><span data-stu-id="5353d-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="5353d-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5353d-216">Ubuntu</span></span>   | <span data-ttu-id="5353d-217">17.04</span><span class="sxs-lookup"><span data-stu-id="5353d-217">17.04</span></span>   | [<span data-ttu-id="5353d-218">Januar 2018</span><span class="sxs-lookup"><span data-stu-id="5353d-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="5353d-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5353d-219">Ubuntu</span></span>   | <span data-ttu-id="5353d-220">17.10</span><span class="sxs-lookup"><span data-stu-id="5353d-220">17.10</span></span>   | [<span data-ttu-id="5353d-221">Juli 2018</span><span class="sxs-lookup"><span data-stu-id="5353d-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="5353d-222">Debian</span><span class="sxs-lookup"><span data-stu-id="5353d-222">Debian</span></span>   | <span data-ttu-id="5353d-223">8</span><span class="sxs-lookup"><span data-stu-id="5353d-223">8</span></span>       | [<span data-ttu-id="5353d-224">Juni 2018</span><span class="sxs-lookup"><span data-stu-id="5353d-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="5353d-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="5353d-225">Fedora</span></span>   | <span data-ttu-id="5353d-226">27</span><span class="sxs-lookup"><span data-stu-id="5353d-226">27</span></span>      | [<span data-ttu-id="5353d-227">November 2018</span><span class="sxs-lookup"><span data-stu-id="5353d-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="5353d-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5353d-228">Ubuntu</span></span>   | <span data-ttu-id="5353d-229">14.04</span><span class="sxs-lookup"><span data-stu-id="5353d-229">14.04</span></span>   | [<span data-ttu-id="5353d-230">April 2019</span><span class="sxs-lookup"><span data-stu-id="5353d-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="5353d-231">Hinweise zur Lizenzierung</span><span class="sxs-lookup"><span data-stu-id="5353d-231">Notes on licensing</span></span>

<span data-ttu-id="5353d-232">PowerShell Core wird unter der [MIT-Lizenz][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="5353d-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="5353d-233">Unter dieser Lizenz und ohne kostenpflichtige Supportvereinbarung gibt es für die Benutzer nur den [Communitysupport][].</span><span class="sxs-lookup"><span data-stu-id="5353d-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="5353d-234">Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="5353d-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="5353d-235">Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="5353d-235">Windows PowerShell Module</span></span>

<span data-ttu-id="5353d-236">Der Support für PowerShell Core gilt nicht für andere Produktmodule, es sei denn, diese Module unterstützen PowerShell Core ausdrücklich.</span><span class="sxs-lookup"><span data-stu-id="5353d-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="5353d-237">Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5353d-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="5353d-238">Allerdings können auch Module, die PowerShell Core nicht explizit unterstützen, in manchen Fällen kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="5353d-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="5353d-239">Durch die Installation des Moduls [`WindowsPSModulePath`][] können Sie `PSModulePath` von Windows PowerShell an `PSModulePath` von PowerShell Core anfügen.</span><span class="sxs-lookup"><span data-stu-id="5353d-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="5353d-240">Installieren Sie zunächst das `WindowsPSModulePath`-Modul aus dem PowerShell-Katalog:</span><span class="sxs-lookup"><span data-stu-id="5353d-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="5353d-241">Führen Sie nach der Installation dieses Moduls das Cmdlet `Add-WindowsPSModulePath` aus, um `PSModulePath` aus Windows PowerShell zu PowerShell Core hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="5353d-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="5353d-242">Experimentelle Features</span><span class="sxs-lookup"><span data-stu-id="5353d-242">Experimental features</span></span>

<span data-ttu-id="5353d-243">[Experimentelle Features][] sind auf [Communitysupport](#community-support) begrenzt.</span><span class="sxs-lookup"><span data-stu-id="5353d-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
[Experimentelle Features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
