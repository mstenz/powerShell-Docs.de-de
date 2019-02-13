---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: Einen Knoten neu starten
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678354"
---
# <a name="reboot-a-node"></a><span data-ttu-id="208ba-103">Einen Knoten neu starten</span><span class="sxs-lookup"><span data-stu-id="208ba-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="208ba-104">In diesem Thema erläutert, wie einen Knoten neu starten.</span><span class="sxs-lookup"><span data-stu-id="208ba-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="208ba-105">In der Reihenfolge für den Neustart erfolgen die **ActionAfterReboot** und **RebootNodeIfNeeded** LCM-Einstellungen müssen ordnungsgemäß konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="208ba-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="208ba-106">Informationen zu den Einstellungen des lokalen Konfigurations-Managers finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md), oder [Konfigurieren des lokalen Konfigurations-Managers (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="208ba-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="208ba-107">Knoten können neu gestartet werden, von innerhalb einer Ressource, mit der `$global:DSCMachineStatus` Flag.</span><span class="sxs-lookup"><span data-stu-id="208ba-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="208ba-108">Wenn dieses Flag auf `1` in die `Set-TargetResource` Funktion erzwingt, dass den LCM den Knoten direkt nach dem Neustart der **festgelegt** Methode die aktuelle Ressource.</span><span class="sxs-lookup"><span data-stu-id="208ba-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="208ba-109">Verwenden dieses Flag die **xPendingReboot** Ressource wird erkannt, ob ein Neustart aussteht außerhalb von DSC.</span><span class="sxs-lookup"><span data-stu-id="208ba-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="208ba-110">Ihre [Konfigurationen](configurations.md) möglicherweise Schritte ausgeführt, die den Knoten neu starten zu müssen.</span><span class="sxs-lookup"><span data-stu-id="208ba-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="208ba-111">Dies kann z. B. Aspekte umfassen:</span><span class="sxs-lookup"><span data-stu-id="208ba-111">This could include things such as:</span></span>

- <span data-ttu-id="208ba-112">Windows-Updates</span><span class="sxs-lookup"><span data-stu-id="208ba-112">Windows updates</span></span>
- <span data-ttu-id="208ba-113">Softwareinstallation</span><span class="sxs-lookup"><span data-stu-id="208ba-113">Software install</span></span>
- <span data-ttu-id="208ba-114">Datei wird umbenannt.</span><span class="sxs-lookup"><span data-stu-id="208ba-114">File renames</span></span>
- <span data-ttu-id="208ba-115">Benennen Sie Computer</span><span class="sxs-lookup"><span data-stu-id="208ba-115">Computer rename</span></span>

<span data-ttu-id="208ba-116">Die **xPendingReboot** Ressource überprüft den bestimmten Computer-Standorte, um festzustellen, ob ein Neustart aussteht.</span><span class="sxs-lookup"><span data-stu-id="208ba-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="208ba-117">Wenn der Knoten einen Neustart außerhalb von DSC, erfordert die **xPendingReboot** Ressourcensätzen der `$global:DSCMachineStatus` flag `1` einen Neustart erzwungen und das ausstehende Problem zu beheben.</span><span class="sxs-lookup"><span data-stu-id="208ba-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="208ba-118">Alle DSC-Ressourcen kann anweisen, die den LCM den Knoten neu gestartet, indem Sie dieses Flag festlegen, der `Set-TargetResource` Funktion.</span><span class="sxs-lookup"><span data-stu-id="208ba-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="208ba-119">Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="208ba-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="208ba-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="208ba-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="208ba-121">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="208ba-121">Properties</span></span>

| <span data-ttu-id="208ba-122">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="208ba-122">Property</span></span> | <span data-ttu-id="208ba-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="208ba-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="208ba-124">Name</span><span class="sxs-lookup"><span data-stu-id="208ba-124">Name</span></span>| <span data-ttu-id="208ba-125">Erforderlicher Parameter, der jede Instanz der Ressource in einer Konfiguration eindeutig sein müssen.</span><span class="sxs-lookup"><span data-stu-id="208ba-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="208ba-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="208ba-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="208ba-127">Skip-Neustarts, die von der komponentenbasierten Wartung-Komponente ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="208ba-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="208ba-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="208ba-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="208ba-129">Skip-Neustarts durch Windows Update ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="208ba-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="208ba-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="208ba-130">SkipPendingFileRename</span></span> | <span data-ttu-id="208ba-131">Benennen Sie Skip ausstehende Neustarts aus.</span><span class="sxs-lookup"><span data-stu-id="208ba-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="208ba-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="208ba-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="208ba-133">Skip-Neustarts durch den ConfigMgr-Client ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="208ba-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="208ba-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="208ba-134">SkipComputerRename</span></span> | <span data-ttu-id="208ba-135">Skip wird veranschaulicht, wie die Computerrichtlinie durch Umbenennen der Computer neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="208ba-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="208ba-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="208ba-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="208ba-137">In v5 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="208ba-137">Supported in v5.</span></span> <span data-ttu-id="208ba-138">Führt die Ressource als den angegebenen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="208ba-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="208ba-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="208ba-139">DependsOn</span></span> | <span data-ttu-id="208ba-140">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="208ba-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="208ba-141">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="208ba-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="208ba-142">Weitere Informationen finden Sie unter [mithilfe von "DependsOn"](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="208ba-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="208ba-143">Beispiel</span><span class="sxs-lookup"><span data-stu-id="208ba-143">Example</span></span>

<span data-ttu-id="208ba-144">Im folgende Beispiel wird installiert, Microsoft Exchange verwenden die [xExchange](https://github.com/PowerShell/xExchange) Ressource.</span><span class="sxs-lookup"><span data-stu-id="208ba-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="208ba-145">Während der Installation der **xPendingReboot** Ressource wird verwendet, um die Knoten neu starten.</span><span class="sxs-lookup"><span data-stu-id="208ba-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="208ba-146">Dieses Beispiel erfordert die Anmeldeinformationen eines Kontos, das über Rechte zum Hinzufügen von eines Exchange-Servers in der Gesamtstruktur verfügt.</span><span class="sxs-lookup"><span data-stu-id="208ba-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="208ba-147">Weitere Informationen zur Verwendung von Anmeldeinformationen in DSC finden Sie unter [Behandeln von Anmeldeinformationen in DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="208ba-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="208ba-148">In diesem Beispiel wird davon ausgegangen, dass Sie Ihre lokalen Konfigurations-Managers zum ermöglichen von Neustarts und die Konfiguration nach einem Neustart weiterhin konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="208ba-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="208ba-149">Wo heruntergeladen</span><span class="sxs-lookup"><span data-stu-id="208ba-149">Where to Download</span></span>

<span data-ttu-id="208ba-150">Sie können die Ressourcen verwendet, die in diesem Thema an folgenden Speicherorten oder mithilfe von PowerShell-Katalog herunterladen.</span><span class="sxs-lookup"><span data-stu-id="208ba-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="208ba-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="208ba-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="208ba-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="208ba-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
