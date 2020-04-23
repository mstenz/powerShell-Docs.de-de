---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Abrufen von Informationen zu Befehlen
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030948"
---
# <a name="getting-information-about-commands"></a>Abrufen von Informationen zu Befehlen

Das PowerShell-Cmdlet `Get-Command` zeigt Befehle an, die in Ihrer aktuellen Sitzung verfügbar sind.
Wenn Sie das Cmdlet `Get-Command` ausführen, wird eine Ausgabe wie die folgende angezeigt:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Diese Ausgabe hat große Ähnlichkeit mit der Hilfe-Ausgabe von **Cmd.exe**: Sie umfasst eine tabellarische Zusammenfassung der internen Befehle. Im Auszug der oben gezeigten `Get-Command`-Befehlsausgabe weist jeder aufgeführte Befehl den Befehlstyp (CommandType) „Cmdlet“ auf. Ein Cmdlet ist ein systeminterner PowerShell-Befehlstyp. Dieser Typ entspricht in etwa Befehlen wie `dir` und `cd` in **cmd.exe** oder den integrierten Befehlen von Unix-Shells wie Bash.

Das Cmdlet `Get-Command` umfasst einen Parameter **Syntax**, der die Syntax jedes Cmdlets zurückgibt. Das folgende Beispiel zeigt, wie Sie die Syntax für das Cmdlet `Get-Help` abrufen:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Anzeigen verfügbarer Befehle nach Typ

Mit dem Befehl `Get-Command` werden nur die Cmdlets in der aktuellen Sitzung aufgelistet. PowerShell unterstützt tatsächlich verschiedene weitere Befehlstypen:

- Aliase
- Functions
- Skripts

Externe ausführbare Dateien oder Dateien mit einem registrierten Dateityphandler werden ebenfalls als Befehle klassifiziert.

Um alle Befehle in der Sitzung aufzurufen, geben Sie Folgendes ein:

```powershell
Get-Command *
```

Diese Liste schließt externe Dateien in Ihrem Suchpfad ein, deshalb kann sie Tausende von Elementen enthalten.
Es ist sinnvoller, einen reduzierten Satz von Befehlen anzuzeigen.

> [!NOTE]
> Das Sternchen (\*) wird zum Abgleich mit Platzhalterzeichen in PowerShell-Befehlsargumenten verwendet. \* bedeutet „Abgleichen mit einem oder mehreren beliebigen Zeichen“. Beispielsweise können Sie `Get-Command a*` eingeben, um nach allen Befehlen zu suchen, die mit dem Buchstaben „a“ beginnen. Anders als beim Platzhalterabgleich in **cmd.exe** führt das PowerShell-Platzhalterzeichen auch einen Abgleich mit einem Punkt durch.

Verwenden Sie den **CommandType**-Parameter von `Get-Command`, um die nativen Befehle anderer Typen
abzurufen.

Geben Sie Folgendes ein, um Befehlsaliase abzurufen, bei denen es sich um die zugewiesenen Spitznamen von Befehlen handelt:

```powershell
Get-Command -CommandType Alias
```

Um die Funktionen in der aktuellen Sitzung abzurufen, geben Sie Folgendes ein:

```powershell
Get-Command -CommandType Function
```

Um Skripts im Suchpfad von PowerShell anzuzeigen, geben Sie Folgendes ein:

```powershell
Get-Command -CommandType Script
```
