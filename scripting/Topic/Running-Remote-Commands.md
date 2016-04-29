---
title: Ausführen von Remotebefehlen
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---
# Ausführen von Remotebefehlen
Mit einem einzigen Windows PowerShell-Befehl können Sie Befehle auf einem oder Hunderten von Computern ausführen. Windows PowerShell unterstützt das Remotecomputing mithilfe verschiedener Technologien, unter anderem WMI, RPC und WS-Management.

## Remoting ohne Konfiguration
Viele Windows PowerShell-Cmdlets verfügen über einen „ComputerName“-Parameter, mit dem Sie Daten auf einem oder mehreren Remotecomputern sammeln und Einstellungsänderungen vornehmen können. Sie verwenden eine Vielzahl von Kommunikationstechnologien und viele arbeiten ohne besondere Konfiguration unter allen Windows-Betriebssystemen, die Windows PowerShell unterstützen.

Zu diesem Cmdlets zählen:

-   [Restart-Computer](assetId:///bd52bcf6-80ee-4866-9320-04ee1d1dca4a)

-   [Test-Connection](assetId:///87d293e5-10e2-489b-b0a9-922d77c05f3f)

-   [Clear-EventLog](assetId:///05d0de31-3c9d-4cd6-8e1a-dac19835464c)

-   [Get-EventLog [m2]](assetId:///a4372a60-b7d9-4b1c-a268-aa5240300141)

-   [Get-Hotfix](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)

-   [Get-Service [m2]](assetId:///0a09cb22-0a1c-4a79-9851-4e53075f9cf6)

-   [Set-Service [m2]](assetId:///b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

-   [Get-WinEvent](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-WmiObject [m2]](assetId:///a4c499fa-deec-4c4b-b3fb-6e195d48a396)

In der Regel haben Cmdlets, die Remoting ohne besondere Konfiguration unterstützen, einen „ComputerName“-Parameter und keinen „Session“-Parameter. Um diese Cmdlets in Ihrer Sitzung zu finden, geben Sie Folgendes ein:

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Windows PowerShell-Remoting
Mit dem Windows PowerShell-Remoting, bei dem das WS-Verwaltungsprotokoll verwendet wird, können Sie jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen. Sie können dauerhafte Verbindungen herstellen, interaktive 1:1-Sitzungen 1:1 starten und Skripts auf mehreren Computern ausführen.

Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein. Weitere Informationen und Anweisungen hierzu finden Sie unter [about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd).

Nachdem Sie Windows PowerShell-Remoting konfiguriert haben, stehen Ihnen viele Remotingstrategien zur Verfügung. Im weiteren Verlauf dieses Dokuments sind einige davon aufgelistet. Weitere Informationen finden Sie unter [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970) und [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42).

### Starten einer interaktiven Sitzung
Um eine interaktive Sitzung mit einem einzelnen Remotecomputer zu starten, verwenden Sie das Cmdlet [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c). Um beispielsweise eine interaktive Sitzung mit dem Remotecomputer „Server01“ zu starten, geben Sie Folgendes ein:

```
enter-pssession Server01
```

Die Eingabeaufforderung ändert sich, und es wird der Name des Computers angezeigt, mit dem Sie verbunden sind. Von nun an werden alle Befehle, die Sie an der Eingabeaufforderung eingeben, auf dem Remotecomputer ausgeführt, und die Ergebnisse werden auf dem lokalen Computer angezeigt.

Um die interaktive Sitzung zu beenden, geben Sie Folgendes ein:

```
exit-pssession
```

Weitere Informationen über die Cmdlets „Enter-PSSession“ und „Exit-PSSession“ Sie unter [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) und [Exit-PSSession](assetId:///b6daa1ce-48a5-41a3-ac4b-b64dbe03465d).

### Ausführen eines Remotebefehls
Zum Ausführen eines Befehls auf einem oder mehreren Remotecomputern verwenden Sie das Cmdlet [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462). Um beispielsweise einen [Get-UICulture [m2]](assetId:///99175c2e-e856-4208-970e-3dd2f6bac5b8)-Befehl auf den Remotecomputern „Server01“ und „Server02“ auszuführen, geben Sie Folgendes ein:

```
invoke-command -computername Server01, Server02 {get-UICulture}
```

Die Ausgabe wird an den Computer zurückgegeben.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Ausführen eines Skripts
Zum Ausführen eines Skripts auf einem oder mehreren Remotecomputern verwenden Sie den Parameter „FilePath“ des Cmdlets „Invoke-Command“. Das Skript muss sich auf dem lokalen Computer befinden oder für diesen verfügbar sein. Die Ergebnisse werden an den lokalen Computer zurückgegeben.

Der folgende Befehl führt beispielsweise das Skript „DiskCollect.ps1“ auf den Remotecomputern „Server01“ und „Server02“ aus.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Herstellen einer dauerhaften Verbindung
Um eine Reihe verwandter Befehle auszuführen, die Daten gemeinsam nutzen, erstellen Sie eine Sitzung auf dem Remotecomputer, und verwenden Sie dann das Cmdlet „Invoke-Command“ zum Ausführen der Befehle in der Sitzung, die Sie erstellen. Um eine Remotesitzung zu erstellen, verwenden Sie das Cmdlet „New-PSSession“.

Mit dem folgenden Befehl erstellen Sie z. B. eine Remotesitzung auf dem Computer "Server01" und eine weitere Remotesitzung auf dem Computer "Server02". Es speichert die Sitzungsobjekte in der Variablen „$s“.

```
$s = new-pssession -computername Server01, Server02
```

Nachdem die Sitzungen nun hergestellt sind, können Sie jeden beliebigen Befehl in diesen ausführen. Und da die Sitzungen dauerhaft sind, können Sie Daten in einem Befehl sammeln und diese in einem nachfolgenden Befehl verwenden.

Beispielsweise führt der folgende Befehl einen „Get-Hotfix“-Befehl in den Sitzungen in der Variablen „$s“ aus und speichert die Ergebnisse dann in der Variablen „$h“. Die Variable „$h“ wird in jeder der Sitzungen in „$s“ erstellt, ist jedoch in der lokalen Sitzung nicht vorhanden.

```
invoke-command -session $s {$h = get-hotfix}
```

Sie können die Daten in der Variablen „$h“ jetzt in nachfolgenden Befehle verwenden, wie z. B. dem folgenden. Die Ergebnisse werden auf dem lokalen Computer angezeigt.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"
```

### Erweitertes Remoting
Dies sind nur die grundlegenden Möglichkeiten, die die Remoteverwaltung von Windows PowerShell bietet. Mithilfe von Cmdlets, die mit Windows PowerShell installiert werden, können Sie Remotesitzungen sowohl von lokaler Seite als auch von Remoteseite aus einrichten und konfigurieren, angepasste und eingeschränkte Sitzungen erstellen, Benutzern über eine Remotesitzung den Import von Befehlen ermöglichen, die tatsächlich implizit in der Remotesitzung ausgeführt werden, die Sicherheit einer Remotesitzung konfigurieren und vieles mehr.

Um die Remotekonfiguration zu vereinfachen, umfasst Windows PowerShell einen WSMan-Anbieter. Das vom Anbieter erstellte Laufwerk „WSMAN:“ ermöglicht Ihnen, durch eine Hierarchie von Konfigurationseinstellungen auf dem lokalen Computer und den Remotecomputern zu navigieren. Weitere Informationen zum WSMan-Anbieter finden Sie unter [WSMan-Anbieter](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735) und [about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed), oder wenn Sie in der Windows PowerShell-Konsole „get-help wsman“ eingeben.

Weitere Informationen finden Sie unter [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42), [Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25) und [Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d). Hilfe zu Remotingfehlern finden Sie unter [about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317).

## Weitere Informationen
[about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
[about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)
[about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)
[about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)
[about_PSSessions](assetId:///7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
[about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)
[Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
[New-PSSession](assetId:///59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)
[WS-Management-Anbieter](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=Apr16_HO1-->


