---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Was ist PowerShell?
ms.openlocfilehash: 267b2938a0892c99c3a961bc7107f573df40a683
ms.sourcegitcommit: 38215ad49e237b219e62bb5a5f0eb3b6b048df1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "83868478"
---
# <a name="what-is-powershell"></a>Was ist PowerShell?

PowerShell ist ein Framework zur plattformübergreifenden Aufgabenautomatisierung und Konfigurationsverwaltung und besteht aus einer Befehlszeilenshell und Skriptsprache. Im Gegensatz zu den meisten Shells, bei denen Text akzeptiert und zurückgegeben wird, basiert PowerShell auf der .NET Common Language Runtime (CLR) und akzeptiert und gibt .NET-Objekte zurück. Diese grundlegende Änderung bringt völlig neue Tools und Methoden für die Automatisierung mit sich.

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a>Die Ausgabe ist objektbasiert

Im Gegensatz zu herkömmlichen Befehlszeilenschnittstellen sind PowerShell-Cmdlets für den Umgang mit Objekten entworfen.
Ein Objekt setzt sich aus strukturierten Informationen zusammen und ist mehr als nur die Zeichenfolge, die auf dem Bildschirm erscheint. Die Befehlsausgabe umfasst immer zusätzliche Informationen, die Sie bei Bedarf nutzen können.

Wenn Sie in schon mal ein Textverarbeitungsprogramm zum Verarbeiten von Daten verwendet haben, werden Sie das abweichende Verhalten der Daten in PowerShell bemerken. In den meisten Fällen benötigen Sie kein Textverarbeitungsprogramm, um bestimmte Informationen zu extrahieren. Sie greifen mit der standardmäßigen PowerShell-Objektsyntax direkt auf Teile der Daten zu.

## <a name="the-command-family-is-extensible"></a>Die Befehlsfamilie ist erweiterbar

Schnittstellen wie `cmd.exe` bieten keine Möglichkeit zur direkten Erweiterung des integrierten Befehlssatzes. Sie können externe Befehlszeilentools erstellen, die in `cmd.exe` ausgeführt werden. Aber diese externen Tools umfassen keine Dienste wie z.B. eine integrierte Hilfe. `cmd.exe` weiß nicht automatisch, dass es sich bei diesen externen Tools um gültige Befehle handelt.

Die Befehle in PowerShell werden als _Cmdlets_ bezeichnet. Sie können jedes Cmdlet einzeln verwenden, aber deren Leistungsfähigkeit wird freigesetzt, wenn Sie diese kombinieren, um komplexe Aufgaben auszuführen. Ähnlich wie viele Shells ermöglicht PowerShell Ihnen Zugriff auf das Dateisystem auf dem Computer. Mit PowerShell-_Anbietern_ haben Sie die Möglichkeit, auf andere Datenspeicher, etwa die Registrierung und den Zertifikatspeicher, so einfach zuzugreifen wie auf das Dateisystem.

Mithilfe von kompiliertem Code oder Skripts können Sie eigene Cmdlets und Funktionsmodule erstellen. Mit Modulen können der Shell Cmdlets und Anbieter hinzugefügt werden. PowerShell bietet außerdem Unterstützung für Skripts, analog zu UNIX-Shellskripts und `cmd.exe`-Batchdateien.

## <a name="support-for-command-aliases"></a>Unterstützung für Befehlsaliase

PowerShell unterstützt Aliase, um mit alternativen Namen auf Befehle zu verweisen. Durch Aliase können Benutzer mit Erfahrung in anderen Shell-Umgebungen gängige Befehlsnamen, die sie bereits kennen, für ähnliche Vorgänge in PowerShell verwenden.

Bei der Aliasverwendung wird einem Befehl ein neuer Name zugeordnet. Beispielsweise umfasst PowerShell eine interne Funktion namens `Clear-Host`, mit der das Ausgabefenster gelöscht wird. Sie können an einer Eingabeaufforderung entweder `cls` oder den Alias `clear` eingeben. PowerShell interpretiert diese Aliase und führt die Funktion `Clear-Host` aus.

Dieses Feature unterstützt Benutzer beim Erlernen von PowerShell. Zunächst beherrschen die meisten `cmd.exe`- und Unix-Benutzer ein großes Repertoire an Befehlen, deren Namen sie bereits kennen. Die PowerShell-Äquivalente führen möglicherweise nicht zu identischen Ergebnissen. Dennoch sind die Ergebnisse ähnlich genug, um Benutzern das Arbeiten ohne Kenntnis der PowerShell-Befehlsnamen zu ermöglichen. Das „Muskelgedächtnis“ ist eine weitere Quelle für Frustrationen beim Erlernen einer neuen Befehlsshell. Wenn Sie seit Jahren `cmd.exe` verwenden, geben Sie möglicherweise reflexartig den Befehl `cls` ein, um den Bildschirm zu löschen. Ohne den Alias für `Clear-Host` erhalten Sie eine Fehlermeldung und wissen nicht, wie Sie zum Löschen der Ausgabe vorgehen müssen.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell verarbeitet Konsoleneingabe und Anzeige

Wenn Sie einen Befehl eingeben, verarbeitet PowerShell die Befehlszeileneingabe immer sofort. PowerShell formatiert darüber hinaus die Ausgabe, die auf dem Bildschirm angezeigt wird. Dieser Unterschied ist wesentlich, weil dadurch die Arbeit für jedes Cmdlet verringert wird. Es wird sichergestellt, dass Sie Aufgaben mit beliebigen Cmdlets immer gleich ausführen können. Cmdlet-Entwickler müssen keinen Code schreiben, mit dem die Befehlszeilenargumente analysiert oder die Ausgabe formatiert wird.

Herkömmliche Befehlszeilentools haben eigene Schemas zum Anfordern und Anzeigen von Hilfe. Einige Befehlszeilentools verwenden `/?` zum Aufrufen der Hilfe, während andere `-?`, `/H` oder `//` verwenden. Bei einigen wird Hilfe in einem Fenster auf der grafischen Benutzeroberfläche und nicht in der Konsole angezeigt. Wenn Sie den falschen Parameter verwenden, ignoriert das Tool möglicherweise Ihre Eingabe und beginnt damit, automatisch einen Task auszuführen.
Da PowerShell die Befehlszeile automatisch analysiert und verarbeitet, bedeutet der Parameter `-?` immer „Hilfe für diesen Befehl anzeigen“.

> [!NOTE]
> Wenn Sie eine grafische Anwendung in PowerShell ausführen, wird das Fenster für die Anwendung geöffnet.
> PowerShell greift nur beim Verarbeiten der angegebenen Befehlszeileneingabe oder zur Ausgabe der Anwendungsergebnisse im Konsolenfenster ein. PowerShell hat keinen Einfluss darauf, wie die Anwendung intern arbeitet.

## <a name="powershell-has-a-pipeline"></a>Die PowerShell-Pipeline

Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird. Bei richtigem Einsatz verringern Pipelines den Aufwand durch die Verwendung von komplexen Befehlen und erleichtern es, den Ablauf zu sehen. Jeder Befehl in einer Pipeline gibt seine Ausgabe Element für Element an den nächsten Befehl weiter. Befehle müssen jeweils nur ein Element zurzeit verarbeiten. Das Ergebnis ist eine verringerte Ressourcennutzung und die Möglichkeit, die Ausgabe unmittelbar zu erhalten.

Die Notation für Pipelines ist der Notation in anderen Shells ähnlich. Auf den ersten Blick ist es möglicherweise nicht offensichtlich, wie sich Pipelines in PowerShell unterscheiden. Obwohl Text auf dem Bildschirm angezeigt wird, leitet PowerShell Objekte und keinen Text zwischen Befehlen weiter.

Wenn Sie beispielsweise das Cmdlet `Out-Host` zum Erzwingen einer seitenweisen Anzeige der Ausgabe eines anderen Befehls verwenden, sieht die Ausgabe wie der normale auf dem Bildschirm gezeigte Text aus, der in Seiten unterteilt ist:

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

Durch die Einteilung in Seiten wird auch die CPU-Auslastung reduziert, da die Verarbeitung an das Cmdlet `Out-Host` übertragen wird, wenn eine vollständige Seite für die Anzeige bereit ist. Die Cmdlets, die sich in der Pipeline davor befinden, unterbrechen die Ausführung, bis die nächste Seite der Ausgabe verfügbar ist.

### <a name="objects-in-the-pipeline"></a>Objekte in der Pipeline

Wenn Sie ein Cmdlet in PowerShell ausführen, sehen Sie eine Textausgabe, da es erforderlich ist, Objekte in einem Konsolenfenster als Text darzustellen. Die Textausgabe enthält möglicherweise nicht alle Eigenschaften des Objekts, das ausgegeben wird.

Betrachten Sie beispielsweise das Cmdlet `Get-Location`. Die Textausgabe ist eine Zusammenfassung der Informationen, keine vollständige Darstellung des Objekts, das von `Get-Location` zurückgegeben wird. Die Überschrift in der Ausgabe wird durch den Prozess hinzugefügt, der die Daten für die Anzeige auf dem Bildschirm formatiert.

```powershell
Get-Location
```

```Output
Path
----
C:\
```

Wenn Sie die Ausgabe an das Cmdlet `Get-Member` weiterleiten, werden Informationen über das Objekt angezeigt, das von `Get-Location` zurückgegeben wird.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` gibt ein **PathInfo**-Objekt zurück, das den aktuellen Pfad und andere Informationen enthält.

## <a name="built-in-help-system"></a>Integriertes Hilfesystem

Ähnlich wie bei `man`-Seiten, umfasst PowerShell ausführliche Hilfeartikel, in denen die Konzepte von PowerShell und die Befehlssyntax erläutert werden. Verwenden Sie das Cmdlet [Get-Help][], um diese Artikel über die Eingabeaufforderung anzuzeigen. Sie können aber auch die zuletzt aktualisierten Versionen dieser Artikel in der PowerShell-Dokumentation online anzeigen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu PowerShell erhalten Sie im Abschnitt **Erlernen von PowerShell** auf dieser Website.

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
