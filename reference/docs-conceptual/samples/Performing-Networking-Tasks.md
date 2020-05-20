---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ausführen von Netzwerkaufgaben
ms.openlocfilehash: e0aa3b8ef3d911ab0fe851f6621d70e1265c5bd4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737201"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="3ccea-103">Ausführen von Netzwerkaufgaben</span><span class="sxs-lookup"><span data-stu-id="3ccea-103">Performing Networking Tasks</span></span>

<span data-ttu-id="3ccea-104">Weil TCP/IP das am häufigsten verwendete Netzwerkprotokoll ist, geht es bei den meisten Aufgaben zur grundlegenden Netzwerkprotokollverwaltung um TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="3ccea-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="3ccea-105">In diesem Abschnitt werden PowerShell und WMI verwendet, um diese Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-105">In this section, we use PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="3ccea-106">Auflisten der IP-Adressen für einen Computer</span><span class="sxs-lookup"><span data-stu-id="3ccea-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="3ccea-107">Um alle IP-Adressen abzurufen, die auf dem lokalen Computer verwendet werden, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3ccea-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

<span data-ttu-id="3ccea-108">Die Ausgabe dieses Befehls unterscheidet sich von den meisten Eigenschaftenlisten, weil die jeweiligen Werte in geschweiften Klammern stehen:</span><span class="sxs-lookup"><span data-stu-id="3ccea-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

<span data-ttu-id="3ccea-109">Untersuchen Sie mithilfe des Cmdlets `Get-Member` die Eigenschaft **IPAddress**, um zu verstehen, warum die geschweiften Klammern angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="3ccea-109">To understand why the braces appear, use the `Get-Member` cmdlet to examine the **IPAddress** property:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

<span data-ttu-id="3ccea-110">Die „IPAdress“-Eigenschaft für jede Netzwerkkarte ist tatsächlich ein Array.</span><span class="sxs-lookup"><span data-stu-id="3ccea-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="3ccea-111">Die geschweiften Klammern in der Definition kennzeichnen, dass **IPAdress** ein **System.String**-Wert ist, allerdings ein Array von **System.String**-Werten.</span><span class="sxs-lookup"><span data-stu-id="3ccea-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="3ccea-112">Auflisten von IP-Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="3ccea-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="3ccea-113">Um die detaillierten IP-Konfigurationsdaten für jede Netzwerkkarte anzuzeigen, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3ccea-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

<span data-ttu-id="3ccea-114">Die Standardanzeige für das Konfigurationsobjekt einer Netzwerkkarte ist ein sehr eingeschränkter Satz der verfügbaren Informationen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="3ccea-115">Für eine ausführliche Überprüfung und Problembehandlung verwenden Sie das Cmdlet `Select-Object` oder ein Formatierungs-Cmdlet wie z. B. `Format-List`, um die anzuzeigenden Eigenschaften anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3ccea-115">For in-depth inspection and troubleshooting, use `Select-Object` or a formatting cmdlet, such as `Format-List`, to specify the properties to be displayed.</span></span>

<span data-ttu-id="3ccea-116">In einem modernen TCP/IP-Netzwerk sind IPX- oder WINS-Eigenschaften wahrscheinlich nicht von Interesse.</span><span class="sxs-lookup"><span data-stu-id="3ccea-116">In modern TCP/IP networks you are probably not interested in IPX or WINS properties.</span></span> <span data-ttu-id="3ccea-117">Sie können den Parameter **ExcludeProperty** von `Select-Object` verwenden, um Eigenschaften auszublenden, die mit „WINS“ oder „IPX“ beginnen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-117">You can use the **ExcludeProperty** parameter of `Select-Object` to hide properties with names that begin with "WINS" or "IPX".</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="3ccea-118">Dieser Befehl gibt detaillierte Informationen zu DHCP, DNS, Routing und einigen unwesentlicheren IP-Konfigurationseigenschaften zurück.</span><span class="sxs-lookup"><span data-stu-id="3ccea-118">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="3ccea-119">Pingen von Computern</span><span class="sxs-lookup"><span data-stu-id="3ccea-119">Pinging Computers</span></span>

<span data-ttu-id="3ccea-120">Sie können einen einfachen Ping zu einem Computer ausführen, indem Sie **Win32_PingStatus** verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-120">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="3ccea-121">Der folgende Befehl führt den Ping aus, gibt jedoch eine ausführliche Ausgabe zurück:</span><span class="sxs-lookup"><span data-stu-id="3ccea-121">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

<span data-ttu-id="3ccea-122">Eine nützlichere Form für Zusammenfassungsinformationen ist eine Anzeige der Eigenschaften „Address“, „ResponseTime“ und „StatusCode“, wie sie vom folgenden Befehl generiert wird.</span><span class="sxs-lookup"><span data-stu-id="3ccea-122">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="3ccea-123">Der **Autosize**-Parameter von `Format-Table` bewirkt eine Breitenänderung der Tabellenspalten, sodass diese ordnungsgemäß in PowerShell angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-123">The **Autosize** parameter of `Format-Table` resizes the table columns so that they display properly in PowerShell.</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="3ccea-124">Ein StatusCode von 0 weist auf einen erfolgreichen Pingvorgang hin.</span><span class="sxs-lookup"><span data-stu-id="3ccea-124">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="3ccea-125">Sie können ein Array verwenden, um mehrere Computer mit einem einzigen Befehl zu pingen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-125">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="3ccea-126">Da es mehrere Adressen gibt, verwenden Sie das Cmdlet `ForEach-Object`, um jede Adresse einzeln zu pingen:</span><span class="sxs-lookup"><span data-stu-id="3ccea-126">Because there is more than one address, use the `ForEach-Object` to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

<span data-ttu-id="3ccea-127">Mit dem gleichen Befehlsformat können Sie alle Computer in einem Subnetz pingen, beispielsweise in einem privaten Netzwerk, in dem die Netzwerknummer 192.168.1.0 und eine standardmäßige Klasse-C-Subnetzmaske (255.255.255.0) verwendet wird. Nur Adressen im Bereich von 192.168.1.1 bis 192.168.1.254 sind zulässige lokale Adressen (0 ist immer für die Netzwerknummer reserviert, und 255 ist eine Subnetz-Broadcastadresse).</span><span class="sxs-lookup"><span data-stu-id="3ccea-127">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="3ccea-128">Um ein Array der Zahlen von 1 bis 254 in PowerShell darzustellen, verwenden Sie die Anweisung **1..254**.</span><span class="sxs-lookup"><span data-stu-id="3ccea-128">To represent an array of the numbers from 1 through 254 in PowerShell, use the statement **1..254.**</span></span>
<span data-ttu-id="3ccea-129">Ein vollständiges Subnetz-Ping kann ausgeführt werden, indem das Array erstellt und dann jeder Wert zu einer unvollständigen Adresse in der Ping-Anweisung hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="3ccea-129">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="3ccea-130">Diese Vorgehensweise zum Generieren eines Adressbereichs kann auch an jeder anderen Stelle verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-130">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="3ccea-131">Sie können einen vollständigen Satz von Adressen auf diese Weise generieren:</span><span class="sxs-lookup"><span data-stu-id="3ccea-131">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="3ccea-132">Abrufen von Netzwerkkarteneigenschaften</span><span class="sxs-lookup"><span data-stu-id="3ccea-132">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="3ccea-133">Wie bereits erwähnt, können Sie allgemeine Konfigurationseigenschaften über die Klasse **Win32_NetworkAdapterConfiguration** abrufen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-133">Earlier, we mentioned that you could retrieve general configuration properties using the **Win32_NetworkAdapterConfiguration** class.</span></span> <span data-ttu-id="3ccea-134">Netzwerkkarteninformationen wie MAC-Adressen und Kartentypen sind zwar keine TCP/IP-Informationen, können aber trotzdem nützlich sein, um zu verstehen, was mit einem Computer los ist.</span><span class="sxs-lookup"><span data-stu-id="3ccea-134">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="3ccea-135">Um eine Zusammenfassung dieser Informationen zu erhalten, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3ccea-135">To get a summary of this information, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="3ccea-136">Zuweisen der DNS-Domäne für eine Netzwerkkarte</span><span class="sxs-lookup"><span data-stu-id="3ccea-136">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="3ccea-137">Wenn Sie die DNS-Domäne für die automatische Namensauflösung zuweisen möchten, verwenden Sie die Methode **SetDNSDomain** von **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="3ccea-137">To assign the DNS domain for automatic name resolution, use the **SetDNSDomain** method of the **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="3ccea-138">Da Sie die DNS-Domäne für jede Netzwerkadapterkonfiguration unabhängig voneinander zuweisen, müssen Sie eine `ForEach-Object`-Anweisung verwenden, um die Domäne jedem Adapter zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="3ccea-138">Because you assign the DNS domain for each network adapter configuration independently, you need to use a `ForEach-Object` statement to assign the domain to each adapter:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="3ccea-139">Die Filteranweisung `IPEnabled=$true` ist erforderlich, da selbst in einem Netzwerk, in dem nur TCP/IP verwendet wird, verschiedene Netzwerkadapterkonfigurationen auf einem Computer keine wirklichen TCP/IP-Adapter sind. Es handelt sich um allgemeine Softwareelemente, die RAS, PPTP, QoS und andere Dienste für alle Adapter unterstützen und deshalb keine eigene Adresse aufweisen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-139">The filtering statement `IPEnabled=$true` is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="3ccea-140">Sie können den Befehl filtern, indem Sie anstelle des Filters `Get-CimInstance` das Cmdlet `Where-Object` verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-140">You can filter the command by using the `Where-Object` cmdlet, instead of using the `Get-CimInstance` filter.</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="3ccea-141">Ausführen von DHCP-Konfigurationsaufgaben</span><span class="sxs-lookup"><span data-stu-id="3ccea-141">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="3ccea-142">Ein Ändern von DHCP-Details umfasst das Arbeiten mit einem Satz von Netzwerkkarten, ähnlich wie dies bei der DNS-Konfiguration der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="3ccea-142">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="3ccea-143">Es gibt mehrere unterschiedliche Aktionen, die Sie über WMI ausführen können. Einige der üblichen Aktionen werden hier durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-143">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="3ccea-144">Ermitteln der DHCP-fähigen Netzwerkkarten</span><span class="sxs-lookup"><span data-stu-id="3ccea-144">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="3ccea-145">Um die DHCP-fähigen Netzwerkkarten auf einem Computer zu ermitteln, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3ccea-145">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

<span data-ttu-id="3ccea-146">Wenn Sie Netzwerkkarten mit IP-Konfigurationsproblemen ausschließen möchten, können Sie so vorgehen, dass Sie nur IP-fähige Netzwerkkarten abrufen:</span><span class="sxs-lookup"><span data-stu-id="3ccea-146">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="3ccea-147">Abrufen von DHCP-Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="3ccea-147">Retrieving DHCP Properties</span></span>

<span data-ttu-id="3ccea-148">Da DHCP-bezogene Eigenschaften für einen Adapter grundsätzlich mit `DHCP` beginnen, können Sie den Property-Parameter von `Format-Table` verwenden, um ausschließlich diese Eigenschaften anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="3ccea-148">Because DHCP-related properties for an adapter generally begin with `DHCP`, you can use the Property parameter of `Format-Table` to display only those properties:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="3ccea-149">Aktivieren von DHCP auf jeder Netzwerkkarte</span><span class="sxs-lookup"><span data-stu-id="3ccea-149">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="3ccea-150">Wenn Sie DHCP auf allen Netzwerkkarten aktivieren möchten, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="3ccea-150">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="3ccea-151">Sie können die **Filter**-Anweisung `IPEnabled=$true and DHCPEnabled=$false` verwenden, um eine DHCP-Aktivierung zu vermeiden, wenn DHCP bereits aktiviert ist. Es wird jedoch kein Fehler verursacht, wenn dieser Schritt ausgelassen wird.</span><span class="sxs-lookup"><span data-stu-id="3ccea-151">You can use the **Filter** statement `IPEnabled=$true and DHCPEnabled=$false` to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="3ccea-152">Freigeben und Erneuern von DHCP-Leases auf bestimmten Netzwerkkarten</span><span class="sxs-lookup"><span data-stu-id="3ccea-152">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="3ccea-153">Die **Win32_NetworkAdapterConfiguration**-Klasse hat die Methoden **ReleaseDHCPLease** und **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="3ccea-153">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="3ccea-154">Beide werden auf die gleiche Weise verwendet.</span><span class="sxs-lookup"><span data-stu-id="3ccea-154">Both are used in the same way.</span></span> <span data-ttu-id="3ccea-155">Üblicherweise verwenden Sie diese Methoden, wenn Sie nur Adressen für eine Netzwerkkarte in einem bestimmten Subnetz freigeben oder erneuern müssen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-155">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="3ccea-156">Die einfachste Möglichkeit zum Filtern von Netzwerkkarten in einem Subnetz besteht darin, nur die Netzwerkkartenkonfigurationen auswählen, die das Gateway für das Subnetz verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-156">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="3ccea-157">Beispielsweise gibt der folgende Befehl alle DHCP-Leases auf Netzwerkkarten des lokalen Computers frei, die DHCP-Leases von 192.168.1.254 erhalten:</span><span class="sxs-lookup"><span data-stu-id="3ccea-157">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="3ccea-158">Die einzige Änderung für die Erneuerung einer DHCP-Lease ist die, dass die **RenewDHCPLease**-Methode anstelle der **ReleaseDHCPLease**-Methode verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="3ccea-158">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="3ccea-159">Wenn Sie diese Methoden auf einem Remotecomputer verwenden, sollten Sie daran denken, dass der Zugriff auf das Remotesystem verloren gehen kann, wenn die Verbindung mit dem System über die Netzwerkkarte mit der freigegebenen oder erneuerten Lease besteht.</span><span class="sxs-lookup"><span data-stu-id="3ccea-159">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="3ccea-160">Freigeben und Erneuern von DHCP-Leases auf allen Netzwerkkarten</span><span class="sxs-lookup"><span data-stu-id="3ccea-160">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="3ccea-161">Sie können globale DHCP-Adressfreigaben oder -erneuerungen auf allen Netzwerkkarten ausführen, indem Sie die **Win32_NetworkAdapterConfiguration**-Methoden **ReleaseDHCPLeaseAll** und **RenewDHCPLeaseAll** verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-161">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span>
<span data-ttu-id="3ccea-162">Allerdings muss der Befehl auf die WMI-Klasse statt auf eine bestimmte Netzwerkkarte angewendet werden, weil globales Freigeben und Erneuern von Leases für die Klasse, nicht für eine bestimmte Netzwerkkarte ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3ccea-162">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="3ccea-163">Sie können einen Verweis auf eine WMI-Klasse anstelle von Klasseninstanzen abrufen, indem Sie alle WMI-Klassen auflisten und dann nur die gewünschte Klasse nach Name auswählen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-163">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="3ccea-164">Beispielsweise gibt der folgende Befehl die **Win32_NetworkAdapterConfiguration**-Klasse zurück:</span><span class="sxs-lookup"><span data-stu-id="3ccea-164">For example, the following command returns the **Win32_NetworkAdapterConfiguration** class:</span></span>

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="3ccea-165">Sie können den gesamten Befehl als die Klasse behandeln und dann die **ReleaseDHCPAdapterLease**-Methode für ihn aufrufen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-165">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="3ccea-166">Im folgenden Befehl wird PowerShell durch die Klammern um die Pipelineelemente `Get-CimInstance` und `Where-Object` angewiesen, diese zuerst auszuwerten:</span><span class="sxs-lookup"><span data-stu-id="3ccea-166">In the following command, the parentheses surrounding the `Get-CimInstance` and `Where-Object` pipeline elements direct PowerShell to evaluate them first:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="3ccea-167">Sie können das gleiche Befehlsformat verwenden, um die **RenewDHCPLeaseAll**-Methode aufzurufen:</span><span class="sxs-lookup"><span data-stu-id="3ccea-167">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="3ccea-168">Erstellen einer Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="3ccea-168">Creating a Network Share</span></span>

<span data-ttu-id="3ccea-169">Um eine Netzwerkfreigabe zu erstellen, verwenden Sie die Methode **Create** von **Win32_Share**:</span><span class="sxs-lookup"><span data-stu-id="3ccea-169">To create a network share, use the **Create** method of **Win32_Share**:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

<span data-ttu-id="3ccea-170">Sie können die Freigabe auch erstellen, indem Sie `net share` in PowerShell unter Windows verwenden:</span><span class="sxs-lookup"><span data-stu-id="3ccea-170">You can also create the share by using `net share` in PowerShell on Windows:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="3ccea-171">Entfernen einer Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="3ccea-171">Removing a Network Share</span></span>

<span data-ttu-id="3ccea-172">Sie können eine Netzwerkfreigabe mit **Win32_Share** entfernen, aber der Vorgang unterscheidet sich etwas vom Erstellen einer Freigabe, weil Sie die bestimmte zu entfernende Freigabe anstelle der **Win32_Share**-Klasse abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="3ccea-172">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="3ccea-173">Mit der folgenden Anweisung wird die Freigabe **TempShare** gelöscht:</span><span class="sxs-lookup"><span data-stu-id="3ccea-173">The following statement deletes the share **TempShare**:</span></span>

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="3ccea-174">Unter Windows funktioniert `net share` ebenfalls:</span><span class="sxs-lookup"><span data-stu-id="3ccea-174">In Windows, `net share` works as well:</span></span>

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="3ccea-175">Verbinden eines für Windows verfügbaren Netzlaufwerks</span><span class="sxs-lookup"><span data-stu-id="3ccea-175">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="3ccea-176">Das Cmdlet `New-PSDrive` erstellt ein PowerShell-Laufwerk, aber auf diese Weise erstellte Laufwerke sind nur für PowerShell verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3ccea-176">The `New-PSDrive` cmdlets creates a PowerShell drive, but drives created this way are available only to PowerShell.</span></span> <span data-ttu-id="3ccea-177">Um ein neues Netzlaufwerk zu erstellen, können Sie das **WScript.Network**-COM-Objekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="3ccea-177">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="3ccea-178">Durch den folgenden Befehl wird die Freigabe `\\FPS01\users` dem lokalen Laufwerk `B:` zugeordnet:</span><span class="sxs-lookup"><span data-stu-id="3ccea-178">The following command maps the share `\\FPS01\users` to local drive `B:`,</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="3ccea-179">Unter Windows funktioniert der Befehl `net use` ebenfalls:</span><span class="sxs-lookup"><span data-stu-id="3ccea-179">On Windows, the `net use` command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="3ccea-180">Laufwerke, die entweder mit **WScript.Network** oder `net use` zugeordnet wurden, sind sofort für PowerShell verfügbar.</span><span class="sxs-lookup"><span data-stu-id="3ccea-180">Drives mapped with either **WScript.Network** or `net use` are immediately available to PowerShell.</span></span>
