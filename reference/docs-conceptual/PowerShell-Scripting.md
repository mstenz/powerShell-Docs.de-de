---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShell-Skripterstellung
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094050"
---
# <a name="powershell"></a>PowerShell

PowerShell basiert auf dem .NET Framework und ist eine aufgabenbasierte Befehlszeilenshell und Skriptsprache. Sie wurde speziell für Administratoren und Poweruser entworfen, um das Verwalten von mehreren Betriebssystemen (Linux, macOS, Unix und Windows) und die anwendungsbezogenen Prozesse auf diesen Betriebssystemen schnell zu automatisieren.

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

Nachdem Sie ermittelt haben, welches Cmdlet welche Aufgabe erledigt, können Sie mithilfe des Cmdlets `Get-Help` mehr über das Cmdlet erfahren.
Geben Sie z.B. zum Anzeigen der Hilfe zum Cmdlet `Get-Service` Folgendes ein:

```powershell
Get-Help Get-Service
```
Die meisten Cmdlets geben Objekte aus, die bearbeitet und dann in Text für die Anzeige gerendert werden können.
Um die Ausgabe dieses Cmdlets vollständig zu verstehen, leiten Sie seine Ausgabe an das Cmdlet `Get-Member` weiter.
Der folgende Befehl zeigt z.B. Informationen zu den Elementen des Objekts an, das vom Cmdlet `Get-Service` ausgegeben wurde.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Konsistenz
Das Verwalten von Systemen kann ein komplexer Vorgang sein, und Tools mit einer konsistenten Schnittstelle helfen, die inhärente Komplexität im Griff zu behalten.
Leider zeichnen sich weder Befehlszeilentools noch skriptfähige COM-Objekte durch ihre Konsistenz aus.

PowerShell besticht durch Konsistenz.
Wenn Sie z.B. gelernt haben, wie das Cmdlet `Sort-Object` verwendet wird, können Sie mit diesem Wissen die Ausgabe sämtlicher Cmdlets sortieren.
Sie müssen also nicht für jedes Cmdlet eine andere Sortierroutine erlernen.

Darüber hinaus müssen Cmdlet-Entwickler keine Sortierfunktionen für ihre Cmdlets entwerfen.
PowerShell bietet ihnen ein Framework, das grundlegende Funktionen bereitstellt und Konsistenz bei vielen Aspekten der Schnittstelle erzwingt.
Das Framework bietet nicht mehr einige der Wahlmöglichkeiten, die normalerweise dem Entwickler überlassen werden, vereinfacht aber im Gegenzug die Entwicklung zuverlässiger und benutzerfreundlicher Cmdlets wesentlich.

### <a name="interactive-and-scripting-environments"></a>Interaktive und Skriptumgebung
PowerShell ist sowohl eine interaktive Umgebung als auch eine Skriptumgebung, die Zugriff auf Befehlszeilentools und COM-Objekte bietet, mit der Sie von der Leistungsfähigkeit der .NET Framework Class Library (FCL) profitieren können.

Diese Umgebung verbessert die Windows-Eingabeaufforderung, die eine interaktive Umgebung mit mehreren Befehlszeilentools bereitstellt.
Sie verbessert auch WSH-Skripts (Windows Script Host), mit denen Sie können mehrere Befehlszeilentools und COM-Automatisierungsobjekte verwenden können, die aber keine interaktive Umgebung bieten.

Durch die Kombination dieser Features erweitert PowerShell die Möglichkeiten des interaktiven Benutzers und Skripterstellers und vereinfacht die Systemverwaltung.

### <a name="object-orientation"></a>Objektorientierung
Obwohl Sie mit PowerShell interagieren, indem Sie Befehle als Text eingeben, ist PowerShell objekt- und nicht textbasiert.
Die Ausgabe eines Befehls ist ein Objekt.
Sie können das Ausgabeobjekt als Eingabe an einen anderen Befehl weiterleiten.
Daher bietet PowerShell eine vertraute Schnittstelle für Personen, die mit anderen Shells vertraut sind, und führt gleichzeitig ein neues, leistungsstarkes Befehlszeilenmodell ein.
Das Konzept des Übermittelns von Daten zwischen Befehlen wird erweitert, indem Sie Objekte anstelle von Text übermitteln können.

### <a name="easy-transition-to-scripting"></a>Einfacher Übergang zur Skripterstellung
PowerShell vereinfacht den Übergang von der interaktiven Eingabe von Befehlen zum Erstellen und Ausführen von Skripts.
Sie können Befehle an der PowerShell-Eingabeaufforderung eingeben, um die Befehle zu ermitteln, die eine Aufgabe ausführen.
Dann können Sie diese Befehle in einer Aufzeichnung oder einem Verlauf speichern, bevor Sie sie in eine Datei zur Verwendung als Skript kopieren.
