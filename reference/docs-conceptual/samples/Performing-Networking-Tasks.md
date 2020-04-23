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
# <a name="performing-networking-tasks"></a>Ausführen von Netzwerkaufgaben

Weil TCP/IP das am häufigsten verwendete Netzwerkprotokoll ist, geht es bei den meisten Aufgaben zur grundlegenden Netzwerkprotokollverwaltung um TCP/IP. In diesem Abschnitt werden PowerShell und WMI verwendet, um diese Aufgaben auszuführen.

## <a name="listing-ip-addresses-for-a-computer"></a>Auflisten der IP-Adressen für einen Computer

Um alle IP-Adressen abzurufen, die auf dem lokalen Computer verwendet werden, verwenden Sie den folgenden Befehl:

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

Die Ausgabe dieses Befehls unterscheidet sich von den meisten Eigenschaftenlisten, weil die jeweiligen Werte in geschweiften Klammern stehen:

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

Untersuchen Sie mithilfe des Cmdlets `Get-Member` die Eigenschaft **IPAddress**, um zu verstehen, warum die geschweiften Klammern angezeigt werden:

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

Die „IPAdress“-Eigenschaft für jede Netzwerkkarte ist tatsächlich ein Array. Die geschweiften Klammern in der Definition kennzeichnen, dass **IPAdress** ein **System.String**-Wert ist, allerdings ein Array von **System.String**-Werten.

## <a name="listing-ip-configuration-data"></a>Auflisten von IP-Konfigurationsdaten

Um die detaillierten IP-Konfigurationsdaten für jede Netzwerkkarte anzuzeigen, verwenden Sie den folgenden Befehl:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

Die Standardanzeige für das Konfigurationsobjekt einer Netzwerkkarte ist ein sehr eingeschränkter Satz der verfügbaren Informationen. Für eine ausführliche Überprüfung und Problembehandlung verwenden Sie das Cmdlet `Select-Object` oder ein Formatierungs-Cmdlet wie z. B. `Format-List`, um die anzuzeigenden Eigenschaften anzugeben.

In einem modernen TCP/IP-Netzwerk sind IPX- oder WINS-Eigenschaften wahrscheinlich nicht von Interesse. Sie können den Parameter **ExcludeProperty** von `Select-Object` verwenden, um Eigenschaften auszublenden, die mit „WINS“ oder „IPX“ beginnen.

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

Dieser Befehl gibt detaillierte Informationen zu DHCP, DNS, Routing und einigen unwesentlicheren IP-Konfigurationseigenschaften zurück.

## <a name="pinging-computers"></a>Pingen von Computern

Sie können einen einfachen Ping zu einem Computer ausführen, indem Sie **Win32_PingStatus** verwenden. Der folgende Befehl führt den Ping aus, gibt jedoch eine ausführliche Ausgabe zurück:

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

Eine nützlichere Form für Zusammenfassungsinformationen ist eine Anzeige der Eigenschaften „Address“, „ResponseTime“ und „StatusCode“, wie sie vom folgenden Befehl generiert wird. Der **Autosize**-Parameter von `Format-Table` bewirkt eine Breitenänderung der Tabellenspalten, sodass diese ordnungsgemäß in PowerShell angezeigt werden.

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Ein StatusCode von 0 weist auf einen erfolgreichen Pingvorgang hin.

Sie können ein Array verwenden, um mehrere Computer mit einem einzigen Befehl zu pingen. Da es mehrere Adressen gibt, verwenden Sie das Cmdlet `ForEach-Object`, um jede Adresse einzeln zu pingen:

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

Mit dem gleichen Befehlsformat können Sie alle Computer in einem Subnetz pingen, beispielsweise in einem privaten Netzwerk, in dem die Netzwerknummer 192.168.1.0 und eine standardmäßige Klasse-C-Subnetzmaske (255.255.255.0) verwendet wird. Nur Adressen im Bereich von 192.168.1.1 bis 192.168.1.254 sind zulässige lokale Adressen (0 ist immer für die Netzwerknummer reserviert, und 255 ist eine Subnetz-Broadcastadresse).

Um ein Array der Zahlen von 1 bis 254 in PowerShell darzustellen, verwenden Sie die Anweisung **1..254**.
Ein vollständiges Subnetz-Ping kann ausgeführt werden, indem das Array erstellt und dann jeder Wert zu einer unvollständigen Adresse in der Ping-Anweisung hinzugefügt wird:

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

Diese Vorgehensweise zum Generieren eines Adressbereichs kann auch an jeder anderen Stelle verwendet werden. Sie können einen vollständigen Satz von Adressen auf diese Weise generieren:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Abrufen von Netzwerkkarteneigenschaften

Wie bereits erwähnt, können Sie allgemeine Konfigurationseigenschaften über die Klasse **Win32_NetworkAdapterConfiguration** abrufen. Netzwerkkarteninformationen wie MAC-Adressen und Kartentypen sind zwar keine TCP/IP-Informationen, können aber trotzdem nützlich sein, um zu verstehen, was mit einem Computer los ist. Um eine Zusammenfassung dieser Informationen zu erhalten, verwenden Sie den folgenden Befehl:

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Zuweisen der DNS-Domäne für eine Netzwerkkarte

Wenn Sie die DNS-Domäne für die automatische Namensauflösung zuweisen möchten, verwenden Sie die Methode **SetDNSDomain** von **Win32_NetworkAdapterConfiguration**. Da Sie die DNS-Domäne für jede Netzwerkadapterkonfiguration unabhängig voneinander zuweisen, müssen Sie eine `ForEach-Object`-Anweisung verwenden, um die Domäne jedem Adapter zuzuweisen:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

Die Filteranweisung `IPEnabled=$true` ist erforderlich, da selbst in einem Netzwerk, in dem nur TCP/IP verwendet wird, verschiedene Netzwerkadapterkonfigurationen auf einem Computer keine wirklichen TCP/IP-Adapter sind. Es handelt sich um allgemeine Softwareelemente, die RAS, PPTP, QoS und andere Dienste für alle Adapter unterstützen und deshalb keine eigene Adresse aufweisen.

Sie können den Befehl filtern, indem Sie anstelle des Filters `Where-Object` das Cmdlet `Get-CimInstance` verwenden.

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Ausführen von DHCP-Konfigurationsaufgaben

Ein Ändern von DHCP-Details umfasst das Arbeiten mit einem Satz von Netzwerkkarten, ähnlich wie dies bei der DNS-Konfiguration der Fall ist. Es gibt mehrere unterschiedliche Aktionen, die Sie über WMI ausführen können. Einige der üblichen Aktionen werden hier durchlaufen.

### <a name="determining-dhcp-enabled-adapters"></a>Ermitteln der DHCP-fähigen Netzwerkkarten

Um die DHCP-fähigen Netzwerkkarten auf einem Computer zu ermitteln, verwenden Sie den folgenden Befehl:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

Wenn Sie Netzwerkkarten mit IP-Konfigurationsproblemen ausschließen möchten, können Sie so vorgehen, dass Sie nur IP-fähige Netzwerkkarten abrufen:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a>Abrufen von DHCP-Eigenschaften

Da DHCP-bezogene Eigenschaften für einen Adapter grundsätzlich mit `DHCP` beginnen, können Sie den Property-Parameter von `Format-Table` verwenden, um ausschließlich diese Eigenschaften anzuzeigen:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Aktivieren von DHCP auf jeder Netzwerkkarte

Wenn Sie DHCP auf allen Netzwerkkarten aktivieren möchten, verwenden Sie den folgenden Befehl:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

Sie können die **Filter**-Anweisung `IPEnabled=$true and DHCPEnabled=$false` verwenden, um eine DHCP-Aktivierung zu vermeiden, wenn DHCP bereits aktiviert ist. Es wird jedoch kein Fehler verursacht, wenn dieser Schritt ausgelassen wird.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Freigeben und Erneuern von DHCP-Leases auf bestimmten Netzwerkkarten

Die **Win32_NetworkAdapterConfiguration**-Klasse hat die Methoden **ReleaseDHCPLease** und **RenewDHCPLease**. Beide werden auf die gleiche Weise verwendet. Üblicherweise verwenden Sie diese Methoden, wenn Sie nur Adressen für eine Netzwerkkarte in einem bestimmten Subnetz freigeben oder erneuern müssen. Die einfachste Möglichkeit zum Filtern von Netzwerkkarten in einem Subnetz besteht darin, nur die Netzwerkkartenkonfigurationen auswählen, die das Gateway für das Subnetz verwenden. Beispielsweise gibt der folgende Befehl alle DHCP-Leases auf Netzwerkkarten des lokalen Computers frei, die DHCP-Leases von 192.168.1.254 erhalten:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Die einzige Änderung für die Erneuerung einer DHCP-Lease ist die, dass die **RenewDHCPLease**-Methode anstelle der **ReleaseDHCPLease**-Methode verwendet wird:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Wenn Sie diese Methoden auf einem Remotecomputer verwenden, sollten Sie daran denken, dass der Zugriff auf das Remotesystem verloren gehen kann, wenn die Verbindung mit dem System über die Netzwerkkarte mit der freigegebenen oder erneuerten Lease besteht.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Freigeben und Erneuern von DHCP-Leases auf allen Netzwerkkarten

Sie können globale DHCP-Adressfreigaben oder -erneuerungen auf allen Netzwerkkarten ausführen, indem Sie die **Win32_NetworkAdapterConfiguration**-Methoden **ReleaseDHCPLeaseAll** und **RenewDHCPLeaseAll** verwenden.
Allerdings muss der Befehl auf die WMI-Klasse statt auf eine bestimmte Netzwerkkarte angewendet werden, weil globales Freigeben und Erneuern von Leases für die Klasse, nicht für eine bestimmte Netzwerkkarte ausgeführt wird.

Sie können einen Verweis auf eine WMI-Klasse anstelle von Klasseninstanzen abrufen, indem Sie alle WMI-Klassen auflisten und dann nur die gewünschte Klasse nach Name auswählen. Beispielsweise gibt der folgende Befehl die **Win32_NetworkAdapterConfiguration**-Klasse zurück:

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Sie können den gesamten Befehl als die Klasse behandeln und dann die **ReleaseDHCPAdapterLease**-Methode für ihn aufrufen. Im folgenden Befehl wird PowerShell durch die Klammern um die Pipelineelemente `Get-CimInstance` und `Where-Object` angewiesen, diese zuerst auszuwerten:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

Sie können das gleiche Befehlsformat verwenden, um die **RenewDHCPLeaseAll**-Methode aufzurufen:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Erstellen einer Netzwerkfreigabe

Um eine Netzwerkfreigabe zu erstellen, verwenden Sie die Methode **Create** von **Win32_Share**:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

Sie können die Freigabe auch erstellen, indem Sie `net share` in PowerShell unter Windows verwenden:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Entfernen einer Netzwerkfreigabe

Sie können eine Netzwerkfreigabe mit **Win32_Share** entfernen, aber der Vorgang unterscheidet sich etwas vom Erstellen einer Freigabe, weil Sie die bestimmte zu entfernende Freigabe anstelle der **Win32_Share**-Klasse abrufen müssen. Mit der folgenden Anweisung wird die Freigabe **TempShare** gelöscht:

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

Unter Windows funktioniert `net share` ebenfalls:

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Verbinden eines für Windows verfügbaren Netzlaufwerks

Das Cmdlet `New-PSDrive` erstellt ein PowerShell-Laufwerk, aber auf diese Weise erstellte Laufwerke sind nur für PowerShell verfügbar. Um ein neues Netzlaufwerk zu erstellen, können Sie das **WScript.Network**-COM-Objekt verwenden. Durch den folgenden Befehl wird die Freigabe `\\FPS01\users` dem lokalen Laufwerk `B:` zugeordnet:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

Unter Windows funktioniert der Befehl `net use` ebenfalls:

```powershell
net use B: \\FPS01\users
```

Laufwerke, die entweder mit **WScript.Network** oder `net use` zugeordnet wurden, sind sofort für PowerShell verfügbar.
