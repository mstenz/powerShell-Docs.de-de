---
title: Neuigkeiten in PowerShell Core 6.1
description: Neue Funktionen und Änderungen in PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086105"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="d73c3-103">Neuigkeiten in PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="d73c3-104">Im Folgenden finden Sie eine Auswahl der wichtigsten Funktionen und Änderungen, die in PowerShell Core 6.1 eingeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="d73c3-105">Außerdem wurden viele Fehler behoben und **unzählige Verbesserungen** vorgenommen, die PowerShell schneller und stabiler machen, aber vielleicht weniger aufregend klingen.</span><span class="sxs-lookup"><span data-stu-id="d73c3-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="d73c3-106">Eine vollständige Liste der Änderungen finden Sie unter [Changelog (Änderungsprotokoll)](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="d73c3-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="d73c3-107">Ein großer Dank geht an alle [Mitwirkende aus der Community](https://github.com/PowerShell/PowerShell/graphs/contributors), die dieses Release überhaupt möglich gemacht haben, und von denen weiter unten nur eine kleine Auswahl genannt wird.</span><span class="sxs-lookup"><span data-stu-id="d73c3-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="d73c3-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-108">.NET Core 2.1</span></span>

<span data-ttu-id="d73c3-109">PowerShell Core 6.1 wurde nach der [Veröffentlichung im Mai](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) zu .NET Core 2.1 verschoben, wodurch sich u.a. folgende Verbesserungen für PowerShell ergeben:</span><span class="sxs-lookup"><span data-stu-id="d73c3-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="d73c3-110">Leistungsverbesserungen (siehe [unten](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="d73c3-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="d73c3-111">Unterstützung von Alpine Linux (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="d73c3-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="d73c3-112">[Globale Toolunterstützung für .NET](/dotnet/core/tools/global-tools) – Demnächst für PowerShell verfügbar</span><span class="sxs-lookup"><span data-stu-id="d73c3-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="d73c3-113">Windows Compatibility Pack für .NET Core</span><span class="sxs-lookup"><span data-stu-id="d73c3-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="d73c3-114">Im Lieferumfang war unter Windows das [Windows Compatibility Pack für .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/) enthalten, das aus verschiedenen Assemblys besteht, mit denen .NET Core unter Windows einige entfernte APIs wieder hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="d73c3-115">Nun wurde das Windows Compatibility Pack dem Release von PowerShell Core 6.1 hinzugefügt, damit diese APIs für alle Module oder Skripts, die sie verwenden, auch verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d73c3-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="d73c3-116">Durch das Windows Compatibility Pack kann PowerShell Core **mehr als 1.900 Cmdlets verwenden, die im Windows Update vom 10. Oktober 2018 und in Windows Server 2019 enthalten sind**.</span><span class="sxs-lookup"><span data-stu-id="d73c3-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-whitelisting"></a><span data-ttu-id="d73c3-117">Unterstützung für Anwendungswhitelists</span><span class="sxs-lookup"><span data-stu-id="d73c3-117">Support for Application Whitelisting</span></span>

<span data-ttu-id="d73c3-118">PowerShell Core 6.1 verfügt über dieselbe Unterstützung für Anwendungswhitelists von [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) und [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) wie Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="d73c3-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application whitelisting.</span></span>
<span data-ttu-id="d73c3-119">Mit Anwendungswhitelists können Sie detailliert steuern, welche Binärdateien ausgeführt werden dürfen, wenn PowerShell im [eingeschränkten Sprachmodus](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d73c3-119">Application whitelisting allows granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="d73c3-120">Leistungsverbesserungen</span><span class="sxs-lookup"><span data-stu-id="d73c3-120">Performance improvements</span></span>

<span data-ttu-id="d73c3-121">PowerShell Core 6.0 enthielt bereits einige bedeutende Leistungsverbesserungen.</span><span class="sxs-lookup"><span data-stu-id="d73c3-121">PowerShell Core 6.0 made some significant performance improvements.</span></span>
<span data-ttu-id="d73c3-122">PowerShell Core 6.1 erhöht nun die Geschwindigkeit bestimmter Vorgänge noch weiter.</span><span class="sxs-lookup"><span data-stu-id="d73c3-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="d73c3-123">So wurde beispielsweise die Geschwindigkeit von `Group-Object` um 66 % gesteigert:</span><span class="sxs-lookup"><span data-stu-id="d73c3-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | <span data-ttu-id="d73c3-124">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-124">Windows PowerShell 5.1</span></span> | <span data-ttu-id="d73c3-125">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="d73c3-125">PowerShell Core 6.0</span></span> | <span data-ttu-id="d73c3-126">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-126">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="d73c3-127">Zeit (in Sek.)</span><span class="sxs-lookup"><span data-stu-id="d73c3-127">Time (sec)</span></span>   | <span data-ttu-id="d73c3-128">25,178</span><span class="sxs-lookup"><span data-stu-id="d73c3-128">25.178</span></span>                 | <span data-ttu-id="d73c3-129">19,653</span><span class="sxs-lookup"><span data-stu-id="d73c3-129">19.653</span></span>              | <span data-ttu-id="d73c3-130">6,641</span><span class="sxs-lookup"><span data-stu-id="d73c3-130">6.641</span></span>               |
| <span data-ttu-id="d73c3-131">Beschleunigung (in %)</span><span class="sxs-lookup"><span data-stu-id="d73c3-131">Speed-up (%)</span></span> | <span data-ttu-id="d73c3-132">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d73c3-132">N/A</span></span>                    | <span data-ttu-id="d73c3-133">21,9 %</span><span class="sxs-lookup"><span data-stu-id="d73c3-133">21.9%</span></span>               | <span data-ttu-id="d73c3-134">66,2 %</span><span class="sxs-lookup"><span data-stu-id="d73c3-134">66.2%</span></span>               |

<span data-ttu-id="d73c3-135">Auf ähnliche Weise wurden auch Sortierszenarios wie etwa das folgende um mehr als 15 % verbessert:</span><span class="sxs-lookup"><span data-stu-id="d73c3-135">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | <span data-ttu-id="d73c3-136">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-136">Windows PowerShell 5.1</span></span> | <span data-ttu-id="d73c3-137">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="d73c3-137">PowerShell Core 6.0</span></span> | <span data-ttu-id="d73c3-138">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-138">PowerShell Core 6.1</span></span> |
|--------------|------------------------|---------------------|---------------------|
| <span data-ttu-id="d73c3-139">Zeit (in Sek.)</span><span class="sxs-lookup"><span data-stu-id="d73c3-139">Time (sec)</span></span>   | <span data-ttu-id="d73c3-140">12,170</span><span class="sxs-lookup"><span data-stu-id="d73c3-140">12.170</span></span>                 | <span data-ttu-id="d73c3-141">8,493</span><span class="sxs-lookup"><span data-stu-id="d73c3-141">8.493</span></span>               | <span data-ttu-id="d73c3-142">7,08</span><span class="sxs-lookup"><span data-stu-id="d73c3-142">7.08</span></span>                |
| <span data-ttu-id="d73c3-143">Beschleunigung (in %)</span><span class="sxs-lookup"><span data-stu-id="d73c3-143">Speed-up (%)</span></span> | <span data-ttu-id="d73c3-144">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d73c3-144">N/A</span></span>                    | <span data-ttu-id="d73c3-145">30,2 %</span><span class="sxs-lookup"><span data-stu-id="d73c3-145">30.2%</span></span>               | <span data-ttu-id="d73c3-146">16,6 %</span><span class="sxs-lookup"><span data-stu-id="d73c3-146">16.6%</span></span>               |

<span data-ttu-id="d73c3-147">Auch `Import-Csv` wurde nach Regression durch Windows PowerShell deutlich schneller.</span><span class="sxs-lookup"><span data-stu-id="d73c3-147">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="d73c3-148">Im folgenden Beispiel wird eine CSV-Testdatei mit 26.616 Zeilen und sechs Spalten verwendet:</span><span class="sxs-lookup"><span data-stu-id="d73c3-148">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | <span data-ttu-id="d73c3-149">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-149">Windows PowerShell 5.1</span></span> | <span data-ttu-id="d73c3-150">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="d73c3-150">PowerShell Core 6.0</span></span> | <span data-ttu-id="d73c3-151">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-151">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="d73c3-152">Zeit (in Sek.)</span><span class="sxs-lookup"><span data-stu-id="d73c3-152">Time (sec)</span></span>   | <span data-ttu-id="d73c3-153">0,441</span><span class="sxs-lookup"><span data-stu-id="d73c3-153">0.441</span></span>                  | <span data-ttu-id="d73c3-154">1,069</span><span class="sxs-lookup"><span data-stu-id="d73c3-154">1.069</span></span>               | <span data-ttu-id="d73c3-155">0,268</span><span class="sxs-lookup"><span data-stu-id="d73c3-155">0.268</span></span>                  |
| <span data-ttu-id="d73c3-156">Beschleunigung (in %)</span><span class="sxs-lookup"><span data-stu-id="d73c3-156">Speed-up (%)</span></span> | <span data-ttu-id="d73c3-157">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d73c3-157">N/A</span></span>                    | <span data-ttu-id="d73c3-158">–142,4 %</span><span class="sxs-lookup"><span data-stu-id="d73c3-158">-142.4%</span></span>             | <span data-ttu-id="d73c3-159">74,9 % (39,2 % im Vergleich zu WPS)</span><span class="sxs-lookup"><span data-stu-id="d73c3-159">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="d73c3-160">Letztendlich wurde die Konvertierung von JSON in `PSObject` um mehr als 50 % im Vergleich zu Windows PowerShell beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-160">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="d73c3-161">Im folgenden Beispiel wird eine JSON-Testdatei mit einer Größe von etwa 2 MB verwendet:</span><span class="sxs-lookup"><span data-stu-id="d73c3-161">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | <span data-ttu-id="d73c3-162">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-162">Windows PowerShell 5.1</span></span> | <span data-ttu-id="d73c3-163">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="d73c3-163">PowerShell Core 6.0</span></span> | <span data-ttu-id="d73c3-164">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="d73c3-164">PowerShell Core 6.1</span></span>    |
|--------------|------------------------|---------------------|------------------------|
| <span data-ttu-id="d73c3-165">Zeit (in Sek.)</span><span class="sxs-lookup"><span data-stu-id="d73c3-165">Time (sec)</span></span>   | <span data-ttu-id="d73c3-166">0,259</span><span class="sxs-lookup"><span data-stu-id="d73c3-166">0.259</span></span>                  | <span data-ttu-id="d73c3-167">0,577</span><span class="sxs-lookup"><span data-stu-id="d73c3-167">0.577</span></span>               | <span data-ttu-id="d73c3-168">0,125</span><span class="sxs-lookup"><span data-stu-id="d73c3-168">0.125</span></span>                  |
| <span data-ttu-id="d73c3-169">Beschleunigung (in %)</span><span class="sxs-lookup"><span data-stu-id="d73c3-169">Speed-up (%)</span></span> | <span data-ttu-id="d73c3-170">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="d73c3-170">N/A</span></span>                    | <span data-ttu-id="d73c3-171">–122,8 %</span><span class="sxs-lookup"><span data-stu-id="d73c3-171">-122.8%</span></span>             | <span data-ttu-id="d73c3-172">78,3 % (51,7 % im Vergleich zu WPS)</span><span class="sxs-lookup"><span data-stu-id="d73c3-172">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a><span data-ttu-id="d73c3-173">Überprüfen von `system32` nach kompatiblen Modulen unter Windows</span><span class="sxs-lookup"><span data-stu-id="d73c3-173">Check `system32` for compatible in-box modules on Windows</span></span>

<span data-ttu-id="d73c3-174">Im Update 1809 für Windows Update 10 und im Update für Windows Server 2019 wurden eine Reihe von integrierten PowerShell-Modulen aktualisiert, um sie als mit PowerShell Core kompatibel zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="d73c3-174">In the Windows 10 1809 update and Windows Server 2019, we updated a number of in-box PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="d73c3-175">Beim Starten von PowerShell Core 6.1 wird automatisch `$windir\System32` als Teil der `PSModulePath`-Umgebungsvariable mit einbezogen.</span><span class="sxs-lookup"><span data-stu-id="d73c3-175">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span>
<span data-ttu-id="d73c3-176">Allerdings werden Module nur dann `Get-Module` und `Import-Module` verfügbar gemacht, wenn `CompatiblePSEdition` als kompatibel mit `Core` gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="d73c3-176">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="d73c3-177">Je nach den installierten Rollen und Funktionen werden Ihnen möglicherweise unterschiedliche verfügbare Module angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-177">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="d73c3-178">Mit dem Switch-Parameter `-SkipEditionCheck` können Sie dieses Verhalten so überschreiben, dass alle Module angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-178">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="d73c3-179">Außerdem wurde der Tabellenausgabe eine `PSEdition`-Eigenschaft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-179">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="d73c3-180">Weitere Informationen zu diesem Verhalten finden Sie unter [PowerShell RFC 0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span><span class="sxs-lookup"><span data-stu-id="d73c3-180">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="d73c3-181">Markdown-Cmdlets und -Rendering</span><span class="sxs-lookup"><span data-stu-id="d73c3-181">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="d73c3-182">Markdown ist eine Standardsprache zum Erstellen von lesbaren Nur-Text-Dokumenten mit grundlegender Formatierung, die in HTML gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="d73c3-182">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="d73c3-183">PowerShell Core 6.1 wurden einige Cmdlets hinzugefügt, mit denen Sie Markdowndokumente in der Konsole konvertieren und rendern können, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="d73c3-183">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="d73c3-184">Mit `Show-Markdown` wird beispielsweise eine Markdowndatei in der Konsole gerendert:</span><span class="sxs-lookup"><span data-stu-id="d73c3-184">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Beispiel „Show-Markdown“](./images/markdown_example.png)

<span data-ttu-id="d73c3-186">Weitere Informationen zur Funktionsweise dieser Cmdlets finden Sie unter [dieser RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span><span class="sxs-lookup"><span data-stu-id="d73c3-186">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="d73c3-187">Experimentelle Featureflags</span><span class="sxs-lookup"><span data-stu-id="d73c3-187">Experimental feature flags</span></span>

<span data-ttu-id="d73c3-188">Unterstützung für [experimentelle Features][] wurde aktiviert.</span><span class="sxs-lookup"><span data-stu-id="d73c3-188">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="d73c3-189">Auf diese Weise können PowerShell-Entwickler neue Funktionen bereitstellen und Feedback erhalten, bevor der Entwurf abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="d73c3-189">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="d73c3-190">Auf diese Weise vermeiden wir, dass wir bei der Weiterentwicklung des Entwurfs Breaking Changes vornehmen.</span><span class="sxs-lookup"><span data-stu-id="d73c3-190">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="d73c3-191">Verwenden Sie `Get-ExperimentalFeature`, um eine Liste der verfügbaren experimentellen Features abzurufen.</span><span class="sxs-lookup"><span data-stu-id="d73c3-191">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="d73c3-192">Sie können diese Features mit `Enable-ExperimentalFeature` und `Disable-ExperimentalFeature` aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="d73c3-192">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="d73c3-193">Weitere Informationen zu dieser Funktion finden Sie unter [PowerShell RFC 0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span><span class="sxs-lookup"><span data-stu-id="d73c3-193">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="d73c3-194">Verbesserungen an Web-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="d73c3-194">Web cmdlet improvements</span></span>

<span data-ttu-id="d73c3-195">Durch die Mithilfe von [@markekraus](https://github.com/markekraus) konnte eine ganze Reihe von Verbesserungen an den Web-Cmdlets [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="d73c3-195">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="d73c3-196">und [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod) vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-196">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="d73c3-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109): Standardcodierung für `application-json`-Antworten auf UTF-8 festgelegt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-197">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="d73c3-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation`-Parameter zum Zulassen von `Content-Type`-Headern, die nicht mit den Standards kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="d73c3-198">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="d73c3-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form`-Parameter zur Unterstützung von vereinfachter `multipart/form-data`-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="d73c3-199">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="d73c3-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338): Kompatible Verarbeitung von Beziehungsschlüsseln ohne Beachtung der Groß-/Kleinschreibung.</span><span class="sxs-lookup"><span data-stu-id="d73c3-200">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="d73c3-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447): Hinzufügen des `-Resume`-Parameters zu Web-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d73c3-201">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="d73c3-202">Remoting-Verbesserungen</span><span class="sxs-lookup"><span data-stu-id="d73c3-202">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="d73c3-203">PowerShell Direct für Container verwendet zunächst PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d73c3-203">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="d73c3-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) ist eine Funktion von PowerShell und Hyper-V, mit der Sie ohne Netzwerkverbindung oder einem anderen Remoteverwaltungsdienst eine Verbindung zu einem virtuellen Hyper-V-Computer oder Container herstellen können.</span><span class="sxs-lookup"><span data-stu-id="d73c3-204">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="d73c3-205">Bisher wurde die Verbindung von PowerShell Direct mithilfe der integrierten Windows PowerShell-Instanz auf dem Container hergestellt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-205">In the past, PowerShell Direct connected using the inbox Windows PowerShell instance on the Container.</span></span>
<span data-ttu-id="d73c3-206">Nun versucht PowerShell Direct zunächst, verfügbare `pwsh.exe`-Dateien der `PATH`-Umgebungsvariable dafür zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-206">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span>
<span data-ttu-id="d73c3-207">Ist `pwsh.exe` nicht verfügbar, greift PowerShell Direct wieder auf `powershell.exe` zurück.</span><span class="sxs-lookup"><span data-stu-id="d73c3-207">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="d73c3-208">`Enable-PSRemoting` erstellt jetzt separate Remotingendpunkte für Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="d73c3-208">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="d73c3-209">`Enable-PSRemoting` erstellt jetzt zwei Konfigurationen für Remotesitzungen:</span><span class="sxs-lookup"><span data-stu-id="d73c3-209">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="d73c3-210">Eine für die Hauptversion von PowerShell,</span><span class="sxs-lookup"><span data-stu-id="d73c3-210">One for the major version of PowerShell.</span></span> <span data-ttu-id="d73c3-211">Beispiel: `PowerShell.6`.</span><span class="sxs-lookup"><span data-stu-id="d73c3-211">For example, `PowerShell.6`.</span></span> <span data-ttu-id="d73c3-212">Auf diesen Endpunkt kann nach geringfügigen Aktualisierungen als systemweite Sitzungskonfiguration von PowerShell 6 zurückgegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-212">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="d73c3-213">Eine versionsspezifische Sitzungskonfiguration, z.B. `PowerShell.6.1.0`.</span><span class="sxs-lookup"><span data-stu-id="d73c3-213">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="d73c3-214">Dieses Verhalten ist hilfreich, wenn Sie mehrere Versionen von PowerShell 6 auf einem Computer installiert und zugänglich haben möchten.</span><span class="sxs-lookup"><span data-stu-id="d73c3-214">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="d73c3-215">Darüber hinaus verfügen Vorschauversionen von PowerShell nun über eigene Remotesitzungskonfigurationen, wenn Sie das `Enable-PSRemoting`-Cmdlet ausgeführt haben:</span><span class="sxs-lookup"><span data-stu-id="d73c3-215">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="d73c3-216">Die Ausgabe sieht möglicherweise anders aus, wenn Sie nicht zuvor WinRM eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="d73c3-216">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="d73c3-217">In diesem Fall werden möglicherweise separate PowerShell-Sitzungskonfigurationen für die Vorschau und stabile Builds von PowerShell 6 sowie für jede einzelne Version angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-217">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="d73c3-218">Für SSH unterstützte `user@host:port`-Syntax</span><span class="sxs-lookup"><span data-stu-id="d73c3-218">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="d73c3-219">SSH-Clients unterstützen in der Regel eine Verbindungszeichenfolge im Format `user@host:port`.</span><span class="sxs-lookup"><span data-stu-id="d73c3-219">SSH clients typically support a connection string in the format `user@host:port`.</span></span>
<span data-ttu-id="d73c3-220">Durch das Hinzufügen von SSH als Protokoll für PowerShell-Remoting ist nun Unterstützung für dieses Format der Verbindungszeichenfolge enthalten:</span><span class="sxs-lookup"><span data-stu-id="d73c3-220">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="d73c3-221">MSI-Option zum Hinzufügen eines Explorer-Shell-Kontextmenüs unter Windows</span><span class="sxs-lookup"><span data-stu-id="d73c3-221">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="d73c3-222">Durch die Mithilfe von [@bergmeister](https://github.com/bergmeister) ist es nun möglich, ein Kontextmenü unter Windows zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d73c3-222">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="d73c3-223">Sie können Ihre systemweite Installation von PowerShell 6.1 jetzt aus einem beliebigen Ordner im Windows-Explorer öffnen:</span><span class="sxs-lookup"><span data-stu-id="d73c3-223">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![Shell-Kontextmenü für PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="d73c3-225">Nützliche Funktionen</span><span class="sxs-lookup"><span data-stu-id="d73c3-225">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="d73c3-226">„Als Administrator ausführen“ in der Sprungliste der Windows-Verknüpfungen</span><span class="sxs-lookup"><span data-stu-id="d73c3-226">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="d73c3-227">Durch die Mithilfe von [@bergmeister](https://github.com/bergmeister) enthält die Sprungliste der Verknüpfungen von PowerShell Core jetzt die Option „Als Administrator ausführen“:</span><span class="sxs-lookup"><span data-stu-id="d73c3-227">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![„Als Administrator ausführen“ in der Sprungliste von PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="d73c3-229">Zurück zum vorherigen Verzeichnis mit `cd -`</span><span class="sxs-lookup"><span data-stu-id="d73c3-229">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="d73c3-230">Oder unter Linux:</span><span class="sxs-lookup"><span data-stu-id="d73c3-230">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="d73c3-231">`cd` und `cd --` wechseln auch zu `$HOME`.</span><span class="sxs-lookup"><span data-stu-id="d73c3-231">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="d73c3-232">Durch die Mithilfe von [@iSazonov](https://github.com/iSazonov) konnte das [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection)-Cmdlet auf PowerShell Core portiert werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-232">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="d73c3-233">`Update-Help` als Nicht-Administrator</span><span class="sxs-lookup"><span data-stu-id="d73c3-233">`Update-Help` as non-admin</span></span>

<span data-ttu-id="d73c3-234">Aufgrund der großen Nachfrage muss nun `Update-Help` nicht mehr als Administrator ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-234">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span>
<span data-ttu-id="d73c3-235">Über `Update-Help` wird die Hilfe jetzt standardmäßig in einen benutzerdefinierten Ordner gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d73c3-235">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="d73c3-236">Neue Methoden/Eigenschaften für `PSCustomObject`</span><span class="sxs-lookup"><span data-stu-id="d73c3-236">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="d73c3-237">Durch die Mithilfe von [@iSazonov](https://github.com/iSazonov) konnten `PSCustomObject` neue Methoden und Eigenschaften hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-237">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span>
<span data-ttu-id="d73c3-238">`PSCustomObject` enthält nun eine `Count`/`Length`-Eigenschaften wie andere Objekte.</span><span class="sxs-lookup"><span data-stu-id="d73c3-238">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="d73c3-239">Diese Vorgehensweise umfasst auch `ForEach`- und `Where`-Methoden, mit denen Sie nach `PSCustomObject`-Elementen ausführen und filtern können:</span><span class="sxs-lookup"><span data-stu-id="d73c3-239">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="d73c3-240">Durch die Mithilfe von @SimonWahlin konnte `Where-Object` der `-Not`-Parameter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-240">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span>
<span data-ttu-id="d73c3-241">Jetzt können Sie ein Objekt in der Pipeline nach dem Nichtvorhandensein einer Eigenschaft oder eines leeren oder NULL-Eigenschaftswerts filtern.</span><span class="sxs-lookup"><span data-stu-id="d73c3-241">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="d73c3-242">Dieser Befehl gibt z.B. alle Dienste zurück, die über keine definierten abhängigen Dienste verfügen:</span><span class="sxs-lookup"><span data-stu-id="d73c3-242">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="d73c3-243">Erstellen eines BOM-freien UTF-8-Dokuments mit `New-ModuleManifest`</span><span class="sxs-lookup"><span data-stu-id="d73c3-243">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="d73c3-244">Durch den Umstieg auf BOM-freies UTF-8 in PowerShell 6.0 wurde das `New-ModuleManifest`-Cmdlet aktualisiert, und es erstellt nun BOM-freie UTF-8-Dokumente anstatt UTF-16-Dokumente.</span><span class="sxs-lookup"><span data-stu-id="d73c3-244">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="d73c3-245">Konvertierungen von PSMethod in einen Delegaten</span><span class="sxs-lookup"><span data-stu-id="d73c3-245">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="d73c3-246">Durch die Mithilfe von [@powercode](https://github.com/powercode) wird jetzt die Konvertierung von `PSMethod` in einen Delegaten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-246">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span>
<span data-ttu-id="d73c3-247">Dadurch kann nun beispielsweise `PSMethod` `[M]::DoubleStrLen` als Delegatwert an `[M]::AggregateString` übergeben werden:</span><span class="sxs-lookup"><span data-stu-id="d73c3-247">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="d73c3-248">Weitere Informationen zu dieser Änderung finden Sie unter [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span><span class="sxs-lookup"><span data-stu-id="d73c3-248">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="d73c3-249">Standardabweichung in `Measure-Object`</span><span class="sxs-lookup"><span data-stu-id="d73c3-249">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="d73c3-250">Durch die Mithilfe von [@CloudyDino](https://github.com/CloudyDino) wurde `Measure-Object` eine `StandardDeviation`-Eigenschaft hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="d73c3-250">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="d73c3-251">Durch die Mithilfe von [@maybe-hello-world](https://github.com/maybe-hello-world) verfügt `Get-PfxCertificate` jetzt über den `Password`-Parameter, der eine `SecureString` erfordert.</span><span class="sxs-lookup"><span data-stu-id="d73c3-251">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="d73c3-252">Dadurch kann er ohne Benutzereingriff verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="d73c3-252">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="d73c3-253">Entfernen der `more`-Funktion</span><span class="sxs-lookup"><span data-stu-id="d73c3-253">Removal of the `more` function</span></span>

<span data-ttu-id="d73c3-254">Bisher enthielt PowerShell unter Windows eine Funktion mit dem Namen `more`, die `more.com` mit einschloss.</span><span class="sxs-lookup"><span data-stu-id="d73c3-254">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span>
<span data-ttu-id="d73c3-255">Diese Funktion wurde nun entfernt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-255">That function has now been removed.</span></span>

<span data-ttu-id="d73c3-256">Zudem wurde die `help`-Funktion so geändert, dass unter Windows `more.com` verwendet wird bzw. auf anderen Plattformen der unter `$env:PAGER` angegebene Standardpager des Systems.</span><span class="sxs-lookup"><span data-stu-id="d73c3-256">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="d73c3-257">Zurückleiten der Benutzer zum aktuellen Arbeitsverzeichnis im Laufwerk mit `cd DriveName:`</span><span class="sxs-lookup"><span data-stu-id="d73c3-257">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="d73c3-258">Bisher wurden Benutzer zum Standardspeicherort für das Laufwerk geleitet, wenn sie mit `Set-Location` oder `cd` zu einem PowerShell-Laufwerk (PSDrive) zurückkehren wollten.</span><span class="sxs-lookup"><span data-stu-id="d73c3-258">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="d73c3-259">Durch die Mithilfe von [@mcbobke](https://github.com/mcbobke) werden Benutzer jetzt zum letzten bekannten aktuellen Arbeitsverzeichnis für die jeweilige Sitzung geleitet.</span><span class="sxs-lookup"><span data-stu-id="d73c3-259">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="d73c3-260">Typbezeichner für Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d73c3-260">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="d73c3-261">Windows PowerShell enthält nun die folgenden Typbezeichner für ein einfacheres Arbeiten mit den jeweiligen Typen:</span><span class="sxs-lookup"><span data-stu-id="d73c3-261">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="d73c3-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="d73c3-262">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="d73c3-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="d73c3-263">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="d73c3-264">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="d73c3-264">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="d73c3-265">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="d73c3-265">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="d73c3-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="d73c3-266">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="d73c3-267">In PowerShell 6 waren diese Typbezeichner noch nicht enthalten und wurden nun in PowerShell 6.1 unter Windows hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-267">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="d73c3-268">Mit diesen Typen können auf einfache Weise AD- und WMI-Objekte erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-268">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="d73c3-269">Sie können beispielsweise mithilfe von LDAP eine Abfrage ausführen:</span><span class="sxs-lookup"><span data-stu-id="d73c3-269">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="d73c3-270">Im folgenden Beispiel wird ein CIM-Objekt „Win32_OperatingSystem“ erstellt:</span><span class="sxs-lookup"><span data-stu-id="d73c3-270">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="d73c3-271">In diesem Beispiel wird ein ManagementClass-Objekt für die Klasse „Win32_OperatingSystem“ zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="d73c3-271">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="d73c3-272">`-lp`-Alias für alle `-LiteralPath`-Parameter</span><span class="sxs-lookup"><span data-stu-id="d73c3-272">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="d73c3-273">Durch die Mithilfe von [@kvprasoon](https://github.com/kvprasoon) gibt es nun einen Parameteralias `-lp` für alle integrierten PowerShell-Cmdlets mit einem `-LiteralPath`-Parameter.</span><span class="sxs-lookup"><span data-stu-id="d73c3-273">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="d73c3-274">Wichtige Änderungen</span><span class="sxs-lookup"><span data-stu-id="d73c3-274">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="d73c3-275">MSI-basierte Installationspfade unter Windows</span><span class="sxs-lookup"><span data-stu-id="d73c3-275">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="d73c3-276">Unter Windows wird das MSI-Paket nun im folgenden Pfad installiert:</span><span class="sxs-lookup"><span data-stu-id="d73c3-276">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="d73c3-277">`$env:ProgramFiles\PowerShell\6\` für die stabile Installation von 6.x</span><span class="sxs-lookup"><span data-stu-id="d73c3-277">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="d73c3-278">`$env:ProgramFiles\PowerShell\6-preview\` für die Installation der Vorschau von 6.x</span><span class="sxs-lookup"><span data-stu-id="d73c3-278">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="d73c3-279">Mit dieser Änderung wird sichergestellt, dass PowerShell Core durch Microsoft Update aktualisiert/gewartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d73c3-279">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="d73c3-280">Weitere Informationen finden Sie unter [PowerShell RFC 0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span><span class="sxs-lookup"><span data-stu-id="d73c3-280">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="d73c3-281">Deaktivieren von Telemetrie nur mit einer Umgebungsvariable</span><span class="sxs-lookup"><span data-stu-id="d73c3-281">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="d73c3-282">PowerShell Core sendet beim Starten grundlegende Telemetriedaten an Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d73c3-282">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="d73c3-283">Diese enthalten den Namen und die Version des Betriebssystems sowie die Version von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d73c3-283">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="d73c3-284">Dadurch wird erkennbar, in welchen Umgebungen PowerShell verwendet wird und welche neuen Funktionen und Problembehebungen Vorrang haben sollten.</span><span class="sxs-lookup"><span data-stu-id="d73c3-284">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="d73c3-285">Wenn Sie diese Telemetriedaten nicht senden möchten, legen Sie die Umgebungsvariable `POWERSHELL_TELEMETRY_OPTOUT` auf `true`, `yes` oder `1` fest.</span><span class="sxs-lookup"><span data-stu-id="d73c3-285">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="d73c3-286">Die Datei `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` wird zum Deaktivieren der Telemetrie nicht mehr unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-286">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="d73c3-287">Standardauthentifizierung über HTTP in PowerShell-Remoting auf Unix-Plattformen nicht zulässig</span><span class="sxs-lookup"><span data-stu-id="d73c3-287">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="d73c3-288">PowerShell-Remoting auf Unix-Plattformen erfordert nun die Verwendung von NTLM/Negotiate oder HTTPS, um unverschlüsselten Datenverkehr zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="d73c3-288">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="d73c3-289">Weitere Informationen zu diesen Änderungen finden Sie unter [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span><span class="sxs-lookup"><span data-stu-id="d73c3-289">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="d73c3-290">`VisualBasic` als unterstützte Sprache in Add-Type entfernt</span><span class="sxs-lookup"><span data-stu-id="d73c3-290">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="d73c3-291">Bisher konnte Visual Basic-Code mit dem `Add-Type`-Cmdlet kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="d73c3-291">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span>
<span data-ttu-id="d73c3-292">Visual Basic wurde jedoch nur selten mit `Add-Type` verwendet.</span><span class="sxs-lookup"><span data-stu-id="d73c3-292">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="d73c3-293">Daher wurde diese Funktion nun entfernt, um die Größe von PowerShell zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="d73c3-293">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="d73c3-294">Verwendung von `CommandTypes.Workflow` und `WorkflowInfoCleaned` bereinigt</span><span class="sxs-lookup"><span data-stu-id="d73c3-294">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="d73c3-295">Weitere Informationen zu diesen Änderungen finden Sie unter [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span><span class="sxs-lookup"><span data-stu-id="d73c3-295">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="d73c3-296">Group-Object sortiert jetzt die Gruppen</span><span class="sxs-lookup"><span data-stu-id="d73c3-296">Group-Object now sorts the groups</span></span>

<span data-ttu-id="d73c3-297">Im Rahmen der Leistungsverbesserung gibt `Group-Object` jetzt eine sortierte Auflistung der Gruppen zurück.</span><span class="sxs-lookup"><span data-stu-id="d73c3-297">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="d73c3-298">Obwohl Sie sich auf die Reihenfolge nicht verlassen sollten, könnte diese Änderung zu einer Teilung führen, wenn Sie die erste Gruppe anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="d73c3-298">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="d73c3-299">Wir haben entschieden, dass diese Leistungsverbesserung die Änderung wert wäre, weil sich die Abhängigkeit vom früheren Verhalten nur geringfügig auswirkt.</span><span class="sxs-lookup"><span data-stu-id="d73c3-299">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="d73c3-300">Weitere Informationen zu dieser Änderung finden Sie unter [Problem #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span><span class="sxs-lookup"><span data-stu-id="d73c3-300">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[Experimentelle Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
