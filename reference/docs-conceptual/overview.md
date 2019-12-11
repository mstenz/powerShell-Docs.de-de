---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell-Skripterstellung
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058487"
---
# <a name="powershell"></a>PowerShell

PowerShell ist eine aufgabenbasierte Befehlszeilenshell und Skriptsprache, die auf .NET basiert.
Mit PowerShell können Systemadministratoren und Poweruser Aufgaben zum Verwalten von Betriebssystemen (Linux, macOS und Windows) und Prozessen schnell automatisieren.

Über PowerShell-Befehle können Sie Computer mit der Befehlszeile verwalten. Mithilfe von PowerShell-Anbietern können Sie auf Datenspeicher wie die Registrierung und den Zertifikatspeicher genauso einfach zugreifen wie auf das Dateisystem. PowerShell verfügt über einen umfangreichen Ausdrucksparser und eine vollständig entwickelte Skriptsprache.

## <a name="powershell-is-open-source"></a>PowerShell ist Open Source

Der grundlegende PowerShell-Quellcode ist jetzt auf GitHub verfügbar und für Community-Beiträge offen.
Informationen dazu finden Sie unter [PowerShell-Quellcode auf GitHub](https://github.com/powershell/powershell).

Sie können sich alles Notwendige [hier](https://github.com/PowerShell/PowerShell#get-powershell) im Abschnitt „Get PowerShell“ (PowerShell herunterladen) herunterladen.
Beginnen Sie alternativ mit einer kurzen Einführung unter [Getting Started (Erste Schritte)](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>PowerShell-Entwurfsziele

PowerShell soll Befehlszeilen- und Skriptumgebungen verbessern. Es beseitigt lange bestehende Probleme und führt neue Features ein.

### <a name="discoverability"></a>Erkennbarkeit

Sie können sich leicht mit den Features in PowerShell vertraut machen. Um z. B. eine Liste von Cmdlets zu finden, die zum Anzeigen und Ändern von Windows-Diensten dienen, geben Sie Folgendes ein:

```powershell
Get-Command *-Service
```

Nachdem Sie ermittelt haben, welches Cmdlet welche Aufgabe erledigt, können Sie mithilfe des Cmdlets `Get-Help` mehr über das Cmdlet erfahren. Geben Sie z.B. zum Anzeigen der Hilfe zum Cmdlet `Get-Service` Folgendes ein:

```powershell
Get-Help Get-Service
```

Die meisten Cmdlets geben Objekte zurück, die bearbeitet und dann als Text für die Anzeige gerendert werden können. Um die Ausgabe eines Cmdlets vollständig zu verstehen, leiten Sie die Ausgabe an das Cmdlet `Get-Member` weiter. Der folgende Befehl zeigt z.B. Informationen zu den Elementen des Objekts an, das vom Cmdlet `Get-Service` ausgegeben wurde.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Konsistenz

Das Verwalten von Systemen kann eine komplexe Aufgabe sein. Tools mit einer konsistenten Schnittstelle helfen, die inhärente Komplexität im Griff zu behalten. Leider zeichnen sich Befehlszeilentools und skriptfähige COM-Objekte (Component Object Model) nicht durch ihre Konsistenz aus.

PowerShell besticht durch Konsistenz. Wenn Sie z.B. gelernt haben, wie das Cmdlet `Sort-Object` verwendet wird, können Sie mit diesem Wissen die Ausgabe sämtlicher Cmdlets sortieren. Sie müssen also nicht für jedes Cmdlet eine andere Sortierroutine erlernen.

Darüber hinaus müssen Cmdlet-Entwickler keine Sortierfunktionen für ihre Cmdlets entwerfen. PowerShell bietet ein Framework mit den grundlegenden Funktionen, das Konsistenz erzwingt. Das Framework bietet einige Optionen nicht, die dem Entwickler überlassen werden. Im Gegenzug vereinfacht es aber die Entwicklung von Cmdlets deutlich.

### <a name="interactive-and-scripting-environments"></a>Interaktive und Skriptumgebungen

Die Windows-Eingabeaufforderung bietet eine interaktive Shell mit Zugriff auf Befehlszeilentools und grundlegende Funktionen für die Skripterstellung. Windows Script Host (WSH) weist skriptfähige Befehlszeilentools und COM-Automatisierungsobjekte auf, jedoch keine interaktive Shell.

PowerShell kombiniert eine interaktive Shell und einer Skriptumgebung. PowerShell kann auf Befehlszeilentools, COM-Objekte und .NET-Klassenbibliotheken zugreifen. Diese Kombination von Features erweitert die Möglichkeiten von interaktiven Benutzern, Skriptautoren und Systemadministratoren.

### <a name="object-orientation"></a>Objektorientierung

PowerShell ist objekt- und nicht textbasiert. Die Ausgabe eines Befehls ist ein Objekt. Sie können das Ausgabeobjekt über die Pipeline als Eingabe an einen anderen Befehl senden.

Diese Pipeline bietet Benutzern, die bereits über Erfahrung mit anderen Shells verfügen, eine vertraute Schnittstelle. PowerShell erweitert dieses Konzept durch das Senden von Objekten anstelle von Text.

### <a name="easy-transition-to-scripting"></a>Einfacher Übergang zur Skripterstellung

Die Erkennbarkeit von Befehlen in PowerShell vereinfacht den Übergang von der interaktiven Eingabe von Befehlen zum Erstellen und Ausführen von Skripts. Aufzeichnungen und der Verlauf von PowerShell erleichtern das Kopieren von Befehlen in eine Datei, um sie als Skript zu verwenden.
