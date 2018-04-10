---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2b6b81d250c3d745f3ab21ebadb9a657583638b0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="ae11e-102">Verwalten von Netzwerkswitches mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae11e-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="ae11e-103">Das Cmdlet **Get-NetworkSwitchEthernetPort** gibt nun die folgenden zusätzlichen Informationen für Instanzen zurück:</span><span class="sxs-lookup"><span data-stu-id="ae11e-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="ae11e-104">„IPAddress“ – die dem Port zugeordnete IP-Adresse</span><span class="sxs-lookup"><span data-stu-id="ae11e-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="ae11e-105">PortMode – der Portmodus: „access“, „route“ oder „trunk“</span><span class="sxs-lookup"><span data-stu-id="ae11e-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="ae11e-106">AccessVLAN – die diesem Port im Modus „access“ zugeordnete ID des VLAN</span><span class="sxs-lookup"><span data-stu-id="ae11e-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="ae11e-107">TrunkedVLANList – die diesem Port im Modus „trunk“ zugeordnete Listen von IDs von VLANs</span><span class="sxs-lookup"><span data-stu-id="ae11e-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="ae11e-108">Grundlegende Verwaltung von Netzwerkswitches mit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae11e-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="ae11e-109">Die „NetworkSwitch“-Cmdlets, die in WMF 5.0 eingeführt wurden, ermöglichen Ihnen Netzwerkswitches, die mit dem Windows Server 2012 R2-Logo zertifiziert sind, mit einer Switch-, VLAN- und grundlegenden Layer 2-Netzwerkswitch-Konfiguration zu versehen.</span><span class="sxs-lookup"><span data-stu-id="ae11e-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="ae11e-110">Microsoft unterstützt weiterhin das [Datacenter Abstraction Layer](http://technet.microsoft.com/cloud/dal.aspx)-Konzept (DAL), um Kunden und Partnern weiter einen Nutzen zu bieten.</span><span class="sxs-lookup"><span data-stu-id="ae11e-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="ae11e-111">Mithilfe dieser Cmdlets können Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="ae11e-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="ae11e-112">Globale Switchkonfiguration, wie z. B.:</span><span class="sxs-lookup"><span data-stu-id="ae11e-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="ae11e-113">Hostnamen festlegen</span><span class="sxs-lookup"><span data-stu-id="ae11e-113">Set host name</span></span>
    - <span data-ttu-id="ae11e-114">Switchbanner festlegen</span><span class="sxs-lookup"><span data-stu-id="ae11e-114">Set switch banner</span></span>
    - <span data-ttu-id="ae11e-115">Konfiguration dauerhaft speichern</span><span class="sxs-lookup"><span data-stu-id="ae11e-115">Persist configuration</span></span>
    - <span data-ttu-id="ae11e-116">Features aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="ae11e-116">Enable or disable feature</span></span>

- <span data-ttu-id="ae11e-117">VLAN-Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="ae11e-117">VLAN configuration:</span></span>
    - <span data-ttu-id="ae11e-118">VLAN erstellen oder entfernen</span><span class="sxs-lookup"><span data-stu-id="ae11e-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="ae11e-119">VLAN aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="ae11e-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="ae11e-120">VLAN auflisten</span><span class="sxs-lookup"><span data-stu-id="ae11e-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="ae11e-121">Anzeigenamen für ein VLAN festlegen</span><span class="sxs-lookup"><span data-stu-id="ae11e-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="ae11e-122">Layer 2-Portkonfiguration:</span><span class="sxs-lookup"><span data-stu-id="ae11e-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="ae11e-123">Ports auflisten</span><span class="sxs-lookup"><span data-stu-id="ae11e-123">Enumerate ports</span></span>
    - <span data-ttu-id="ae11e-124">Ports aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="ae11e-124">Enable or disable ports</span></span>
    - <span data-ttu-id="ae11e-125">Portmodi und -eigenschaften festlegen</span><span class="sxs-lookup"><span data-stu-id="ae11e-125">Set port modes and properties</span></span>
    - <span data-ttu-id="ae11e-126">VLAN im Modus „Access“ oder „Trunk“ für den Port hinzufügen oder zuordnen</span><span class="sxs-lookup"><span data-stu-id="ae11e-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="ae11e-127">Machen Sie sich am besten mit allen „NetworkSwitch“-Cmdlets vertraut!</span><span class="sxs-lookup"><span data-stu-id="ae11e-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="ae11e-128">Weitere Informationen finden Sie im Blogbeitrag von Jeffrey Snover mit der Ankündigung der WMF 5.0 Preview-Version: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="ae11e-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>