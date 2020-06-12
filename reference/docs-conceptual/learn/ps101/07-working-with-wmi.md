---
title: Arbeiten mit WMI
description: PowerShell verfügt seit jeher über Cmdlets für die Arbeit mit WMI.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438291"
---
# <a name="chapter-7---working-with-wmi"></a>Kapitel 7: Arbeiten mit WMI

## <a name="wmi-and-cim"></a>WMI und CIM

PowerShell wird standardmäßig mit Cmdlets für die Arbeit mit anderen Technologien wie Windows-Verwaltungsinstrumentation (WMI) ausgeliefert. Es gibt mehrere native WMI-Cmdlets, die in PowerShell vorhanden sind, ohne dass zusätzliche Software oder Module installiert werden müssen.

PowerShell verfügt seit jeher über Cmdlets für die Arbeit mit WMI. `Get-Command` kann verwendet werden, um zu ermitteln, welche WMI-Cmdlets in PowerShell vorhanden sind. Die folgenden Ergebnisse stammen von meinem Computer in der Windows 10-Laborumgebung, auf dem PowerShell, Version 5.1., ausgeführt wird. Ihre Ergebnisse können je nach ausgeführter PowerShell-Version variieren.

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

CIM-Cmdlets (Common Information Model) wurden in PowerShell-Version 3.0 eingeführt. Die CIM-Cmdlets sind so konzipiert, dass sie sowohl auf Windows- als auch auf Nicht-Windows-Computern verwendet werden können. Die WMI-Cmdlets werden nicht mehr unterstützt, weshalb ich empfehle, die CIM-Cmdlets anstelle der älteren WMI-Cmdlets zu verwenden.

Die CIM-Cmdlets sind alle in einem Modul enthalten. Verwenden Sie zum Abrufen einer Liste der CIM-Cmdlets `Get-Command` mit dem Parameter **Module**, wie im folgenden Beispiel gezeigt.

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

Die CIM-Cmdlets ermöglichen es Ihnen weiterhin, mit WMI zu arbeiten. Lassen Sie sich also nicht verwirren, wenn jemand die Aussage trifft: „Wenn ich WMI mit den CIM-Cmdlets von PowerShell abfrage...“.

Wie bereits erwähnt, ist WMI eine gesonderte Technologie von PowerShell, und Sie verwenden lediglich die CIM-Cmdlets für den Zugriff auf WMI. Möglicherweise finden Sie ein altes VBScript, das die WMI-Abfragesprache (WQL) zum Abfragen von WMI verwendet, wie im folgenden Beispiel gezeigt.

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

Sie können die WQL-Abfrage aus diesem VBScript nehmen und ohne Änderungen mit dem Cmdlet `Get-CimInstance` verwenden.

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Dies ist allerdings nicht das Standardverfahren, mit dem ich WMI in PowerShell abfrage. Aber es funktioniert und gestattet Ihnen, vorhandene VBScripts auf einfache Weise zu PowerShell zu migrieren. Wenn ich mit dem Schreiben eines Einzeilers zum Abfragen von WMI beginne, verwende ich die folgende Syntax.

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

Wenn ich nur die Seriennummer benötige, kann ich die Ausgabe per Pipeline an `Select-Object` weiterleiten und nur die Eigenschaft **SerialNumber** angeben.

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Standardmäßig gibt es mehrere Eigenschaften, die hinter den Kulissen abgerufen werden, die nie verwendet werden.
Dies mag keine große Rolle spielen, wenn Sie WMI auf dem lokalen Computer abfragen. Sobald Sie aber mit dem Abfragen von Remotecomputern beginnen, handelt es sich dabei nicht nur um zusätzliche Verarbeitungszeit, um diese Informationen zurückzugeben, sondern auch um zusätzliche unnötige Informationen, die über das Netzwerk abgerufen werden müssen. `Get-CimInstance` verfügt über einen Parameter **Eigenschaft**, der die Informationen einschränkt, die abgerufen werden. Dadurch wird die WMI-Abfrage effizienter.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

Die vorherigen Ergebnisse haben ein Objekt zurückgegeben. Um eine einfache Zeichenfolge zurückzugeben, verwenden Sie den Parameter **ExpandProperty**.

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

Sie können auch den Strich-Stil der Syntax verwenden, um eine einfache Zeichenfolge zurückzugeben. Hierdurch entfällt die Notwendigkeit einer Weitergabe per Pipeline an `Select-Object`.

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a>Abfragen von Remotecomputern mit den CIM-Cmdlets

Ich führe PowerShell immer noch als lokaler Administrator aus, der ein Domänenbenutzer ist. Wenn ich versuche, Informationen von einem Remotecomputer mithilfe des Cmdlets `Get-CimInstance` abzufragen, erhalte ich die Fehlermeldung „Zugriff verweigert“.

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

Viele Leute haben Sicherheitsbedenken, wenn es um PowerShell geht, aber die Wahrheit ist, dass Sie in PowerShell exakt dieselben Berechtigungen wie in der grafischen Benutzeroberfläche haben. Nicht mehr und nicht weniger. Das Problem im vorherigen Beispiel besteht darin, dass der Benutzer, der PowerShell ausführt, nicht über die Berechtigung zum Abfragen von WMI-Informationen vom Server „DC01“ verfügt. Ich könnte PowerShell als Domänenadministrator neu starten, da `Get-CimInstance` keinen Parameter **Credential** besitzt. Aber glauben Sie mir, dass das keine gute Idee ist, weil dann alles, was ich von PowerShell aus ausführe, als Domänenadministrator ausgeführt würde. Dies könnte hinsichtlich der Sicherheit, je nach Situation, gefährlich sein.

Unter Anwendung des Prinzips der geringsten Rechte führe ich pro Befehl eine Erhöhung der Rechte zum Domänenadministrator durch, indem ich den Parameter **Credential** verwenden, wenn ein Befehl diesen besitzt. `Get-CimInstance` besitzt keinen Parameter **Credential**, sodass die Lösung in diesem Szenario darin besteht, zuerst eine **CimSession** zu erstellen. Dann verwende ich die **CimSession-** anstelle eines Computernamens, um WMI auf dem Remotecomputer abzufragen.

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

Die CIM-Sitzung wurde in einer Variablen namens `$CimSession` gespeichert. Beachten Sie, dass ich auch das Cmdlet `Get-Credential` in Klammern angegeben habe, damit es zuerst ausgeführt wird und mich vor der Erstellung der neuen Sitzung zur Eingabe von alternativen Anmeldeinformationen auffordert. Später in diesem Kapitel zeige ich Ihnen noch eine andere, effizientere Methode, um alternative Anmeldeinformationen anzugeben. Aber es ist wichtig, dieses grundlegende Konzept zu verstehen, bevor es komplizierter wird.

Die im vorherigen Beispiel erstellte CIM-Sitzung kann nun mit dem Cmdlet `Get-CimInstance` verwendet werden, um die BIOS-Informationen von WMI auf dem Remotecomputer abzufragen.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

Die Verwendung von CIM-Sitzungen bietet mehrere zusätzliche Vorteile gegenüber dem reinen Angeben eines Computernamens. Wenn Sie mehrere Abfragen auf demselben Computer ausführen, ist die Verwendung einer CIM-Sitzung effizienter als die Verwendung des Computernamens bei jeder einzelnen Abfrage. Beim Erstellen einer CIM-Sitzung wird die Verbindung nur einmal eingerichtet.
Anschließend verwenden mehrere Abfragen dieselbe Sitzung, um Informationen abzurufen. Die Verwendung des Computernamens erfordert, dass die Cmdlets die Verbindung bei jeder einzelnen Abfrage herstellen und wieder beenden.

Das Cmdlet `Get-CimInstance` verwendet standardmäßig das WSMan-Protokoll, was bedeutet, dass der Remotecomputer PowerShell, Version 3.0 oder höher, benötigt, um eine Verbindung herzustellen. Tatsächlich ist nicht die PowerShell-Version relevant, sondern die Stapelversion. Die Stapelversion lässt sich mit dem Cmdlet `Test-WSMan` bestimmen.
Es muss Version 3.0 sein. Das ist die Version, die Sie bei PowerShell, Version 3.0 und höher, vorfinden.

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

Die älteren WMI-Cmdlets verwenden das DCOM-Protokoll, das mit älteren Versionen von Windows kompatibel ist. DCOM wird aber in der Regel von der Firewall auf neueren Versionen von Windows blockiert. Mit dem Cmdlet `New-CimSessionOption` können Sie eine DCOM-Protokollverbindung für die Verwendung mit `New-CimSession` erstellen. Dies gestattet, das Cmdlet `Get-CimInstance` für die Kommunikation mit Versionen von Windows zu verwenden, die älter sind als Windows Server 2000. Dies bedeutet auch, dass PowerShell auf dem Remotecomputer nicht erforderlich ist, wenn das Cmdlet `Get-CimInstance` mit einer CimSession verwendet wird, die für die Verwendung des DCOM-Protokolls konfiguriert ist.

Erstellen Sie die DCOM-Protokolloption mithilfe des Cmdlets `New-CimSessionOption`, und speichern Sie sie in einer Variablen.

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

Aus Gründen der Effizienz können Sie Ihre Domänenadministrator- oder erhöhten Anmeldeinformationen in einer Variablen speichern, damit Sie sie nicht bei jedem Befehl erneut eingeben müssen.

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

Ich verfüge über einen Server namens „SQL03“, auf dem Windows Server 2008 (nicht R2) ausgeführt wird. Dabei handelt es sich um das neueste Windows Server-Betriebssystem, auf dem PowerShell nicht standardmäßig installiert ist.

Erstellen Sie mithilfe des DCOM-Protokolls eine **CimSession** zu SQL03.

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

Beachten Sie im vorherigen Befehl, dass ich diesmal die Variable namens `$Cred` als Wert für den Parameter **Credential** angegeben habe, anstatt sie erneut manuell eingeben zu müssen.

Die Ausgabe der Abfrage ist unabhängig vom verwendeten, zugrunde liegenden Protokoll identisch.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

Das Cmdlet `Get-CimSession` wird verwendet, um zu sehen, welche **CimSessions** derzeit verbunden sind und welche Protokolle diese verwenden.

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

Rufen Sie die beiden zuvor erstellten **CimSessions** ab, und speichern Sie sie in einer Variablen mit dem Namen `$CimSession`.

```powershell
$CimSession = Get-CimSession
```

Fragen Sie beide Computer mit jeweils einem Befehl ab, mit einem, der das WSMan-Protokoll verwendet, und einem, der DCOM verwendet.

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

Ich habe zahlreiche Blogartikel zu den WMI- und CIM-Cmdlets verfasst. Einer der nützlichsten behandelt eine Funktion, die ich erstellt habe, um automatisch festzustellen, ob WSMan oder DCOM verwendet werden sollte, und um die CIM-Sitzung automatisch einzurichten, ohne manuell herausfinden zu müssen, welches. Dieser Blogartikel trägt den Titel [PowerShell-Funktion zum Erstellen von CimSessions für Remotecomputer mit Fallback auf DCOM][].

Wenn Sie mit den CIM-Sitzungen fertig sind, sollten Sie sie mit dem Cmdlet `Remove-CimSession` entfernen. Um alle CIM-Sitzungen zu entfernen, leiten Sie einfach `Get-CimSession` per Pipeline an `Remove-CimSession` weiter.

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie erfahren, wie Sie PowerShell verwenden, um sowohl auf lokalen als auch auf Remotecomputern mit WMI zu arbeiten. Sie haben ferner erfahren, wie Sie die CIM-Cmdlets verwenden, um mit Remotecomputern sowohl mit dem WSMan- als auch mit dem DCOM-Protokoll zu arbeiten.

## <a name="review"></a>Überprüfung

1. Worin besteht der Unterschied zwischen WMI- und CIM-Cmdlets?
1. Welches Protokoll verwendet das `Get-CimInstance`-Cmdlet standardmäßig?
1. Was sind einige der Vorteile bei der Verwendung einer CIM-Sitzung, anstatt einen Computernamen mit `Get-CimInstance` anzugeben?
1. Wie geben Sie ein alternatives Protokoll an, das nicht das Standardprotokoll für die Verwendung mit `Get-CimInstance` ist?
1. Wie schließen oder entfernen Sie CIM-Sitzungen?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [about_WMI][]
- [about_WMI_Cmdlets][]
- [about_WQL][]
- [CimCmdlets-Modul][]
- [Video: Verwenden von CIM-Cmdlets und CIM-Sitzungen][]

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets-Modul]: /powershell/module/cimcmdlets/
[Video: Verwenden von CIM-Cmdlets und CIM-Sitzungen]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[PowerShell-Funktion zum Erstellen von CimSessions für Remotecomputer mit Fallback auf DCOM]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
