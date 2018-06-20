---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden von Variablen, um Objekte zu speichern
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953326"
---
# <a name="using-variables-to-store-objects"></a>Verwenden von Variablen, um Objekte zu speichern
PowerShell arbeitet mit Objekten. In PowerShell können Sie Variablen – eigentlich benannte Objekte – erstellen, um Ausgabe zur späteren Verwendung beizubehalten. Wenn Sie mit dem Verwenden von Variablen in anderen Shells vertraut sind, sollten Sie daran denken, dass PowerShell-Variablen keine Texte, sondern Objekte sind.

Variablen werden immer mit dem Anfangszeichen $ angegeben und können jedes alphanumerische Zeichen und den Unterstrich in ihren Namen enthalten.

### <a name="creating-a-variable"></a>Erstellen einer Variablen
Sie können eine Variablen erstellen, indem Sie einen zulässigen Variablennamen eingeben:

```
PS> $loc
PS>
```

Dies gibt kein Ergebnis zurück, weil **$loc** keinen Wert hat. Sie können im selben Schritt eine Variable erstellen und ihr einen Wert zuweisen. PowerShell erstellt die Variable nur, wenn sie nicht vorhanden ist. Andernfalls weist Windows PowerShell der vorhandenen Variablen den angegebenen Wert zu. Um Ihren aktuellen Speicherort in der Variablen **$loc** zu speichern, geben Sie Folgendes ein:

```
$loc = Get-Location
```

Es wird keine Ausgabe angezeigt, wenn Sie diesen Befehl eingeben, weil die Ausgabe an „$loc“ gesendet wird In PowerShell ist angezeigte Ausgabe ein Nebeneffekt der Tatsache, dass Daten, die nicht anderweitig weitergeleitet werden, immer an den Bildschirm gesendet werden. Durch Eingeben von „$loc“ wird Ihr aktueller Speicherort angezeigt:

```
PS> $loc

Path
----
C:\temp
```

Sie können **Get-Member** verwenden, um Informationen über die Inhalte der Variablen anzuzeigen. Wenn Sie „$loc“ in einer Pipeline an „Get-Member“ übergeben, sehen Sie, dass die Variable ein **PathInfo**-Objekt ist, genau wie die Ausgabe von „Get-Location“:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Verwalten von Variablen
PowerShell stellt mehrere Befehle bereit, mit denen Variablen verwaltet werden können. Eine vollständige Liste in einem lesbaren Format erhalten Sie, wenn Sie Folgendes eingeben:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Zusätzlich zu den Variablen, die Sie in Ihrer aktuellen PowerShell-Sitzung erstellen, gibt es mehrere systemdefinierte Variablen. Mit dem Cmdlet **Remove-Variable** können Sie alle Variablen löschen, die nicht von PowerShell kontrolliert werden. Geben Sie den folgenden Befehl ein, um alle Variablen zu löschen:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Daraufhin wird die nachstehende Bestätigungsaufforderung angezeigt.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Wenn Sie nun das Cmdlet **Get-Variable** ausführen, sehen Sie die verbliebenen PowerShell-Variablen. Da es auch ein PowerShell-Laufwerk für Variablen gibt, können Sie alle PowerShell-Variablen ebenfalls durch die folgende Eingabe anzeigen:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Verwenden von „Cmd.exe“-Variablen
PowerShell ist zwar nicht „Cmd.exe“, wird aber trotzdem in einer Befehlsshellumgebung ausgeführt und kann die Variablen verwenden, die in jeder Umgebung in Windows verfügbar sind. Diese Variablen werden über ein Laufwerk namens **env:** verfügbar gemacht. Sie können diese Variablen anzeigen, indem Sie Folgendes eingeben:

```
Get-ChildItem env:
```

Obwohl die Standardcmdlets für Variablen nicht so konzipiert sind, dass sie mit **env:** funktionieren, können Sie sie weiterhin verwenden, indem Sie das Präfix **env:** angeben. Wenn Sie beispielsweise das Stammverzeichnis des Betriebssystems anzeigen möchten, können Sie die Befehlsshellvariable **%SystemRoot%** in PowerShell verwenden, indem Sie Folgende eingeben:

```
PS> $env:SystemRoot
C:\WINDOWS
```

Sie können auch Umgebungsvariablen in PowerShell erstellen und ändern. Für Umgebungsvariablen, auf die über Windows PowerShell zugegriffen wird, gelten die normalen Regeln für Umgebungsvariablen wie an sonstigen Stellen in Windows.