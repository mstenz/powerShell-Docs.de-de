---
title: Neuigkeiten in PowerShell Core 6.1
description: Neue Funktionen und Änderungen in PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086105"
---
# <a name="whats-new-in-powershell-core-61"></a>Neuigkeiten in PowerShell Core 6.1

Im Folgenden finden Sie eine Auswahl der wichtigsten Funktionen und Änderungen, die in PowerShell Core 6.1 eingeführt wurden.

Außerdem wurden viele Fehler behoben und **unzählige Verbesserungen** vorgenommen, die PowerShell schneller und stabiler machen, aber vielleicht weniger aufregend klingen.
Eine vollständige Liste der Änderungen finden Sie unter [Changelog (Änderungsprotokoll)](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) auf GitHub.

Ein großer Dank geht an alle [Mitwirkende aus der Community](https://github.com/PowerShell/PowerShell/graphs/contributors), die dieses Release überhaupt möglich gemacht haben, und von denen weiter unten nur eine kleine Auswahl genannt wird.

## <a name="net-core-21"></a>.NET Core 2.1

PowerShell Core 6.1 wurde nach der [Veröffentlichung im Mai](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) zu .NET Core 2.1 verschoben, wodurch sich u.a. folgende Verbesserungen für PowerShell ergeben:

- Leistungsverbesserungen (siehe [unten](#performance-improvements))
- Unterstützung von Alpine Linux (Vorschau)
- [Globale Toolunterstützung für .NET](/dotnet/core/tools/global-tools) – Demnächst für PowerShell verfügbar
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Windows Compatibility Pack für .NET Core

Im Lieferumfang war unter Windows das [Windows Compatibility Pack für .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/) enthalten, das aus verschiedenen Assemblys besteht, mit denen .NET Core unter Windows einige entfernte APIs wieder hinzugefügt werden.

Nun wurde das Windows Compatibility Pack dem Release von PowerShell Core 6.1 hinzugefügt, damit diese APIs für alle Module oder Skripts, die sie verwenden, auch verfügbar sind.

Durch das Windows Compatibility Pack kann PowerShell Core **mehr als 1.900 Cmdlets verwenden, die im Windows Update vom 10. Oktober 2018 und in Windows Server 2019 enthalten sind**.

## <a name="support-for-application-whitelisting"></a>Unterstützung für Anwendungswhitelists

PowerShell Core 6.1 verfügt über dieselbe Unterstützung für Anwendungswhitelists von [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) und [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) wie Windows PowerShell 5.1.
Mit Anwendungswhitelists können Sie detailliert steuern, welche Binärdateien ausgeführt werden dürfen, wenn PowerShell im [eingeschränkten Sprachmodus](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/) verwendet wird.

## <a name="performance-improvements"></a>Leistungsverbesserungen

PowerShell Core 6.0 enthielt bereits einige bedeutende Leistungsverbesserungen.
PowerShell Core 6.1 erhöht nun die Geschwindigkeit bestimmter Vorgänge noch weiter.

So wurde beispielsweise die Geschwindigkeit von `Group-Object` um 66 % gesteigert:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Zeit (in Sek.)   | 25,178                 | 19,653              | 6,641               |
| Beschleunigung (in %) | Nicht zutreffend                    | 21,9 %               | 66,2 %               |

Auf ähnliche Weise wurden auch Sortierszenarios wie etwa das folgende um mehr als 15 % verbessert:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Zeit (in Sek.)   | 12,170                 | 8,493               | 7,08                |
| Beschleunigung (in %) | Nicht zutreffend                    | 30,2 %               | 16,6 %               |

Auch `Import-Csv` wurde nach Regression durch Windows PowerShell deutlich schneller.
Im folgenden Beispiel wird eine CSV-Testdatei mit 26.616 Zeilen und sechs Spalten verwendet:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Zeit (in Sek.)   | 0,441                  | 1,069               | 0,268                  |
| Beschleunigung (in %) | Nicht zutreffend                    | –142,4 %             | 74,9 % (39,2 % im Vergleich zu WPS) |

Letztendlich wurde die Konvertierung von JSON in `PSObject` um mehr als 50 % im Vergleich zu Windows PowerShell beschleunigt.
Im folgenden Beispiel wird eine JSON-Testdatei mit einer Größe von etwa 2 MB verwendet:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Zeit (in Sek.)   | 0,259                  | 0,577               | 0,125                  |
| Beschleunigung (in %) | Nicht zutreffend                    | –122,8 %             | 78,3 % (51,7 % im Vergleich zu WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Überprüfen von `system32` nach kompatiblen Modulen unter Windows

Im Update 1809 für Windows Update 10 und im Update für Windows Server 2019 wurden eine Reihe von integrierten PowerShell-Modulen aktualisiert, um sie als mit PowerShell Core kompatibel zu kennzeichnen.

Beim Starten von PowerShell Core 6.1 wird automatisch `$windir\System32` als Teil der `PSModulePath`-Umgebungsvariable mit einbezogen.
Allerdings werden Module nur dann `Get-Module` und `Import-Module` verfügbar gemacht, wenn `CompatiblePSEdition` als kompatibel mit `Core` gekennzeichnet ist.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Je nach den installierten Rollen und Funktionen werden Ihnen möglicherweise unterschiedliche verfügbare Module angezeigt.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Mit dem Switch-Parameter `-SkipEditionCheck` können Sie dieses Verhalten so überschreiben, dass alle Module angezeigt werden.
Außerdem wurde der Tabellenausgabe eine `PSEdition`-Eigenschaft hinzugefügt.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Weitere Informationen zu diesem Verhalten finden Sie unter [PowerShell RFC 0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Markdown-Cmdlets und -Rendering

Markdown ist eine Standardsprache zum Erstellen von lesbaren Nur-Text-Dokumenten mit grundlegender Formatierung, die in HTML gerendert werden kann.

PowerShell Core 6.1 wurden einige Cmdlets hinzugefügt, mit denen Sie Markdowndokumente in der Konsole konvertieren und rendern können, einschließlich:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Mit `Show-Markdown` wird beispielsweise eine Markdowndatei in der Konsole gerendert:

![Beispiel „Show-Markdown“](./images/markdown_example.png)

Weitere Informationen zur Funktionsweise dieser Cmdlets finden Sie unter [dieser RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Experimentelle Featureflags

Unterstützung für [experimentelle Features][] wurde aktiviert. Auf diese Weise können PowerShell-Entwickler neue Funktionen bereitstellen und Feedback erhalten, bevor der Entwurf abgeschlossen ist. Auf diese Weise vermeiden wir, dass wir bei der Weiterentwicklung des Entwurfs Breaking Changes vornehmen.

Verwenden Sie `Get-ExperimentalFeature`, um eine Liste der verfügbaren experimentellen Features abzurufen. Sie können diese Features mit `Enable-ExperimentalFeature` und `Disable-ExperimentalFeature` aktivieren oder deaktivieren.

Weitere Informationen zu dieser Funktion finden Sie unter [PowerShell RFC 0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Verbesserungen an Web-Cmdlets

Durch die Mithilfe von [@markekraus](https://github.com/markekraus) konnte eine ganze Reihe von Verbesserungen an den Web-Cmdlets [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
und [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod) vorgenommen werden.

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109): Standardcodierung für `application-json`-Antworten auf UTF-8 festgelegt.
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation`-Parameter zum Zulassen von `Content-Type`-Headern, die nicht mit den Standards kompatibel sind.
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form`-Parameter zur Unterstützung von vereinfachter `multipart/form-data`-Unterstützung.
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338): Kompatible Verarbeitung von Beziehungsschlüsseln ohne Beachtung der Groß-/Kleinschreibung.
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447): Hinzufügen des `-Resume`-Parameters zu Web-Cmdlets.

## <a name="remoting-improvements"></a>Remoting-Verbesserungen

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>PowerShell Direct für Container verwendet zunächst PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) ist eine Funktion von PowerShell und Hyper-V, mit der Sie ohne Netzwerkverbindung oder einem anderen Remoteverwaltungsdienst eine Verbindung zu einem virtuellen Hyper-V-Computer oder Container herstellen können.

Bisher wurde die Verbindung von PowerShell Direct mithilfe der integrierten Windows PowerShell-Instanz auf dem Container hergestellt.
Nun versucht PowerShell Direct zunächst, verfügbare `pwsh.exe`-Dateien der `PATH`-Umgebungsvariable dafür zu verwenden.
Ist `pwsh.exe` nicht verfügbar, greift PowerShell Direct wieder auf `powershell.exe` zurück.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` erstellt jetzt separate Remotingendpunkte für Vorschauversionen

`Enable-PSRemoting` erstellt jetzt zwei Konfigurationen für Remotesitzungen:

- Eine für die Hauptversion von PowerShell, Beispiel: `PowerShell.6`. Auf diesen Endpunkt kann nach geringfügigen Aktualisierungen als systemweite Sitzungskonfiguration von PowerShell 6 zurückgegriffen werden.
- Eine versionsspezifische Sitzungskonfiguration, z.B. `PowerShell.6.1.0`.

Dieses Verhalten ist hilfreich, wenn Sie mehrere Versionen von PowerShell 6 auf einem Computer installiert und zugänglich haben möchten.

Darüber hinaus verfügen Vorschauversionen von PowerShell nun über eigene Remotesitzungskonfigurationen, wenn Sie das `Enable-PSRemoting`-Cmdlet ausgeführt haben:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

Die Ausgabe sieht möglicherweise anders aus, wenn Sie nicht zuvor WinRM eingerichtet haben.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

In diesem Fall werden möglicherweise separate PowerShell-Sitzungskonfigurationen für die Vorschau und stabile Builds von PowerShell 6 sowie für jede einzelne Version angezeigt.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>Für SSH unterstützte `user@host:port`-Syntax

SSH-Clients unterstützen in der Regel eine Verbindungszeichenfolge im Format `user@host:port`.
Durch das Hinzufügen von SSH als Protokoll für PowerShell-Remoting ist nun Unterstützung für dieses Format der Verbindungszeichenfolge enthalten:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>MSI-Option zum Hinzufügen eines Explorer-Shell-Kontextmenüs unter Windows

Durch die Mithilfe von [@bergmeister](https://github.com/bergmeister) ist es nun möglich, ein Kontextmenü unter Windows zu aktivieren. Sie können Ihre systemweite Installation von PowerShell 6.1 jetzt aus einem beliebigen Ordner im Windows-Explorer öffnen:

![Shell-Kontextmenü für PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Nützliche Funktionen

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>„Als Administrator ausführen“ in der Sprungliste der Windows-Verknüpfungen

Durch die Mithilfe von [@bergmeister](https://github.com/bergmeister) enthält die Sprungliste der Verknüpfungen von PowerShell Core jetzt die Option „Als Administrator ausführen“:

![„Als Administrator ausführen“ in der Sprungliste von PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>Zurück zum vorherigen Verzeichnis mit `cd -`

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Oder unter Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

`cd` und `cd --` wechseln auch zu `$HOME`.

### `Test-Connection`

Durch die Mithilfe von [@iSazonov](https://github.com/iSazonov) konnte das [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection)-Cmdlet auf PowerShell Core portiert werden.

### <a name="update-help-as-non-admin"></a>`Update-Help` als Nicht-Administrator

Aufgrund der großen Nachfrage muss nun `Update-Help` nicht mehr als Administrator ausgeführt werden.
Über `Update-Help` wird die Hilfe jetzt standardmäßig in einen benutzerdefinierten Ordner gespeichert.

### <a name="new-methodsproperties-on-pscustomobject"></a>Neue Methoden/Eigenschaften für `PSCustomObject`

Durch die Mithilfe von [@iSazonov](https://github.com/iSazonov) konnten `PSCustomObject` neue Methoden und Eigenschaften hinzugefügt werden.
`PSCustomObject` enthält nun eine `Count`/`Length`-Eigenschaften wie andere Objekte.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Diese Vorgehensweise umfasst auch `ForEach`- und `Where`-Methoden, mit denen Sie nach `PSCustomObject`-Elementen ausführen und filtern können:

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Durch die Mithilfe von @SimonWahlin konnte `Where-Object` der `-Not`-Parameter hinzugefügt werden.
Jetzt können Sie ein Objekt in der Pipeline nach dem Nichtvorhandensein einer Eigenschaft oder eines leeren oder NULL-Eigenschaftswerts filtern.

Dieser Befehl gibt z.B. alle Dienste zurück, die über keine definierten abhängigen Dienste verfügen:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>Erstellen eines BOM-freien UTF-8-Dokuments mit `New-ModuleManifest`

Durch den Umstieg auf BOM-freies UTF-8 in PowerShell 6.0 wurde das `New-ModuleManifest`-Cmdlet aktualisiert, und es erstellt nun BOM-freie UTF-8-Dokumente anstatt UTF-16-Dokumente.

### <a name="conversions-from-psmethod-to-delegate"></a>Konvertierungen von PSMethod in einen Delegaten

Durch die Mithilfe von [@powercode](https://github.com/powercode) wird jetzt die Konvertierung von `PSMethod` in einen Delegaten unterstützt.
Dadurch kann nun beispielsweise `PSMethod` `[M]::DoubleStrLen` als Delegatwert an `[M]::AggregateString` übergeben werden:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Weitere Informationen zu dieser Änderung finden Sie unter [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Standardabweichung in `Measure-Object`

Durch die Mithilfe von [@CloudyDino](https://github.com/CloudyDino) wurde `Measure-Object` eine `StandardDeviation`-Eigenschaft hinzugefügt:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Durch die Mithilfe von [@maybe-hello-world](https://github.com/maybe-hello-world) verfügt `Get-PfxCertificate` jetzt über den `Password`-Parameter, der eine `SecureString` erfordert. Dadurch kann er ohne Benutzereingriff verwendet werden:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Entfernen der `more`-Funktion

Bisher enthielt PowerShell unter Windows eine Funktion mit dem Namen `more`, die `more.com` mit einschloss.
Diese Funktion wurde nun entfernt.

Zudem wurde die `help`-Funktion so geändert, dass unter Windows `more.com` verwendet wird bzw. auf anderen Plattformen der unter `$env:PAGER` angegebene Standardpager des Systems.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>Zurückleiten der Benutzer zum aktuellen Arbeitsverzeichnis im Laufwerk mit `cd DriveName:`

Bisher wurden Benutzer zum Standardspeicherort für das Laufwerk geleitet, wenn sie mit `Set-Location` oder `cd` zu einem PowerShell-Laufwerk (PSDrive) zurückkehren wollten.

Durch die Mithilfe von [@mcbobke](https://github.com/mcbobke) werden Benutzer jetzt zum letzten bekannten aktuellen Arbeitsverzeichnis für die jeweilige Sitzung geleitet.

### <a name="windows-powershell-type-accelerators"></a>Typbezeichner für Windows PowerShell

Windows PowerShell enthält nun die folgenden Typbezeichner für ein einfacheres Arbeiten mit den jeweiligen Typen:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

In PowerShell 6 waren diese Typbezeichner noch nicht enthalten und wurden nun in PowerShell 6.1 unter Windows hinzugefügt.

Mit diesen Typen können auf einfache Weise AD- und WMI-Objekte erstellt werden.

Sie können beispielsweise mithilfe von LDAP eine Abfrage ausführen:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Im folgenden Beispiel wird ein CIM-Objekt „Win32_OperatingSystem“ erstellt:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

In diesem Beispiel wird ein ManagementClass-Objekt für die Klasse „Win32_OperatingSystem“ zurückgegeben:

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp`-Alias für alle `-LiteralPath`-Parameter

Durch die Mithilfe von [@kvprasoon](https://github.com/kvprasoon) gibt es nun einen Parameteralias `-lp` für alle integrierten PowerShell-Cmdlets mit einem `-LiteralPath`-Parameter.

## <a name="breaking-changes"></a>Wichtige Änderungen

### <a name="msi-based-installation-paths-on-windows"></a>MSI-basierte Installationspfade unter Windows

Unter Windows wird das MSI-Paket nun im folgenden Pfad installiert:

- `$env:ProgramFiles\PowerShell\6\` für die stabile Installation von 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` für die Installation der Vorschau von 6.x

Mit dieser Änderung wird sichergestellt, dass PowerShell Core durch Microsoft Update aktualisiert/gewartet werden kann.

Weitere Informationen finden Sie unter [PowerShell RFC 0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Deaktivieren von Telemetrie nur mit einer Umgebungsvariable

PowerShell Core sendet beim Starten grundlegende Telemetriedaten an Microsoft. Diese enthalten den Namen und die Version des Betriebssystems sowie die Version von PowerShell. Dadurch wird erkennbar, in welchen Umgebungen PowerShell verwendet wird und welche neuen Funktionen und Problembehebungen Vorrang haben sollten.

Wenn Sie diese Telemetriedaten nicht senden möchten, legen Sie die Umgebungsvariable `POWERSHELL_TELEMETRY_OPTOUT` auf `true`, `yes` oder `1` fest. Die Datei `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` wird zum Deaktivieren der Telemetrie nicht mehr unterstützt.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Standardauthentifizierung über HTTP in PowerShell-Remoting auf Unix-Plattformen nicht zulässig

PowerShell-Remoting auf Unix-Plattformen erfordert nun die Verwendung von NTLM/Negotiate oder HTTPS, um unverschlüsselten Datenverkehr zu verhindern.

Weitere Informationen zu diesen Änderungen finden Sie unter [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>`VisualBasic` als unterstützte Sprache in Add-Type entfernt

Bisher konnte Visual Basic-Code mit dem `Add-Type`-Cmdlet kompiliert werden.
Visual Basic wurde jedoch nur selten mit `Add-Type` verwendet. Daher wurde diese Funktion nun entfernt, um die Größe von PowerShell zu reduzieren.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Verwendung von `CommandTypes.Workflow` und `WorkflowInfoCleaned` bereinigt

Weitere Informationen zu diesen Änderungen finden Sie unter [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).

### <a name="group-object-now-sorts-the-groups"></a>Group-Object sortiert jetzt die Gruppen

Im Rahmen der Leistungsverbesserung gibt `Group-Object` jetzt eine sortierte Auflistung der Gruppen zurück.
Obwohl Sie sich auf die Reihenfolge nicht verlassen sollten, könnte diese Änderung zu einer Teilung führen, wenn Sie die erste Gruppe anzeigen möchten. Wir haben entschieden, dass diese Leistungsverbesserung die Änderung wert wäre, weil sich die Abhängigkeit vom früheren Verhalten nur geringfügig auswirkt.

Weitere Informationen zu dieser Änderung finden Sie unter [Problem #7409](https://github.com/PowerShell/PowerShell/issues/7409).

<!-- URL references -->
[Experimentelle Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
