---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: Erlernen der Namen der PowerShell-Befehl
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 3f8ef2648709c4bb5d2eacf30fe9d8fb4f032c13
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012465"
---
# <a name="learning-powershell-command-names"></a>Erlernen der Namen der PowerShell-Befehl

Das Erlernen der Namen von Befehlen und Parametern ist bei den meisten Befehlszeilenschnittstellen mit einem hohen Zeitaufwand verbunden. Das Problem liegt darin, dass nur wenige Muster vorhanden sind. Erinnerung zu behalten, ist die einzige Möglichkeit, lernen die Befehle und Parameter, die Sie regelmäßig verwenden müssen.

Wenn Sie mit einem neuen Befehl oder Parameter arbeiten, können Sie nicht immer auf Bekanntes zurückgreifen. Sie müssen nach neuen Namen suchen und diese lernen. Üblicherweise umfassen Befehlszeilenschnittstellen zu Beginn lediglich einen kleinen Satz an Tools und wachsen mit zunehmenden Ergänzungen. Es ist leicht zu verstehen, warum es keine Standardstruktur gibt.
Dies erscheint bei Befehlsnamen logisch, da jeder Befehl ein eigenes Tool darstellt. PowerShell bietet eine bessere Möglichkeit, Befehlsnamen zu verarbeiten.

## <a name="learning-command-names-in-traditional-shells"></a>Erlernen von Namen in herkömmlichen Shells

Die meisten Befehle werden erstellt, um Elemente des Betriebssystems oder von Anwendungen, z. B. Dienste oder Prozesse, zu verwalten. Die Befehle haben Namen, die zu einer Familie gehören oder auch nicht. Auf Windows-Systemen können Sie z.B. die Befehle `net start` und `net stop` zum Starten und Beenden eines Diensts verwenden. **Sc.exe** ist ein weiteres Tool zur Dienststeuerung für Windows. Dieser Name passt nicht in das Namensmuster für die **net.exe**-Dienstbefehle. Für die Verwaltung von Prozessen bietet Windows den Befehl **tasklist.exe** zum Auflisten von Prozessen und den Befehl **taskkill.exe** zum Beenden von Prozessen.

Darüber hinaus verwenden diese Befehle irreguläre Parameterspezifikationen. Sie können den Befehl `net start` nicht zum Starten eines Diensts auf einem Remotecomputer verwenden. Mit dem Befehl **sc.exe** kann Dienst auf einem Remotecomputer gestartet werden. Um den Remotecomputer anzugeben, müssen sie seinem Namen jedoch einen doppelten umgekehrten Schrägstrich voranstellen. Um den Spoolerdienst auf einem Remotecomputer namens „DC01“ zu starten, geben Sie `sc.exe \\DC01 start spooler` ein.
Um die auf „DC01“ ausgeführten Aufgaben aufzulisten, verwenden Sie den Parameter **/S** und den Computernamen ohne Schrägstriche. Beispiel: `tasklist /S DC01`.

> [!NOTE]
> Vor PowerShell v6 war `sc` ein Alias für das Cmdlet `Set-Content`. Zum Ausführen des Befehls **sc.exe** musste die Dateierweiterung eingeschlossen werden.

Dienste und Prozesse sind Beispiele für verwaltbare Elemente auf einem Computer mit gut definierten Lebenszyklen. Sie können einen Dienst oder Prozess starten oder beenden oder eine Liste aller derzeit ausgeführten Dienste und Prozesse abrufen. Wenngleich es wichtige technische Unterschiede zwischen ihnen gibt, sind die für Dienste und Prozesse ausgeführten Aktionen vom Konzept her identisch. Darüber hinaus können auch Entscheidungen, die wir zum Anpassen einer Aktion durch das Angeben von Parametern treffen, konzeptionell vergleichbar sein.

PowerShell nutzt diese Ähnlichkeiten zum Verringern der Anzahl unterschiedlicher Namen, die Sie kennen müssen, um Cmdlets zu verstehen und zu nutzen.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlets kombinieren für eine bessere Einprägsamkeit Verben und Nomen in ihrem Namen

PowerShell verwendet eine Verb-Nomen-Namenskonvention. Jeder Cmdlet-Name besteht aus einem Standardverb, an das ein Bindestrich und ein bestimmtes Nomen angehängt wird. PowerShell-Verben sind nicht immer englische Verben, drücken aber bestimmte Aktionen in PowerShell aus. Die Nomen ähneln denen in einer beliebigen Sprache. Sie beschreiben bestimmte Arten von Objekten, die bei der Systemadministration wichtig sind. Anhand einiger Beispiele ist einfach zu veranschaulichen, wie diese zweiteiligen Namen den Lernaufwand verringern.

PowerShell umfasst einen empfohlenen Satz an Standardverben. Nomen sind weniger eingeschränkt, beschreiben aber stets, worauf das Verb angewendet wird. PowerShell umfasst Befehle wie z.B. `Get-Process`, `Stop-Process`, `Get-Service` und `Stop-Service`.

In diesem Fall von zwei Nomen und zwei Verben vereinfacht die Konsistenz den Lernprozess nicht wesentlich. Erweitern Sie diese Liste auf einen standardisierten Satz von 10 Verben und 10 Nomen. Jetzt müssen Sie nur 20 Wörter kennen.
Aber diese Wörter können zu insgesamt 100 unterschiedlichen Befehlsnamen kombiniert werden.

Die Wirkung eines PowerShell-Befehls kann leicht an seinem Namen abgelesen werden. Der Befehl zum Herunterfahren eines Computers lautet `Stop-Computer`. Der Befehl zum Auflisten aller Computer im Netzwerk lautet `Get-Computer`. Der Befehl um Abrufen der Systemdaten lautet `Get-Date`.

Über den **Verb**-Parameter für `Get-Command` können Sie alle Befehle mit einem bestimmten Verb auflisten. Um beispielsweise alle Cmdlets anzuzeigen, die das Verb `Get` verwenden, geben Sie Folgendes ein:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Verwenden Sie den **Noun**-Parameter, um eine Familie von Befehlen anzuzeigen, die sich auf den gleichen Objekttyp auswirken. Führen Sie beispielsweise den folgenden Befehl aus, um die verfügbaren Befehle zum Verwalten von Diensten anzuzeigen:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Cmdlets verwenden Standardparameter

Wie bereits erwähnt, weisen in herkömmlichen Befehlsschnittstellen verwendete Befehle nicht immer konsistente Parameternamen auf. Parameter sind oft einzelne Zeichen oder abgekürzte Wörter, die schnell eingegeben werden können, aber für neue Benutzer nicht leicht verständlich sind.

Im Gegensatz zu den meisten anderen herkömmlichen Befehlszeilenschnittstellen verarbeitet PowerShell Parameter direkt und nutzt diesen direkten Zugriff auf die Parameter (zusammen mit Anleitungen für Entwickler), um Parameternamen zu standardisieren. Diese Anleitung empfiehlt, garantiert aber nicht, dass jedes Cmdlet dem Standard entspricht.

PowerShell standardisiert außerdem das Trennzeichen für Parameter. Parameternamen verwenden immer einen angehängten Bindestrich („-“), auf den ein PowerShell-Befehl folgt. Betrachten Sie das folgenden Beispiel:

```powershell
Get-Command -Name Clear-Host
```

Der Parametername lautet **Name**, wird aber eingegeben als `-Name`, wenn er in der Befehlszeile als Parameter verwendet wird.

Es folgen einige allgemeine Merkmale der Standardparameternamen und ihre Verwendungen.

### <a name="the-help-parameter-"></a>Der Parameter „Hilfe“ (?)

Wenn Sie den Parameter `-?` für ein beliebiges Cmdlet angeben, zeigt PowerShell Hilfeinformationen für das Cmdlet an.
Das Cmdlet wird nicht ausgeführt.

### <a name="common-parameters"></a>Allgemeine Parameter

PowerShell umfasst verschiedene *allgemeine Parameter*. Diese Parameter werden durch die PowerShell-Engine gesteuert. Allgemeine Parameter verhalten sich immer gleich. Die allgemeinen Parameter heißen **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** und **OutBuffer**.

### <a name="recommended-parameter-names"></a>Empfohlene Parameternamen

Der Kernsatz an PowerShell-Cmdlets verwendet standardmäßige Namen für ähnliche Parameter. Die Verwendung von standardmäßigen Parameternamen wird nicht erzwungen, aber es gibt zur Förderung der Standardisierung explizite Anleitungen.

Beispielsweise wird für einen Parameter, der anhand des Namens auf einen Computer verweist, die Bezeichnung **ComputerName** empfohlen, statt „Server“, „Host“, „System“, „Node“ oder eine andere gängige Alternative zu wählen. Weitere empfohlene Parameternamen sind **Force**, **Exclude**, **Include**, **PassThru**, **Path** und **CaseSensitive**.
