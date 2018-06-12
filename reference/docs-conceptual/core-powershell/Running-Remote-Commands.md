---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ausführen von Remotebefehlen
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482878"
---
# <a name="running-remote-commands"></a>Ausführen von Remotebefehlen

Mit einem einzigen Windows PowerShell-Befehl können Sie Befehle auf einem oder Hunderten von Computern ausführen. Windows PowerShell unterstützt das Remotecomputing mithilfe verschiedener Technologien, unter anderem WMI, RPC und WS-Management.

## <a name="remoting-in-powershell-core"></a>Remoting in PowerShell Core

PowerShell Core, die neuere Edition von PowerShell für Windows, macOS und Linux, unterstützt WMI, WS-Verwaltung und SSH-Remoting.
(RPC wird nicht mehr unterstützt.)

Weitere Informationen zur Einrichtung finden Sie in folgenden Artikeln:

* [SSH-Remoting in PowerShell Core][ssh-remoting]
* [WSMan-Remoting in PowerShell Core][wsman-remoting]

## <a name="remoting-without-configuration"></a>Remoting ohne Konfiguration

Viele Windows PowerShell-Cmdlets verfügen über einen „ComputerName“-Parameter, mit dessen Hilfe Sie Daten auf einem oder mehreren Remotecomputern sammeln und Einstellungsänderungen vornehmen können. Sie verwenden eine Vielzahl von Kommunikationstechnologien und viele arbeiten ohne besondere Konfiguration unter allen Windows-Betriebssystemen, die Windows PowerShell unterstützen.

Zu diesem Cmdlets zählen:

* [Restart-Computer](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Test-Connection](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Clear-EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-EventLog](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Set-Service](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

In der Regel weisen Cmdlets, die Remoting ohne besondere Konfiguration unterstützen, den „ComputerName“-Parameter und nicht den „Session“-Parameter auf. Um diese Cmdlets in Ihrer Sitzung zu finden, geben Sie Folgendes ein:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell-Remoting

Mit dem Windows PowerShell-Remoting, bei dem das WS-Verwaltungsprotokoll verwendet wird, können Sie jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen. Sie können dauerhafte Verbindungen herstellen, interaktive 1:1-Sitzungen 1:1 starten und Skripts auf mehreren Computern ausführen.

Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein. Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](https://technet.microsoft.com/library/dd315349.aspx).

Nachdem Sie Windows PowerShell-Remoting konfiguriert haben, stehen Ihnen viele Remotingstrategien zur Verfügung. Im weiteren Verlauf dieses Dokuments sind einige davon aufgelistet. Weitere Informationen finden Sie unter [about_Remote](https://technet.microsoft.com/library/dd347744.aspx) und [about_Remote_FAQ](https://technet.microsoft.com/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Starten einer interaktiven Sitzung

Um eine interaktive Sitzung mit einem einzelnen Remotecomputer zu starten, verwenden Sie das Cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).
Um beispielsweise eine interaktive Sitzung mit dem Remotecomputer „Server01“ zu starten, geben Sie Folgendes ein:

```powershell
Enter-PSSession Server01
```

Die Eingabeaufforderung ändert sich, und es wird der Name des Computers angezeigt, mit dem Sie verbunden sind. Von nun an werden alle Befehle, die Sie an der Eingabeaufforderung eingeben, auf dem Remotecomputer ausgeführt, und die Ergebnisse werden auf dem lokalen Computer angezeigt.

Um die interaktive Sitzung zu beenden, geben Sie Folgendes ein:

```powershell
Exit-PSSession
```

Weitere Informationen über die Cmdlets „Enter-PSSession“ und „Exit-PSSession“ Sie unter [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) und [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Ausführen eines Remotebefehls

Zum Ausführen eines Befehls auf einem oder mehreren Remotecomputern verwenden Sie das Cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).
Um beispielsweise einen [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806)-Befehl auf den Remotecomputern „Server01“ und „Server02“ auszuführen, geben Sie Folgendes ein:

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

Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Ausführen eines Skripts

Zum Ausführen eines Skripts auf einem oder mehreren Remotecomputern verwenden Sie den Parameter „FilePath“ des Cmdlets „Invoke-Command“. Das Skript muss sich auf dem lokalen Computer befinden oder für diesen verfügbar sein. Die Ergebnisse werden an den lokalen Computer zurückgegeben.

Der folgende Befehl führt beispielsweise das Skript „DiskCollect.ps1“ auf den Remotecomputern „Server01“ und „Server02“ aus.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Herstellen einer dauerhaften Verbindung

Um eine Reihe verwandter Befehle auszuführen, die Daten gemeinsam nutzen, erstellen Sie eine Sitzung auf dem Remotecomputer, und verwenden Sie dann das Cmdlet „Invoke-Command“ zum Ausführen der Befehle in der Sitzung, die Sie erstellen. Um eine Remotesitzung zu erstellen, verwenden Sie das Cmdlet „New-PSSession“.

Mit dem folgenden Befehl erstellen Sie z. B. eine Remotesitzung auf dem Computer "Server01" und eine weitere Remotesitzung auf dem Computer "Server02". Es speichert die Sitzungsobjekte in der Variablen „$s“.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Nachdem die Sitzungen nun hergestellt sind, können Sie jeden beliebigen Befehl in diesen ausführen. Und da die Sitzungen dauerhaft sind, können Sie Daten in einem Befehl sammeln und diese in einem nachfolgenden Befehl verwenden.

Beispielsweise führt der folgende Befehl einen „Get-HotFix“-Befehl in den Sitzungen in der Variablen „$s“ aus und speichert die Ergebnisse dann in der Variablen „$h“. Die Variable „$h“ wird in jeder der Sitzungen in „$s“ erstellt, ist jedoch in der lokalen Sitzung nicht vorhanden.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Sie können die Daten in der Variablen „$h“ jetzt in nachfolgenden Befehle verwenden, wie z. B. dem folgenden. Die Ergebnisse werden auf dem lokalen Computer angezeigt.

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Erweitertes Remoting

Dies sind nur die grundlegenden Möglichkeiten, die die Remoteverwaltung von Windows PowerShell bietet. Mithilfe von Cmdlets, die mit Windows PowerShell installiert werden, können Sie Remotesitzungen sowohl von lokaler Seite als auch von Remoteseite aus einrichten und konfigurieren, angepasste und eingeschränkte Sitzungen erstellen, Benutzern über eine Remotesitzung den Import von Befehlen ermöglichen, die tatsächlich implizit in der Remotesitzung ausgeführt werden, die Sicherheit einer Remotesitzung konfigurieren und vieles mehr.

Um die Remotekonfiguration zu vereinfachen, umfasst Windows PowerShell einen WSMan-Anbieter. Das vom Anbieter erstellte Laufwerk „WSMAN:“ ermöglicht Ihnen, durch eine Hierarchie von Konfigurationseinstellungen auf dem lokalen Computer und den Remotecomputern zu navigieren.
Weitere Informationen zum WSMan-Anbieter finden Sie unter [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) und [About_WS-Management_Cmdlets](https://technet.microsoft.com/library/dd819481.aspx), oder indem Sie in der Windows PowerShell-Konsole „Get-Help wsman“ eingeben.

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
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan-Anbieter](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md