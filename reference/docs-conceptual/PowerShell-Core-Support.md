# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="6cc60-101">Supportlebenszyklus von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6cc60-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="6cc60-102">PowerShell Core ist eine Zusammenstellung von Tools und Komponenten, die separat von Windows PowerShell bereitgestellt, installiert und konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="6cc60-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="6cc60-103">PowerShell Core ist daher nicht in den Lizenzvereinbarungen für Windows 7/8.1/10 oder Windows Server enthalten.</span><span class="sxs-lookup"><span data-stu-id="6cc60-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="6cc60-104">PowerShell Core wird jedoch von herkömmlichen Microsoft-Supportvereinbarungen unterstützt, einschließlich [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement] und [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="6cc60-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="6cc60-105">Sie können auch Hilfe bei der kostenpflichtigen [assisted support (Unterstützter Support)][] für PowerShell Core anfordern.</span><span class="sxs-lookup"><span data-stu-id="6cc60-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="6cc60-106">Auf GitHub wird Ihnen auch [community support (Communitysupport)][] geboten. Dort können Sie Tickets zu Problemen, Fehlern oder Funktionsanfragen stellen.</span><span class="sxs-lookup"><span data-stu-id="6cc60-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="6cc60-107">Alternativ haben Sie die Möglichkeit, sich von anderen Mitgliedern aus der allgemeinen [Microsoft Community][] oder der Microsoft [PowerShell Tech Community][] helfen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="6cc60-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="6cc60-108">Wir bieten keine Garantie, dass ihr Problem zügig behandelt oder behoben wird.</span><span class="sxs-lookup"><span data-stu-id="6cc60-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="6cc60-109">Wenn Sie ein Problem haben, das unmittelbar Aufmerksamkeit erfordert, sollten Sie sich an die herkömmlichen kostenpflichtigen Supportoptionen wenden.</span><span class="sxs-lookup"><span data-stu-id="6cc60-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="6cc60-110">Lebenszyklus von PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6cc60-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="6cc60-111">PowerShell Core übernimmt die [Modern Lifecycle-Richtlinie von Microsoft][modern].</span><span class="sxs-lookup"><span data-stu-id="6cc60-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="6cc60-112">Dieser Supportlebenszyklus soll Kunden mit den aktuellsten Versionen auf dem neuesten Stand halten.</span><span class="sxs-lookup"><span data-stu-id="6cc60-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="6cc60-113">Der Branch von Version 6.x von PowerShell Core wird ungefähr alle sechs Monate aktualisiert (z.B. 6.0, 6.1, 6.2, usw.)</span><span class="sxs-lookup"><span data-stu-id="6cc60-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6cc60-114">Nach jeder neuen kleinen Versionsfreigabe müssen Sie PowerShell Core innerhalb von sechs Monaten aktualisieren, um weiterhin Unterstützung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6cc60-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="6cc60-115">Beispiel: Wenn PowerShell Core 6.1 am 1. Juli 2018 freigegeben wird, würde von Ihnen erwartet werden, dass Sie das Update auf PowerShell Core 6.1 bis zum 1. Januar 2019 ausgeführt haben, damit die Unterstützung aufrecht erhalten wird.</span><span class="sxs-lookup"><span data-stu-id="6cc60-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![Lebenszyklus des PowerShell Core-Branchs][lifecycle-chart]

<span data-ttu-id="6cc60-117">Die Modern Lifecycle-Richtlinie gibt auch vor, dass Microsoft 12 Monate im Voraus bekannt geben muss, wenn die Unterstützung eines Produkts beendet wird (d.h. PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="6cc60-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="6cc60-118">Letztendlich wird erwartet, dass PowerShell Core den Ansatz der „langfristigen Wartung“ übernimmt, wodurch nur Wartungs- und Sicherheitsupdates erfordert werden, um die Unterstützung eines bestimmten Branchs oder einer bestimmten Version von 6.x aufrecht zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="6cc60-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="6cc60-119">Unterstützte Plattformen</span><span class="sxs-lookup"><span data-stu-id="6cc60-119">Supported platforms</span></span>

<span data-ttu-id="6cc60-120">PowerShell Core wird offiziell auf folgenden Plattformen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="6cc60-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="6cc60-121">Windows 7, 8.1 und 10</span><span class="sxs-lookup"><span data-stu-id="6cc60-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="6cc60-122">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="6cc60-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="6cc60-123">[Halbjährlicher Kanal von Windows Server][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="6cc60-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="6cc60-124">Ubuntu 14.04, 16.04 und 17.04</span><span class="sxs-lookup"><span data-stu-id="6cc60-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="6cc60-125">Debian 8.7 und höher sowie Debian 9</span><span class="sxs-lookup"><span data-stu-id="6cc60-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="6cc60-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6cc60-126">CentOS 7</span></span>
* <span data-ttu-id="6cc60-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="6cc60-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="6cc60-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="6cc60-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="6cc60-129">Fedora 27, 28</span><span class="sxs-lookup"><span data-stu-id="6cc60-129">Fedora 27, 28</span></span>
* <span data-ttu-id="6cc60-130">macOS 10.12 und höher</span><span class="sxs-lookup"><span data-stu-id="6cc60-130">macOS 10.12+</span></span>

<span data-ttu-id="6cc60-131">Unsere Community hat außerdem Pakete für die folgenden Plattformen veröffentlicht, die jedoch nicht offiziell unterstützt werden:</span><span class="sxs-lookup"><span data-stu-id="6cc60-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="6cc60-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="6cc60-132">Arch Linux</span></span>
* <span data-ttu-id="6cc60-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="6cc60-133">Kali Linux</span></span>
* <span data-ttu-id="6cc60-134">AppImage (funktioniert auf verschiedenen Linux-Plattformen)</span><span class="sxs-lookup"><span data-stu-id="6cc60-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="6cc60-135">Hinweise zur Lizenzierung</span><span class="sxs-lookup"><span data-stu-id="6cc60-135">Notes on licensing</span></span>

<span data-ttu-id="6cc60-136">PowerShell Core wird unter der [MIT license (MIT-Lizenz)][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="6cc60-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="6cc60-137">Unter dieser Lizenz und in Abwesenheit einer kostenpflichtigen Supportvereinbarung gibt es für die Benutzer nur den [community support (Communitysupport)][].</span><span class="sxs-lookup"><span data-stu-id="6cc60-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="6cc60-138">Beim Support durch die Community gibt Microsoft keine Garantien zur Schnelligkeit der Reaktion auf Ihre Tickets oder der Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="6cc60-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="6cc60-139">Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="6cc60-139">Windows PowerShell Module</span></span>

<span data-ttu-id="6cc60-140">Die Unterstützung von PowerShell Core gilt nicht für andere Produktmodule, es sei denn, diese Module unterstützen PowerShell Core ausdrücklich.</span><span class="sxs-lookup"><span data-stu-id="6cc60-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="6cc60-141">Zum Beispiel wird das Modul `ActiveDirectory`, das als Teil von Windows Server bereitgestellt wird, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6cc60-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="6cc60-142">Allerdings können auch Module, die PowerShell Core nicht explizit unterstützen, in manchen Fällen kompatibel sein.</span><span class="sxs-lookup"><span data-stu-id="6cc60-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="6cc60-143">Durch die Installation des Moduls [`WindowsPSModulePath`][] können Sie `PSModulePath` von Windows PowerShell an `PSModulePath` von PowerShell Core anfügen.</span><span class="sxs-lookup"><span data-stu-id="6cc60-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="6cc60-144">Installieren Sie zunächst das `WindowsPSModulePath`-Modul aus dem PowerShell-Katalog:</span><span class="sxs-lookup"><span data-stu-id="6cc60-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="6cc60-145">Führen Sie nach der Installation dieses Moduls das Cmdlet `Add-WindowsPSModulePath` aus, um `PSModulePath` aus Windows PowerShell zu PowerShell Core hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="6cc60-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[community support (Communitysupport)]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[assisted support (Unterstützter Support)]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT license (MIT-Lizenz)]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
