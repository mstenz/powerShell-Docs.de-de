---
ms.date: 12/12/2018
keywords: DSC, Powershell, Resource, Katalog, setup
title: Installieren zusätzlicher DSC-Ressourcen
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401694"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="bfd0e-103">Installieren zusätzlicher DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bfd0e-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="bfd0e-104">PowerShell umfasst mehrere Out-of-the-Box-Ressourcen für Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="bfd0e-105">Die **"psdesiredstateconfiguration"** -Modul enthält alle OOB-DSC-Ressourcen für Ihre spezifischen Instanz von PowerShell verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="bfd0e-106">Dies ist eine Liste mit den OOB-Ressourcen, die in PowerShell 4.0 und eine Beschreibung der Funktionen von der Ressource enthalten.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="bfd0e-107">Dies ist eine unvollständige Liste, wie die Anzahl der OOB-Ressourcen mit jeder Version von PowerShell geworden ist.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="bfd0e-108">Ressource</span><span class="sxs-lookup"><span data-stu-id="bfd0e-108">Resource</span></span>  |<span data-ttu-id="bfd0e-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bfd0e-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="bfd0e-110">**File**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-110">**File**</span></span>|<span data-ttu-id="bfd0e-111">Steuert den Status der Dateien und Verzeichnisse.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-111">Controls the state of files and directories.</span></span> <span data-ttu-id="bfd0e-112">Kopiert Dateien aus einer **Quelle** auf eine **Ziel** und aktualisiert sie bei der **Quelle** Änderungen durch Vergleichen von Datumsangaben, Prüfsummen und Hashes.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="bfd0e-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-113">**Archive**</span></span>|<span data-ttu-id="bfd0e-114">Entpacken Archive und einer angegebenen Position.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="bfd0e-115">Überprüft die Archive mit einem angegebenen **Prüfsumme**.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="bfd0e-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-116">**Environment**</span></span>|<span data-ttu-id="bfd0e-117">Verwaltet Umgebungsvariablen.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-117">Manages environment variables.</span></span>|
|<span data-ttu-id="bfd0e-118">**Gruppe**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-118">**Group**</span></span>|<span data-ttu-id="bfd0e-119">Lokale Gruppen verwaltet und steuert die Gruppenmitgliedschaft.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="bfd0e-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-120">**Log**</span></span>|<span data-ttu-id="bfd0e-121">Schreibt Meldungen an die `Microsoft-Windows-Desired State Configuration/Analytic` Ereignisprotokoll.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="bfd0e-122">**Paket**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-122">**Package**</span></span>|<span data-ttu-id="bfd0e-123">Installiert oder deinstalliert Pakete mit **Argumente**, **LogPath**, **ReturnCode**, andere Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="bfd0e-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-124">**Registry**</span></span>|<span data-ttu-id="bfd0e-125">Verwaltet Registrierungsschlüssel und-Werte an.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="bfd0e-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-126">**Script**</span></span>|<span data-ttu-id="bfd0e-127">Können Sie entwerfen Ihre eigenen [Get-Test-Set](../resources/get-test-set.md) Skriptblöcken.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="bfd0e-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-128">**Service**</span></span>|<span data-ttu-id="bfd0e-129">Windows Services konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-129">Configures Windows services.</span></span>|
|<span data-ttu-id="bfd0e-130">**User**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-130">**User**</span></span> |<span data-ttu-id="bfd0e-131">Verwaltet die lokale Benutzer und -Attribute.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="bfd0e-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-132">**WindowsFeature**</span></span>|<span data-ttu-id="bfd0e-133">Verwaltet die Rollen und Features.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-133">Manages roles and features.</span></span>|
|<span data-ttu-id="bfd0e-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="bfd0e-134">**WindowsProcess**</span></span>|<span data-ttu-id="bfd0e-135">Konfiguriert die Windows-Prozesse.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-135">Configures Windows processes.</span></span>|

<span data-ttu-id="bfd0e-136">Die OOB-Ressourcen können einen guten Ausgangspunkt für allgemeine Vorgänge.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="bfd0e-137">Wenn die OOB-Ressourcen Ihre Anforderungen nicht erfüllen, können Sie schreiben Ihre eigenen [benutzerdefinierte Ressource](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="bfd0e-138">Bevor Sie eine benutzerdefinierte Ressource zur Behebung Ihres Problems schreiben, sollten Sie über die große Anzahl von DSC-Ressourcen ansehen, die bereits von Microsoft und der PowerShell-Community erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="bfd0e-139">DSC-Ressourcen finden Sie in beiden die [PowerShell-Katalog](https://www.powershellgallery.com/) und [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="bfd0e-140">Sie können DSC-Ressourcen auch direkt über die PowerShell-Konsole mit installieren [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="bfd0e-141">Installieren von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bfd0e-141">Installing PowerShellGet</span></span>

<span data-ttu-id="bfd0e-142">Um festzustellen, ob Sie bereits haben **PowerShell** erhalten, oder um Hilfe bei der Installation erhalten zu können, finden Sie unter der folgenden Anleitung: [Installieren von PowerShellGet](/powershell/gallery/installing-psget)</span><span class="sxs-lookup"><span data-stu-id="bfd0e-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="bfd0e-143">Suchen von DSC-Ressourcen, die die Verwendung von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bfd0e-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="bfd0e-144">Einmal **PowerShellGet** wird installiert auf Ihrem System können Sie ermitteln und installieren Sie die im gehosteten DSC-Ressourcen die [PowerShell-Katalog](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="bfd0e-145">Verwenden Sie zunächst die [Find-DSCResource](/powershell/module/powershellget/find-dscresource) Cmdlet, um DSC-Ressourcen zu finden.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="bfd0e-146">Beim Ausführen von `Find-DSCResource` erstmals ausführen, finden Sie die folgende Aufforderung zum Installieren des Anbieters"NuGet".</span><span class="sxs-lookup"><span data-stu-id="bfd0e-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="bfd0e-147">Klicken Sie nach dem Drücken 'y' der "NuGet"-Anbieter installiert ist, finden Sie eine Liste von DSC-Ressourcen, die Sie aus dem PowerShell-Katalog installieren können.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="bfd0e-148">Liste wird nicht angezeigt werden, da sie sehr groß ist.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="bfd0e-149">Sie können auch angeben, die `-Name` mithilfe von Platzhaltern, Parameter oder `-Filter` Parameter ohne Platzhalter, um Ihre Suche einzugrenzen.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="bfd0e-150">In diesem Beispiel wird versucht, eine "Zeitzone" DSC-Ressource, die mit der die Platzhalter zu finden.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bfd0e-151">Derzeit ist es jedoch ein Fehler in der `Find-DSCResource` -Cmdlet, das mithilfe von Platzhaltern in beiden verhindert, dass die `-Name` und `-Filter` Parameter.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="bfd0e-152">Das zweite Beispiel unten zeigt eine problemumgehung mithilfe `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="bfd0e-153">Sie können auch `Where-Object` zu DSC-Ressourcen über eine feiner abgestimmte Filtern zu suchen.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="bfd0e-154">Dieser Ansatz wird als unter Verwendung der integrierten Filterparameter langsamer sein.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="bfd0e-155">Weitere Informationen zur Filterung finden Sie unter [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="bfd0e-156">Installieren von DSC-Ressourcen, die die Verwendung von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bfd0e-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="bfd0e-157">Verwenden Sie zum Installieren einer DSC-Ressource die [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet angeben des Namens des Moduls angezeigt, die unter **Modul** Name in den Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="bfd0e-158">Die Ressource "Zeitzone" ist also, d. h. das Modul in diesem Beispiel wird installiert im Modul "ComputerManagementDSC" vorhanden.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="bfd0e-159">Wenn Sie nicht im PowerShell-Katalog vertrauenswürdige haben, Sie sehen, dass die Warnung unter der Aufforderung zur Bestätigung, und installiert, Sie anweisen, wie in nachfolgender eingabeaufforderungen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="bfd0e-160">Drücken Sie "y", um den Vorgang fortzusetzen, installieren das Modul aus.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="bfd0e-161">Nach der Installation können Sie überprüfen, ob mithilfe die neue Ressource installiert [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="bfd0e-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="bfd0e-162">Sie können auch andere Ressourcen in Ihrem neu installierte Modul anzeigen, durch Angabe der `-ModuleName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="bfd0e-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="bfd0e-163">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bfd0e-163">See also</span></span>

- [<span data-ttu-id="bfd0e-164">Was sind Ressourcen?</span><span class="sxs-lookup"><span data-stu-id="bfd0e-164">What are Resources?</span></span>](../resources/resources.md)
