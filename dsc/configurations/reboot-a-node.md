---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,setup
title: Neustart eines Knotens
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470752"
---
# <a name="reboot-a-node"></a><span data-ttu-id="9c42c-103">Neustart eines Knotens</span><span class="sxs-lookup"><span data-stu-id="9c42c-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="9c42c-104">In diesem Thema wird erläutert, wie ein Knoten neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="9c42c-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="9c42c-105">Damit der Neustart erfolgreich verläuft, müssen die LCM-Einstellungen **ActionAfterReboot** und **RebootNodeIfNeeded** ordnungsgemäß konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="9c42c-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="9c42c-106">Weitere Informationen zu Einstellungen des lokalen Konfigurations-Managers finden Sie unter [Configure the Local Configuration Manager (Konfigurieren des lokalen Konfigurations-Managers)](../managing-nodes/metaConfig.md) oder [Configure the Local Configuration Manager (v4) (Konfigurieren des lokalen Konfigurations-Managers (Version 4))](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="9c42c-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="9c42c-107">Knoten können mithilfe des `$global:DSCMachineStatus`-Flags innerhalb einer Ressource neu gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="9c42c-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="9c42c-108">Wenn dieses Flag in der Funktion `Set-TargetResource` auf `1` festgelegt wird, wird der LCM direkt nach der **Set**-Methode der aktuellen Ressource zum Neustart des Knotens gezwungen.</span><span class="sxs-lookup"><span data-stu-id="9c42c-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="9c42c-109">Mithilfe dieses Flags erkennt die Ressource **xPendingReboot**, ob außerhalb der DSC ein Neustart aussteht.</span><span class="sxs-lookup"><span data-stu-id="9c42c-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="9c42c-110">Ihre [Konfigurationen](configurations.md) führen möglicherweise Schritte aus, die für den Neustart des Knotens erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="9c42c-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="9c42c-111">Dazu kann Folgendes gehören:</span><span class="sxs-lookup"><span data-stu-id="9c42c-111">This could include things such as:</span></span>

- <span data-ttu-id="9c42c-112">Windows-Updates</span><span class="sxs-lookup"><span data-stu-id="9c42c-112">Windows updates</span></span>
- <span data-ttu-id="9c42c-113">Softwareinstallation</span><span class="sxs-lookup"><span data-stu-id="9c42c-113">Software install</span></span>
- <span data-ttu-id="9c42c-114">Umbenennen von Dateien</span><span class="sxs-lookup"><span data-stu-id="9c42c-114">File renames</span></span>
- <span data-ttu-id="9c42c-115">Umbenennen von Computern</span><span class="sxs-lookup"><span data-stu-id="9c42c-115">Computer rename</span></span>

<span data-ttu-id="9c42c-116">Die Ressource **xPendingReboot** überprüft bestimmte Computerstandorte, um zu bestimmen, ob ein Neustart aussteht.</span><span class="sxs-lookup"><span data-stu-id="9c42c-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="9c42c-117">Wenn der Knoten einen Neustart außerhalb der DSC erfordert, legt die Ressource **xPendingReboot** das `$global:DSCMachineStatus`-Flag auf `1` fest, wodurch ein Neustart erzwungen und die ausstehende Bedingung aufgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="9c42c-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="9c42c-118">Jede DSC-Ressource kann den LCM zum Neustart des Knotens anweisen, indem dieses Flag in der Funktion `Set-TargetResource` festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="9c42c-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="9c42c-119">Weitere Informationen finden Sie unter [Writing a custom DSC resource with MOF (Schreiben einer benutzerdefinierten DSC-Ressource mit MOF)](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="9c42c-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="9c42c-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c42c-120">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="9c42c-121">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="9c42c-121">Properties</span></span>

| <span data-ttu-id="9c42c-122">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9c42c-122">Property</span></span> | <span data-ttu-id="9c42c-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9c42c-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9c42c-124">Name</span><span class="sxs-lookup"><span data-stu-id="9c42c-124">Name</span></span>| <span data-ttu-id="9c42c-125">Erforderlicher Parameter, der innerhalb einer Konfiguration pro Ressourceninstanz eindeutig sein muss.</span><span class="sxs-lookup"><span data-stu-id="9c42c-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="9c42c-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="9c42c-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="9c42c-127">Überspringen von Neustarts, die von der komponentenbasierten Wartungskomponente ausgelöst wurden.</span><span class="sxs-lookup"><span data-stu-id="9c42c-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="9c42c-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="9c42c-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="9c42c-129">Überspringen von Neustarts, die von einem Windows-Update ausgelöst wurden.</span><span class="sxs-lookup"><span data-stu-id="9c42c-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="9c42c-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="9c42c-130">SkipPendingFileRename</span></span> | <span data-ttu-id="9c42c-131">Überspringen von ausstehenden Neustarts aufgrund von Dateiumbenennungen.</span><span class="sxs-lookup"><span data-stu-id="9c42c-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="9c42c-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="9c42c-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="9c42c-133">Überspringen von Neustarts, die vom ConfigMgr-Client ausgelöst wurden.</span><span class="sxs-lookup"><span data-stu-id="9c42c-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="9c42c-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="9c42c-134">SkipComputerRename</span></span> | <span data-ttu-id="9c42c-135">Überspringen von Neustarts, die von Umbenennungen eines Computers ausgelöst wurden.</span><span class="sxs-lookup"><span data-stu-id="9c42c-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="9c42c-136">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9c42c-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="9c42c-137">Unterstützt in Version 5.</span><span class="sxs-lookup"><span data-stu-id="9c42c-137">Supported in v5.</span></span> <span data-ttu-id="9c42c-138">Führt die Ressource als angegebener Benutzer aus.</span><span class="sxs-lookup"><span data-stu-id="9c42c-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="9c42c-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9c42c-139">DependsOn</span></span> | <span data-ttu-id="9c42c-140">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="9c42c-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9c42c-141">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="9c42c-142">Weitere Informationen finden Sie unter [Using DependsOn (Verwenden von „DependsOn“)](resource-depends-on.md).</span><span class="sxs-lookup"><span data-stu-id="9c42c-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="9c42c-143">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9c42c-143">Example</span></span>

<span data-ttu-id="9c42c-144">Das folgende Beispiel installiert Microsoft Exchange mithilfe der [xExchange](https://github.com/PowerShell/xExchange)-Ressource.</span><span class="sxs-lookup"><span data-stu-id="9c42c-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="9c42c-145">Während der kompletten Installation wird die **xPendingReboot**-Ressource verwendet, um den Knoten neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="9c42c-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="9c42c-146">Für dieses Beispiel sind die Anmeldeinformationen eines Kontos erforderlich, das berechtigt ist, der Gesamtstruktur einen Exchange-Server hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9c42c-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="9c42c-147">Weitere Informationen zur Verwendung von Anmeldeinformationen in DSC finden Sie unter [Handling Credentials in DSC (Verwendung von Anmeldeinformationen in DSC)](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="9c42c-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
> <span data-ttu-id="9c42c-148">In diesem Beispiel wird davon ausgegangen, dass Sie Ihren lokalen Konfigurations-Manager so konfiguriert haben, dass Neustarts erlaubt sind, und die Konfiguration nach einem Neustart fortgesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="9c42c-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="9c42c-149">Speicherorte für Downloads</span><span class="sxs-lookup"><span data-stu-id="9c42c-149">Where to Download</span></span>

<span data-ttu-id="9c42c-150">Sie können die in diesem Thema verwendeten Ressourcen an folgenden Speicherorten abspeichern, oder mithilfe des PowerShell-Katalogs.</span><span class="sxs-lookup"><span data-stu-id="9c42c-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="9c42c-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="9c42c-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="9c42c-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="9c42c-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
