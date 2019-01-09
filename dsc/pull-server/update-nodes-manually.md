---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Aktualisieren von Knoten von einem Pullserver
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401127"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="65c22-103">Aktualisieren von Knoten von einem Pullserver</span><span class="sxs-lookup"><span data-stu-id="65c22-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="65c22-104">In den folgenden Abschnitten wird davon ausgegangen, dass Sie bereits einen Pull-Server eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="65c22-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="65c22-105">Wenn Sie Ihre Pull-Server nicht eingerichtet haben, können Sie die folgenden Handbüchern:</span><span class="sxs-lookup"><span data-stu-id="65c22-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="65c22-106">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="65c22-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="65c22-107">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="65c22-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="65c22-108">Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="65c22-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="65c22-109">In diesem Artikel wird zeigen, wie Ressourcen hochladen, damit sie die heruntergeladen werden, und Konfigurieren von Clients zum automatischen Herunterladen von Ressourcen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="65c22-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="65c22-110">Zeitpunkt des Knotens eine zugewiesenen Konfiguration und empfängt, über **Pull** oder **Push** (v5), automatisch heruntergeladen von der Konfiguration aus dem Speicherort, die im LCM angegebene erforderlichen Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="65c22-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="65c22-111">Verwenden das Cmdlet "Update-DSCConfiguration"</span><span class="sxs-lookup"><span data-stu-id="65c22-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="65c22-112">In PowerShell 5.0 ab der [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) Cmdlet erzwingt einen Knoten, dessen Konfiguration vom Pullserver in der LCM konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="65c22-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="65c22-113">Mithilfe von Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="65c22-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="65c22-114">In PowerShell 4.0 können Sie immer noch manuell erzwingen ein Pull-Client zum Aktualisieren der Konfiguration mit [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="65c22-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="65c22-115">Das folgende Beispiel erstellt eine CIM-Sitzung mit den angegebenen Anmeldeinformationen, ruft die entsprechende CIM-Methode und die Sitzung entfernt.</span><span class="sxs-lookup"><span data-stu-id="65c22-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="65c22-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="65c22-116">See Also</span></span>

[<span data-ttu-id="65c22-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="65c22-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
