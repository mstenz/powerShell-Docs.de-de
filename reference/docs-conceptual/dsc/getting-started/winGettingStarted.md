---
ms.date: 08/15/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Erste Schritte mit Desired State Configuration (DSC) für Windows
ms.openlocfilehash: 2add2c936e60c0c9446bf4b398fbf7b4bd6407f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75416164"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="fb43e-103">Erste Schritte mit Desired State Configuration (DSC) für Windows</span><span class="sxs-lookup"><span data-stu-id="fb43e-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="fb43e-104">In diesem Thema werden die ersten Schritte mit PowerShell Desired State Configuration (DSC) für Windows erläutert.</span><span class="sxs-lookup"><span data-stu-id="fb43e-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="fb43e-105">Allgemeine Informationen zu DSC finden Sie unter [Erste Schritte mit Windows PowerShell DSC](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="fb43e-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="fb43e-106">Unterstützte Windows-Betriebssystemversionen</span><span class="sxs-lookup"><span data-stu-id="fb43e-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="fb43e-107">Die folgenden Versionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="fb43e-107">The following versions are supported:</span></span>

- <span data-ttu-id="fb43e-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="fb43e-108">Windows Server 2019</span></span>
- <span data-ttu-id="fb43e-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fb43e-109">Windows Server 2016</span></span>
- <span data-ttu-id="fb43e-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="fb43e-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="fb43e-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="fb43e-111">Windows Server 2012</span></span>
- <span data-ttu-id="fb43e-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="fb43e-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="fb43e-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="fb43e-113">Windows 10</span></span>
- <span data-ttu-id="fb43e-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fb43e-114">Windows 8.1</span></span>
- <span data-ttu-id="fb43e-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="fb43e-115">Windows 7</span></span>

<span data-ttu-id="fb43e-116">Die eigenständige Produkt-SKU [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) umfasst keine Desired State Configuration-Implementierung und kann deshalb nicht mit PowerShell DSC oder Azure Automation State Configuration verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="fb43e-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku doesn't contain an implementation of Desired State Configuration so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="fb43e-117">Installieren von DSC</span><span class="sxs-lookup"><span data-stu-id="fb43e-117">Installing DSC</span></span>

<span data-ttu-id="fb43e-118">PowerShell Desired State Configuration ist in Windows enthalten und wird über Windows Management Framework aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="fb43e-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span> <span data-ttu-id="fb43e-119">Die aktuelle Version ist [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="fb43e-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="fb43e-120">Es ist nicht erforderlich, das Windows Server-Feature „DSC-Service“ zu aktivieren, um einen Computer mithilfe von DSC zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="fb43e-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="fb43e-121">Dieses Feature wird nur benötigt, wenn Sie eine Windows Pull Server-Instanz erstellen.</span><span class="sxs-lookup"><span data-stu-id="fb43e-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="fb43e-122">Verwenden von DSC für Windows</span><span class="sxs-lookup"><span data-stu-id="fb43e-122">Using DSC for Windows</span></span>

<span data-ttu-id="fb43e-123">In den folgenden Abschnitten wird erläutert, wie DSC-Konfigurationen erstellt und auf Windows-Computern ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fb43e-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="fb43e-124">Erstellen eines MOF-Konfigurationsdokuments</span><span class="sxs-lookup"><span data-stu-id="fb43e-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="fb43e-125">Um eine Konfiguration zu erstellen, wird das Windows PowerShell-Schlüsselwort `Configuration` verwendet.</span><span class="sxs-lookup"><span data-stu-id="fb43e-125">The Windows PowerShell `Configuration` keyword is used to create a configuration.</span></span>
<span data-ttu-id="fb43e-126">Die folgenden Schritte beschreiben die Erstellung eines Konfigurationsdokuments mithilfe von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb43e-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="fb43e-127">Definieren Sie eine Konfiguration, und generieren Sie das Konfigurationsdokument:</span><span class="sxs-lookup"><span data-stu-id="fb43e-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="fb43e-128">Installieren eines Moduls mit DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="fb43e-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="fb43e-129">Windows PowerShell Desired State Configuration umfasst integrierte Module, die DSC-Ressourcen enthalten.</span><span class="sxs-lookup"><span data-stu-id="fb43e-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="fb43e-130">Mithilfe der PowerShellGet-Cmdlets ist es außerdem möglich, Module aus externen Quellen wie z. B. dem PowerShell-Katalog zu laden.</span><span class="sxs-lookup"><span data-stu-id="fb43e-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="fb43e-131">Anwenden der Konfiguration auf den Computer</span><span class="sxs-lookup"><span data-stu-id="fb43e-131">Apply the configuration to the machine</span></span>

> [!NOTE]
> <span data-ttu-id="fb43e-132">Damit DSC ausgeführt werden kann, muss Windows für den Empfang von PowerShell-Remotebefehlen konfiguriert werden – selbst dann, wenn Sie eine `localhost`-Konfiguration ausführen.</span><span class="sxs-lookup"><span data-stu-id="fb43e-132">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="fb43e-133">Um Ihre Umgebung auf einfache Weise ordnungsgemäß zu konfigurieren, rufen Sie einfach `Set-WsManQuickConfig -Force` in einem PowerShell-Terminal mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="fb43e-133">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="fb43e-134">Konfigurationsdokumente (MOF-Dateien) können mit dem Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) auf den Computer angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="fb43e-134">Configuration documents (MOF files) can be applied to the machineusing the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="fb43e-135">Abrufen des aktuellen Status der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="fb43e-135">Get the current state of the configuration</span></span>

<span data-ttu-id="fb43e-136">Mit dem Cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) wird der aktuelle Status des Computers abgerufen, und es werden die aktuellen Werte für die Konfiguration zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="fb43e-136">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

```powershell
Get-DscConfiguration
```

<span data-ttu-id="fb43e-137">Das Cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) gibt die aktuelle Metakonfiguration zurück, die auf den Computer angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="fb43e-137">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="fb43e-138">Entfernen der aktuellen Konfiguration von einem Computer</span><span class="sxs-lookup"><span data-stu-id="fb43e-138">Remove the current configuration from a machine</span></span>

<span data-ttu-id="fb43e-139">Cmdlet [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument):</span><span class="sxs-lookup"><span data-stu-id="fb43e-139">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="fb43e-140">Konfigurieren der Einstellungen im lokalen Konfigurations-Manager</span><span class="sxs-lookup"><span data-stu-id="fb43e-140">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="fb43e-141">Wenden Sie mit dem Cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) eine MOF-Metakonfigurationsdatei auf den Computer an.</span><span class="sxs-lookup"><span data-stu-id="fb43e-141">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="fb43e-142">Erfordert die Angabe des Pfads zur MOF-Metakonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="fb43e-142">Requires the path to the Meta Configuration MOF.</span></span>

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="fb43e-143">Windows PowerShell DSC-Protokolldateien</span><span class="sxs-lookup"><span data-stu-id="fb43e-143">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="fb43e-144">Protokolle für Desired State Configuration werden in das Windows-Ereignisprotokoll im Pfad `Microsoft-Windows-Dsc/Operational` geschrieben.</span><span class="sxs-lookup"><span data-stu-id="fb43e-144">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="fb43e-145">Zusätzliche Protokolle zu Debuggingzwecken können mithilfe der unter [Wo befinden sich die DSC-Ereignisprotokolle?](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs) genannten Schritte aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="fb43e-145">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
