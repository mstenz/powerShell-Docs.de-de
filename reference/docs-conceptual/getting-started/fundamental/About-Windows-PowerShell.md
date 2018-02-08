---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Informationen zu Windows PowerShell
ms.assetid: 979654ae-7994-47f8-be43-d79e7a140143
ms.openlocfilehash: 5e6d1bb4d8915ba3c83ba0020b959e444b5211cd
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="about-windows-powershell"></a>Informationen zu Windows PowerShell
Windows PowerShell ist auf das Verbessern der Befehlszeilen- und Skriptumgebung ausgelegt, indem lange bestehende Probleme beseitigt und neue Features hinzugefügt wurden.

## <a name="discoverability"></a>Erkennbarkeit
Windows PowerShell erleichtert das Ermitteln seiner Features. Um z. B. eine Liste von Cmdlets zu finden, die zum Anzeigen und Ändern von Windows-Diensten dienen, geben Sie Folgendes ein:

```
Get-Command *-Service
```

Nach dem Ermitteln, mit welchem Cmdlet eine Aufgabe erledigt wird, können Sie mithilfe des Cmdlets „Get-Help“ mehr über das Cmdlet erfahren. Geben Sie z.B. zum Anzeigen der Hilfe zum Cmdlet „Get-Service“ Folgendes ein:

```
Get-Help Get-Service
```
Die meisten Cmdlets geben Objekte aus, die bearbeitet und dann in Text für die Anzeige gerendert werden können. Um die Ausgabe dieses Cmdlets vollständig zu verstehen, leiten Sie seine Ausgabe an das Cmdlet „Get-Member“ weiter. Der folgende Befehl zeigt z.B. Informationen zu den Elementen des Objekts an, das vom Cmdlet „Get-Service“ ausgegeben wurde.

```
Get-Service | Get-Member
```

## <a name="consistency"></a>Konsistenz
Das Verwalten von Systemen kann ein komplexer Vorgang sein, und Tools mit einer konsistenten Schnittstelle helfen, die inhärente Komplexität im Griff zu behalten. Leider zeichnen sich weder Befehlszeilentools noch skriptfähige COM-Objekte durch ihre Konsistenz aus.

Die Konsistenz von Windows PowerShell ist einer der wesentlichen Vorteile. Wenn Sie z.B. gelernt haben, wie das Cmdlet „Sort-Object“ verwendet wird, können Sie mit diesem Wissen die Ausgabe sämtlicher Cmdlets sortieren. Sie müssen also nicht für jedes Cmdlet eine andere Sortierroutine erlernen.

Darüber hinaus müssen Cmdlet-Entwickler keine Sortierfunktionen für ihre Cmdlets entwerfen. Windows PowerShell bietet ihnen ein Framework, das die grundlegenden Funktionen bereitstellt und Konsistenz bei vielen Aspekten der Schnittstelle erzwingt. Das Framework bietet nicht mehr einige der Wahlmöglichkeiten, die normalerweise dem Entwickler überlassen werden, vereinfacht aber im Gegenzug die Entwicklung zuverlässiger und benutzerfreundlicher Cmdlets wesentlich.

## <a name="interactive-and-scripting-environments"></a>Interaktive und Skriptumgebung
Windows PowerShell ist eine kombinierte interaktive und Skriptumgebung, die Zugriff auf Befehlszeilentools und COM-Objekte bietet und auch das Ausnutzen der Leistungsfähigkeit der .NET Framework Class Library (FCL) ermöglicht.

Diese Umgebung verbessert die Windows-Eingabeaufforderung, die eine interaktive Umgebung mit mehreren Befehlszeilentools bereitstellt. Sie verbessert auch WSH-Skripts (Windows Script Host), mit denen Sie können mehrere Befehlszeilentools und COM-Automatisierungsobjekte verwenden können, die aber keine interaktive Umgebung bieten.

Durch die Kombination aller dieser Features erweitert Windows PowerShell die Möglichkeiten des interaktiven Benutzers und Skripterstellers und zur Vereinfachung der Systemadministration.

## <a name="object-orientation"></a>Objektorientierung
Obwohl Sie mit Windows PowerShell interagieren, indem Sie Befehle als Text eingeben, basiert Windows PowerShell auf Objekten und nicht auf Text. Die Ausgabe eines Befehls ist ein Objekt. Sie können das Ausgabeobjekt als Eingabe an einen anderen Befehl weiterleiten. Daher bietet Windows PowerShell eine vertraute Schnittstelle für Personen, die mit anderen Shells vertraut sind, und führt gleichzeitig ein neues, leistungsstarkes Befehlszeilenmodell ein. Das Konzept des Übermittelns von Daten zwischen Befehlen wird erweitert, indem Sie Objekte anstelle von Text übermitteln können.

## <a name="easy-transition-to-scripting"></a>Einfacher Übergang zur Skripterstellung
Windows PowerShell vereinfacht den Übergang von der interaktiven Eingabe von Befehlen zum Erstellen und Ausführen von Skripts. Sie können Befehle an der Windows PowerShell-Eingabeaufforderung eingeben, um die Befehle zu ermitteln, die eine Aufgabe ausführen. Dann können Sie diese Befehle in einer Aufzeichnung oder einem Verlauf speichern, bevor Sie sie in eine Datei zur Verwendung als Skript kopieren.

