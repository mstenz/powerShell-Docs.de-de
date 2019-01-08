---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Verwenden von Variablen, um Objekte zu speichern
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401370"
---
# <a name="using-variables-to-store-objects"></a>Verwenden von Variablen zum Speichern von Objekten

PowerShell arbeitet mit Objekten. PowerShell ermöglicht es Ihnen, benannte Objekt zu erstellen, sogenannte Variablen.
Namen von Variablen können es sich um den Unterstrich enthalten und alle alphanumerischen Zeichen enthalten. Bei Verwendung in PowerShell wird eine Variable immer mit dem Zeichen \$, gefolgt von einem Variablennamen angegeben.

## <a name="creating-a-variable"></a>Erstellen einer Variablen

Sie können eine Variablen erstellen, indem Sie einen zulässigen Variablennamen eingeben:

```
PS> $loc
PS>
```

Dieses Beispiel gibt kein Ergebnis zurück, weil `$loc` keinen Wert umfasst. Sie können im selben Schritt eine Variable erstellen und ihr einen Wert zuweisen. PowerShell kann die Variable nur erstellen, wenn sie nicht vorhanden ist.
Andernfalls wird der angegebene Wert der vorhandenen Variablen zugewiesen. Im folgenden Beispiel wird der aktuelle Standort in der Variablen `$loc` gespeichert:

```powershell
$loc = Get-Location
```

PowerShell zeigt keine Ausgabe an, wenn Sie diesen Befehl eingeben. PowerShell sendet die Ausgabe von „Get-Location“ an `$loc`. In PowerShell werden Daten, die nicht zugewiesen oder umgeleitet werden, an den Bildschirm gesendet. Durch Eingabe von `$loc` wird Ihnen der aktuelle Standort angezeigt:

```
PS> $loc

Path
----
C:\temp
```

Sie können `Get-Member` verwenden, um Informationen über die Inhalte der Variablen anzuzeigen. `Get-Member` zeigt Ihnen, dass es sich bei `$loc` um ein **PathInfo**-Objekt handelt, ebenso wie die Ausgabe von `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Bearbeiten von Variablen

PowerShell stellt mehrere Befehle bereit, mit denen Variablen verwaltet werden können. Eine vollständige Liste in einem lesbaren Format erhalten Sie, wenn Sie Folgendes eingeben:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell erstellt außerdem verschiedene systemdefinierte Variablen. Mit dem Cmdlet `Remove-Variable` können Sie Variablen aus der aktuellen Sitzung löschen, die nicht von PowerShell kontrolliert werden. Geben Sie den folgenden Befehl ein, um alle Variablen zu löschen:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Nach dem Ausführen des vorstehenden Befehls zeigt das Cmdlet `Get-Variable` die PowerShell-Systemvariablen an.

PowerShell erstellt außerdem ein Laufwerk „variable“. Verwenden Sie das folgende Beispiel, um alle PowerShell-Variablen mit dem Laufwerk „variable“ anzuzeigen:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Verwenden von Cmd.exe-Variablen

PowerShell kann die gleichen Umgebungsvariablen verwenden, die jedem Windows-Prozess zur Verfügung stehen, **cmd.exe** eingeschlossen. Diese Variablen werden über ein Laufwerk namens `env:` verfügbar gemacht. Sie können diese Variablen anzeigen, indem Sie den folgenden Befehl eingeben:

```powershell
Get-ChildItem env:
```

Die standardmäßigen `*-Variable`-Cmdlets sind nicht auf die Arbeit mit Umgebungsvariablen ausgelegt. Auf Umgebungsvariablen wird über das Laufwerkpräfix `env:` zugegriffen. Beispielsweise enthält die Variable **%SystemRoot%** in **cmd.exe** den Stammverzeichnisnamen des Betriebssystems. In PowerShell verwenden Sie `$env:SystemRoot`, um auf denselben Wert zuzugreifen.

```
PS> $env:SystemRoot
C:\WINDOWS
```

Sie können auch Umgebungsvariablen in PowerShell erstellen und ändern. Umgebungsvariablen in PowerShell unterliegen denselben Regeln für Umgebungsvariablen, die an beliebiger anderer Stelle im Betriebssystem verwendet werden. Durch das folgende Beispiel wird eine neue Umgebungsvariable erstellt:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Wenngleich dies nicht erforderlich ist, ist es gängige Praxis, für Namen von Umgebungsvariablen ausschließlich Großbuchstaben zu verwenden.
