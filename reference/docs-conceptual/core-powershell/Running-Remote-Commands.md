---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Ausführen von Remotebefehlen
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133124"
---
# <a name="running-remote-commands"></a>Ausführen von Remotebefehlen

Mit einem einzigen PowerShell-Befehl können Sie Befehle auf einem oder Hunderten von Computern ausführen. Windows PowerShell unterstützt das Remotecomputing mithilfe verschiedener Technologien, unter anderem WMI, RPC und WS-Management.

PowerShell Core unterstützt WMI, WS-Management und SSH-Remoting. RPC wird nicht mehr unterstützt.

Weitere Informationen zu Remoting in PowerShell Core finden Sie in den folgenden Artikeln:

- [SSH-Remoting in PowerShell Core][ssh-remoting]
- [WSMan-Remoting in PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Windows PowerShell-Remoting ohne Konfiguration

Viele Windows PowerShell-Cmdlets verfügen über einen „ComputerName“-Parameter, mit dessen Hilfe Sie Daten auf einem oder mehreren Remotecomputern sammeln und Einstellungsänderungen vornehmen können. Diese Cmdlets verwenden unterschiedliche Kommunikationsprotokolle und funktionieren auf allen Windows-Betriebssystemen ohne besondere Konfiguration.

Zu diesem Cmdlets zählen:

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

In der Regel weisen Cmdlets, die Remoting ohne besondere Konfiguration unterstützen, den „ComputerName“-Parameter und nicht den „Session“-Parameter auf. Um diese Cmdlets in Ihrer Sitzung zu finden, geben Sie Folgendes ein:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell-Remoting

Über das WS-Management-Protokoll können Sie mit Windows PowerShell-Remoting jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen. Sie können dauerhafte Verbindungen herstellen, interaktive Sitzungen starten und Skripts auf Remotecomputern ausführen.

Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein.
Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Nachdem Sie Windows PowerShell-Remoting konfiguriert haben, stehen Ihnen viele Remotingstrategien zur Verfügung.
In diesem Artikel werden nur einige davon aufgeführt. Weitere Informationen finden Sie unter [Informationen zu Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Starten einer interaktiven Sitzung

Um eine interaktive Sitzung mit einem einzelnen Remotecomputer zu starten, verwenden Sie das Cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).
Um beispielsweise eine interaktive Sitzung mit dem Remotecomputer „Server01“ zu starten, geben Sie Folgendes ein:

```powershell
Enter-PSSession Server01
```

Die Eingabeaufforderung ändert sich, und es wird der Name des Remotecomputers angezeigt. Alle Befehle, die Sie an der Eingabeaufforderung eingeben, werden auf dem Remotecomputer ausgeführt, und die Ergebnisse werden auf dem lokalen Computer angezeigt.

Um die interaktive Sitzung zu beenden, geben Sie Folgendes ein:

```powershell
Exit-PSSession
```

Weitere Informationen über die Cmdlets „Enter-PSSession“ und „Exit-PSSession“ finden Sie unter:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Ausführen eines Remotebefehls

Zum Ausführen eines Befehls auf einem oder mehreren Computern verwenden Sie das Cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command). Um beispielsweise einen [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture)-Befehl auf den Remotecomputern „Server01“ und „Server02“ auszuführen, geben Sie Folgendes ein:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

Die Ausgabe wird an den Computer zurückgegeben.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Ausführen eines Skripts

Zum Ausführen eines Skripts auf einem oder mehreren Remotecomputern verwenden Sie den Parameter „FilePath“ des Cmdlets `Invoke-Command`. Das Skript muss sich auf dem lokalen Computer befinden oder für diesen verfügbar sein. Die Ergebnisse werden an den lokalen Computer zurückgegeben.

Der folgende Befehl führt beispielsweise das Skript „DiskCollect.ps1“ auf den Remotecomputern „Server01“ und „Server02“ aus.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Herstellen einer dauerhaften Verbindung

Verwenden Sie das Cmdlet `New-PSSession`, um eine permanente Sitzung auf einem Remotecomputer zu erstellen. Das folgende Beispiel erstellt Remotesitzungen auf „Server01“ und „Server02. Die Sitzungsobjekte werden in der Variablen `$s` gespeichert.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nachdem die Sitzungen nun hergestellt sind, können Sie jeden beliebigen Befehl in diesen ausführen. Und da die Sitzungen permanent sind, können Sie Daten von einem Befehl sammeln und in einem anderen Befehl verwenden.

Beispielsweise führt der folgende Befehl einen „Get-HotFix“-Befehl in den Sitzungen in der Variablen „$s“ aus und speichert die Ergebnisse dann in der Variablen „$h“. Die Variable „$h“ wird in jeder der Sitzungen in „$s“ erstellt, ist jedoch in der lokalen Sitzung nicht vorhanden.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Nun können Sie die Daten in der Variablen `$h` in der gleichen Sitzung mit anderen Befehlen verwenden. Die Ergebnisse werden auf dem lokalen Computer angezeigt. Beispiel:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Erweitertes Remoting

Dies sind nur die grundlegenden Möglichkeiten, die die Remoteverwaltung von Windows PowerShell bietet. Mithilfe von Cmdlets, die mit Windows PowerShell installiert werden, können Sie Remotesitzungen sowohl von lokaler Seite als auch von Remoteseite aus einrichten und konfigurieren, angepasste und eingeschränkte Sitzungen erstellen, Benutzern über eine Remotesitzung den Import von Befehlen ermöglichen, die tatsächlich implizit in der Remotesitzung ausgeführt werden, die Sicherheit einer Remotesitzung konfigurieren und vieles mehr.

Windows PowerShell umfasst einen WSMan-Anbieter. Der Anbieter erstellt ein `WSMAN:`-Laufwerk, dass es Ihnen ermöglicht, durch eine Hierarchie von Konfigurationseinstellungen auf dem lokalen Computer und den Remotecomputern zu navigieren.

Weitere Informationen zum WSMan-Anbieter finden Sie unter [WS-Management-Anbieter](https://technet.microsoft.com/library/dd819476.aspx) und [Informationen zu WS-Management-Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets). Geben Sie alternativ in der Windows PowerShell-Konsole `Get-Help wsman` ein.

Weitere Informationen finden Sie unter:

- [Häufig gestellte Fragen zu Remote](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Hilfe zu Remotingfehlern finden Sie unter [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Weitere Informationen

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan-Anbieter](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md