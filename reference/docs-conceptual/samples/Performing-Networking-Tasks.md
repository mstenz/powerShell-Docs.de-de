---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ausführen von Netzwerkaufgaben
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030862"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="a91ba-103">Ausführen von Netzwerkaufgaben</span><span class="sxs-lookup"><span data-stu-id="a91ba-103">Performing Networking Tasks</span></span>

<span data-ttu-id="a91ba-104">Weil TCP/IP das am häufigsten verwendete Netzwerkprotokoll ist, geht es bei den meisten Aufgaben zur grundlegenden Netzwerkprotokollverwaltung um TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="a91ba-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="a91ba-105">In diesem Abschnitt werden Windows PowerShell und WMI verwendet, um diese Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="a91ba-106">Auflisten der IP-Adressen für einen Computer</span><span class="sxs-lookup"><span data-stu-id="a91ba-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="a91ba-107">Um alle IP-Adressen abzurufen, die auf dem lokalen Computer verwendet werden, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a91ba-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="a91ba-108">Die Ausgabe dieses Befehls unterscheidet sich von den meisten Eigenschaftenlisten, weil die jeweiligen Werte in geschweiften Klammern stehen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="a91ba-109">Um zu verstehen, warum die geschweiften Klammern angezeigt werden, verwenden Sie das Cmdlet „Get-Member“, um sich die **IPAddress**-Eigenschaft anzusehen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="a91ba-110">Die „IPAdress“-Eigenschaft für jede Netzwerkkarte ist tatsächlich ein Array.</span><span class="sxs-lookup"><span data-stu-id="a91ba-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="a91ba-111">Die geschweiften Klammern in der Definition kennzeichnen, dass **IPAdress** ein **System.String**-Wert ist, allerdings ein Array von **System.String**-Werten.</span><span class="sxs-lookup"><span data-stu-id="a91ba-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="a91ba-112">Auflisten von IP-Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="a91ba-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="a91ba-113">Um die detaillierten IP-Konfigurationsdaten für jede Netzwerkkarte anzuzeigen, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a91ba-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="a91ba-114">Die Standardanzeige für das Konfigurationsobjekt einer Netzwerkkarte ist ein sehr eingeschränkter Satz der verfügbaren Informationen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="a91ba-115">Für eine ausführliche Überprüfung und Problembehandlung verwenden Sie das Cmdlet „Select-Object“ oder ein Formatierungs-Cmdlet, etwa „Format-List“, um die anzuzeigenden Eigenschaften anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a91ba-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="a91ba-116">Wenn Sie nicht an den IPX- oder WINS-Eigenschaften interessiert sind – was in einem modernen TCP/IP-Netzwerk wahrscheinlich der Fall ist –, können Sie den „ExcludeProperty“-Parameter von „Select-Object“ verwenden, um Eigenschaften auszublenden, deren Namen mit „WINS“ oder „IPX“ beginnen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="a91ba-117">Dieser Befehl gibt detaillierte Informationen zu DHCP, DNS, Routing und einigen unwesentlicheren IP-Konfigurationseigenschaften zurück.</span><span class="sxs-lookup"><span data-stu-id="a91ba-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="a91ba-118">Pingen von Computern</span><span class="sxs-lookup"><span data-stu-id="a91ba-118">Pinging Computers</span></span>

<span data-ttu-id="a91ba-119">Sie können einen einfachen Ping zu einem Computer ausführen, indem Sie **Win32_PingStatus** verwenden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="a91ba-120">Der folgende Befehl führt den Ping aus, gibt jedoch eine ausführliche Ausgabe zurück:</span><span class="sxs-lookup"><span data-stu-id="a91ba-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="a91ba-121">Eine nützlichere Form für Zusammenfassungsinformationen ist eine Anzeige der Eigenschaften „Address“, „ResponseTime“ und „StatusCode“, wie sie vom folgenden Befehl generiert wird.</span><span class="sxs-lookup"><span data-stu-id="a91ba-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="a91ba-122">Der „Autosize“-Parameter von „Format-Table“ bewirkt eine Breitenänderung der Tabellenspalten, sodass diese ordnungsgemäß in Windows PowerShell angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="a91ba-123">Ein StatusCode von 0 weist auf einen erfolgreichen Pingvorgang hin.</span><span class="sxs-lookup"><span data-stu-id="a91ba-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="a91ba-124">Sie können ein Array verwenden, um mehrere Computer mit einem einzigen Befehl zu pingen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="a91ba-125">Da es mehrere Adressen gibt, verwenden Sie das Cmdlet **ForEach-Object**, um jede Adresse einzeln zu pingen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="a91ba-126">Mit dem gleichen Befehlsformat können Sie alle Computer in einem Subnetz pingen, beispielsweise in einem privaten Netzwerk, in dem die Netzwerknummer 192.168.1.0 und eine standardmäßige Klasse-C-Subnetzmaske (255.255.255.0) verwendet wird. Nur Adressen im Bereich von 192.168.1.1 bis 192.168.1.254 sind zulässige lokale Adressen (0 ist immer für die Netzwerknummer reserviert, und 255 ist eine Subnetz-Broadcastadresse).</span><span class="sxs-lookup"><span data-stu-id="a91ba-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="a91ba-127">Um ein Array der Zahlen von 1 bis 254 in Windows PowerShell darzustellen, verwenden Sie die Anweisung **1..254**.</span><span class="sxs-lookup"><span data-stu-id="a91ba-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="a91ba-128">Ein vollständiges Subnetz-Ping kann ausgeführt werden, indem das Array erstellt und dann jeder Wert zu einer unvollständigen Adresse in der Ping-Anweisung hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="a91ba-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="a91ba-129">Diese Vorgehensweise zum Generieren eines Adressbereichs kann auch an jeder anderen Stelle verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="a91ba-130">Sie können einen vollständigen Satz von Adressen auf diese Weise generieren:</span><span class="sxs-lookup"><span data-stu-id="a91ba-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="a91ba-131">Abrufen von Netzwerkkarteneigenschaften</span><span class="sxs-lookup"><span data-stu-id="a91ba-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="a91ba-132">Wie bereits in diesem Handbuch erläutert wurde, können Sie allgemeine Konfigurationseigenschaften über **Win32_NetworkAdapterConfiguration** abrufen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="a91ba-133">Netzwerkkarteninformationen wie MAC-Adressen und Kartentypen sind zwar keine TCP/IP-Informationen, können aber trotzdem nützlich sein, um zu verstehen, was mit einem Computer los ist.</span><span class="sxs-lookup"><span data-stu-id="a91ba-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="a91ba-134">Um eine Zusammenfassung dieser Informationen zu erhalten, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a91ba-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="a91ba-135">Zuweisen der DNS-Domäne für eine Netzwerkkarte</span><span class="sxs-lookup"><span data-stu-id="a91ba-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="a91ba-136">Wenn Sie die DNS-Domäne für automatische Namensauflösung zuweisen möchten, verwenden Sie die **Win32_NetworkAdapterConfiguration SetDNSDomain**-Methode.</span><span class="sxs-lookup"><span data-stu-id="a91ba-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="a91ba-137">Weil Sie die DNS-Domäne für jede Netzwerkkartenkonfiguration unabhängig zuweisen, müssen Sie eine **ForEach-Object**-Anweisung verwenden, um die Domäne jedem Adapter zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="a91ba-138">Die Filteranweisung „IPEnabled=$true“ ist erforderlich, da selbst in einem Netzwerk, in dem nur TCP/IP verwendet wird, verschiedene Netzwerkkartenkonfigurationen auf einem Computer keine wirklichen TCP/IP-Adapter sind. Sie sind allgemeine Softwareelemente, die RAS, PPTP, QoS und andere Dienste für alle Adapter unterstützen und daher keine eigenen Adressen haben.</span><span class="sxs-lookup"><span data-stu-id="a91ba-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="a91ba-139">Sie können den Befehl filtern, indem Sie das Cmdlet **Where-Object** anstelle des **Get-WmiObject**-Filters verwenden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="a91ba-140">Ausführen von DHCP-Konfigurationsaufgaben</span><span class="sxs-lookup"><span data-stu-id="a91ba-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="a91ba-141">Ein Ändern von DHCP-Details umfasst das Arbeiten mit einem Satz von Netzwerkkarten, ähnlich wie dies bei der DNS-Konfiguration der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="a91ba-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="a91ba-142">Es gibt mehrere unterschiedliche Aktionen, die Sie über WMI ausführen können. Einige der üblichen Aktionen werden hier durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="a91ba-143">Ermitteln der DHCP-fähigen Netzwerkkarten</span><span class="sxs-lookup"><span data-stu-id="a91ba-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="a91ba-144">Um die DHCP-fähigen Netzwerkkarten auf einem Computer zu ermitteln, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a91ba-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="a91ba-145">Wenn Sie Netzwerkkarten mit IP-Konfigurationsproblemen ausschließen möchten, können Sie so vorgehen, dass Sie nur IP-fähige Netzwerkkarten abrufen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="a91ba-146">Abrufen von DHCP-Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a91ba-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="a91ba-147">Da DHCP-bezogene Eigenschaften für eine Netzwerkkarte grundsätzlich mit „DHCP“ beginnen, können Sie den „Property“-Parameter von „Format-Table“ verwenden, um ausschließlich diese Eigenschaften anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="a91ba-148">Aktivieren von DHCP auf jeder Netzwerkkarte</span><span class="sxs-lookup"><span data-stu-id="a91ba-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="a91ba-149">Wenn Sie DHCP auf allen Netzwerkkarten aktivieren möchten, verwenden Sie den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="a91ba-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="a91ba-150">Sie können die **Filter**-Anweisung „IPEnabled=$true and DHCPEnabled=$false“ verwenden, um ein Aktivieren von DHCP dort zu vermeiden, wo es bereits aktiviert ist. Es werden jedoch keine Fehler verursacht, wenn dieser Schritt nicht erfolgt.</span><span class="sxs-lookup"><span data-stu-id="a91ba-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="a91ba-151">Freigeben und Erneuern von DHCP-Leases auf bestimmten Netzwerkkarten</span><span class="sxs-lookup"><span data-stu-id="a91ba-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="a91ba-152">Die **Win32_NetworkAdapterConfiguration**-Klasse hat die Methoden **ReleaseDHCPLease** und **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="a91ba-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="a91ba-153">Beide werden auf die gleiche Weise verwendet.</span><span class="sxs-lookup"><span data-stu-id="a91ba-153">Both are used in the same way.</span></span> <span data-ttu-id="a91ba-154">Üblicherweise verwenden Sie diese Methoden, wenn Sie nur Adressen für eine Netzwerkkarte in einem bestimmten Subnetz freigeben oder erneuern müssen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="a91ba-155">Die einfachste Möglichkeit zum Filtern von Netzwerkkarten in einem Subnetz besteht darin, nur die Netzwerkkartenkonfigurationen auswählen, die das Gateway für das Subnetz verwenden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="a91ba-156">Beispielsweise gibt der folgende Befehl alle DHCP-Leases auf Netzwerkkarten des lokalen Computers frei, die DHCP-Leases von 192.168.1.254 erhalten:</span><span class="sxs-lookup"><span data-stu-id="a91ba-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="a91ba-157">Die einzige Änderung für die Erneuerung einer DHCP-Lease ist die, dass die **RenewDHCPLease**-Methode anstelle der **ReleaseDHCPLease**-Methode verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="a91ba-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="a91ba-158">Wenn Sie diese Methoden auf einem Remotecomputer verwenden, sollten Sie daran denken, dass der Zugriff auf das Remotesystem verloren gehen kann, wenn die Verbindung mit dem System über die Netzwerkkarte mit der freigegebenen oder erneuerten Lease besteht.</span><span class="sxs-lookup"><span data-stu-id="a91ba-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="a91ba-159">Freigeben und Erneuern von DHCP-Leases auf allen Netzwerkkarten</span><span class="sxs-lookup"><span data-stu-id="a91ba-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="a91ba-160">Sie können globale DHCP-Adressfreigaben oder -erneuerungen auf allen Netzwerkkarten ausführen, indem Sie die **Win32_NetworkAdapterConfiguration**-Methoden **ReleaseDHCPLeaseAll** und **RenewDHCPLeaseAll** verwenden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="a91ba-161">Allerdings muss der Befehl auf die WMI-Klasse statt auf eine bestimmte Netzwerkkarte angewendet werden, weil globales Freigeben und Erneuern von Leases für die Klasse, nicht für eine bestimmte Netzwerkkarte ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a91ba-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="a91ba-162">Sie können einen Verweis auf eine WMI-Klasse anstelle von Klasseninstanzen abrufen, indem Sie alle WMI-Klassen auflisten und dann nur die gewünschte Klasse nach Name auswählen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="a91ba-163">Beispielsweise gibt der folgende Befehl die „Win32_NetworkAdapterConfiguration“-Klasse zurück:</span><span class="sxs-lookup"><span data-stu-id="a91ba-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="a91ba-164">Sie können den gesamten Befehl als die Klasse behandeln und dann die **ReleaseDHCPAdapterLease**-Methode für ihn aufrufen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="a91ba-165">Im folgenden Befehl weisen die Klammern, die die Pipelineelemente **Get-WmiObject** und **Where-Object** umschließen, Windows PowerShell an, diese zuerst auszuwerten:</span><span class="sxs-lookup"><span data-stu-id="a91ba-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="a91ba-166">Sie können das gleiche Befehlsformat verwenden, um die **RenewDHCPLeaseAll**-Methode aufzurufen:</span><span class="sxs-lookup"><span data-stu-id="a91ba-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="a91ba-167">Erstellen einer Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="a91ba-167">Creating a Network Share</span></span>

<span data-ttu-id="a91ba-168">Um eine Netzwerkfreigabe zu erstellen, verwenden Sie die **Win32_Share Create**-Methode:</span><span class="sxs-lookup"><span data-stu-id="a91ba-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="a91ba-169">Sie können die Freigabe auch erstellen, indem Sie **net share** in Windows PowerShell verwenden:</span><span class="sxs-lookup"><span data-stu-id="a91ba-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="a91ba-170">Entfernen einer Netzwerkfreigabe</span><span class="sxs-lookup"><span data-stu-id="a91ba-170">Removing a Network Share</span></span>

<span data-ttu-id="a91ba-171">Sie können eine Netzwerkfreigabe mit **Win32_Share** entfernen, aber der Vorgang unterscheidet sich etwas vom Erstellen einer Freigabe, weil Sie die bestimmte zu entfernende Freigabe anstelle der **Win32_Share**-Klasse abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="a91ba-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="a91ba-172">Mit der folgenden Anweisung wird die Freigabe „TempShare“ gelöscht:</span><span class="sxs-lookup"><span data-stu-id="a91ba-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="a91ba-173">**net share** funktioniert ebenfalls:</span><span class="sxs-lookup"><span data-stu-id="a91ba-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="a91ba-174">Verbinden eines für Windows verfügbaren Netzlaufwerks</span><span class="sxs-lookup"><span data-stu-id="a91ba-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="a91ba-175">Das Cmdlet **New-PSDrive** erstellt ein Windows PowerShell-Laufwerk, aber Laufwerke, die auf diese Weise erstellt wurden, sind nur für Windows PowerShell verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a91ba-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="a91ba-176">Um ein neues Netzlaufwerk zu erstellen, können Sie das **WScript.Network**-COM-Objekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="a91ba-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="a91ba-177">Im folgenden Befehl wird die Freigabe „\\\\FPS01\\users“ dem lokalen Laufwerk B: zugeordnet:</span><span class="sxs-lookup"><span data-stu-id="a91ba-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="a91ba-178">Der Befehl **net use** funktioniert ebenfalls:</span><span class="sxs-lookup"><span data-stu-id="a91ba-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="a91ba-179">Laufwerke, die entweder mit **WScript.Network** oder „net use“ zugeordnet wurden, sind sofort für Windows PowerShell verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a91ba-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>
