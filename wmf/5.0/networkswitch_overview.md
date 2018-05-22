---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 11b5e36f703c242e0bc820ab19d11d39305fa90c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="f992c-102">Verwalten von Netzwerkswitches mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="f992c-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="f992c-103">Das Cmdlet **Get-NetworkSwitchEthernetPort** gibt nun die folgenden zusätzlichen Informationen für Instanzen zurück:</span><span class="sxs-lookup"><span data-stu-id="f992c-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="f992c-104">„IPAddress“ – die dem Port zugeordnete IP-Adresse</span><span class="sxs-lookup"><span data-stu-id="f992c-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="f992c-105">PortMode – der Portmodus: „access“, „route“ oder „trunk“</span><span class="sxs-lookup"><span data-stu-id="f992c-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="f992c-106">AccessVLAN – die diesem Port im Modus „access“ zugeordnete ID des VLAN</span><span class="sxs-lookup"><span data-stu-id="f992c-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="f992c-107">TrunkedVLANList – die diesem Port im Modus „trunk“ zugeordnete Listen von IDs von VLANs</span><span class="sxs-lookup"><span data-stu-id="f992c-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="f992c-108">Grundlegende Verwaltung von Netzwerkswitches mit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f992c-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="f992c-109">Die „NetworkSwitch“-Cmdlets, die in WMF 5.0 eingeführt wurden, ermöglichen Ihnen Netzwerkswitches, die mit dem Windows Server 2012 R2-Logo zertifiziert sind, mit einer Switch-, VLAN- und grundlegenden Layer 2-Netzwerkswitch-Konfiguration zu versehen.</span><span class="sxs-lookup"><span data-stu-id="f992c-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="f992c-110">Microsoft unterstützt weiterhin das [Datacenter Abstraction Layer](http://technet.microsoft.com/cloud/dal.aspx)-Konzept (DAL), um Kunden und Partnern weiter einen Nutzen zu bieten.</span><span class="sxs-lookup"><span data-stu-id="f992c-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="f992c-111">Mithilfe dieser Cmdlets können Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="f992c-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="f992c-112">Globale Switchkonfiguration, wie z. B.:</span><span class="sxs-lookup"><span data-stu-id="f992c-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="f992c-113">Hostnamen festlegen</span><span class="sxs-lookup"><span data-stu-id="f992c-113">Set host name</span></span>
    - <span data-ttu-id="f992c-114">Switchbanner festlegen</span><span class="sxs-lookup"><span data-stu-id="f992c-114">Set switch banner</span></span>
    - <span data-ttu-id="f992c-115">Konfiguration dauerhaft speichern</span><span class="sxs-lookup"><span data-stu-id="f992c-115">Persist configuration</span></span>
    - <span data-ttu-id="f992c-116">Features aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="f992c-116">Enable or disable feature</span></span>

- <span data-ttu-id="f992c-117">VLAN-Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="f992c-117">VLAN configuration:</span></span>
    - <span data-ttu-id="f992c-118">VLAN erstellen oder entfernen</span><span class="sxs-lookup"><span data-stu-id="f992c-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="f992c-119">VLAN aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="f992c-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="f992c-120">VLAN auflisten</span><span class="sxs-lookup"><span data-stu-id="f992c-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="f992c-121">Anzeigenamen für ein VLAN festlegen</span><span class="sxs-lookup"><span data-stu-id="f992c-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="f992c-122">Layer 2-Portkonfiguration:</span><span class="sxs-lookup"><span data-stu-id="f992c-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="f992c-123">Ports auflisten</span><span class="sxs-lookup"><span data-stu-id="f992c-123">Enumerate ports</span></span>
    - <span data-ttu-id="f992c-124">Ports aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="f992c-124">Enable or disable ports</span></span>
    - <span data-ttu-id="f992c-125">Portmodi und -eigenschaften festlegen</span><span class="sxs-lookup"><span data-stu-id="f992c-125">Set port modes and properties</span></span>
    - <span data-ttu-id="f992c-126">VLAN im Modus „Access“ oder „Trunk“ für den Port hinzufügen oder zuordnen</span><span class="sxs-lookup"><span data-stu-id="f992c-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="f992c-127">Machen Sie sich am besten mit allen „NetworkSwitch“-Cmdlets vertraut!</span><span class="sxs-lookup"><span data-stu-id="f992c-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="f992c-128">Weitere Informationen finden Sie im Blogbeitrag von Jeffrey Snover mit der Ankündigung der WMF 5.0 Preview-Version: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="f992c-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
