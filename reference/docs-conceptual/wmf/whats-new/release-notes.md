---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Versionshinweise zu WMF 5.x
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402357"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x – Anmerkungen zu dieser Version

## <a name="wmf-50-changes"></a>WMF 5.0-Änderungen

- Mit PowerShell 5.0 wird ein neuer strukturierter **Information**sdatenstrom hinzugefügt.
- Verbesserungen an DSC umfassen vier neue DSC-Ressourcen:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Just Enough Administration hinzugefügt, um mithilfe von PowerShell-Remoting eine rollenbasierte Verwaltung zu ermöglichen.
- PowerShell 5.0 erweitert die Sprache, um benutzerdefinierte Klassen und Enumerationen einzuschließen.
- Verbesserte Debuggingfunktionen in PowerShell ISE und hinzugefügtes Remotedebuggen
- Module PowerShellGet und PackageManagement hinzugefügt.
- Erweiterte PowerShell-Skriptprotokollierung und -transkripte
- CMS-Cmdlets (Cryptographic Message Syntax, Syntax verschlüsselter Nachrichten) hinzugefügt.
- WMF 5.0 umfasst das NetworkSwitchManager-Modul für Windows.
- Microsoft.PowerShell.ODataUtils-Modul hinzugefügt.
- Unterstützung für Protokollierung des Softwarebestands (Software Inventory Logging, SIL) hinzugefügt.
- Mehrere neue oder aktualisiere Cmdlets als Reaktion auf Benutzeranforderungen und Probleme

## <a name="wmf-51-changes"></a>WMF 5.1 Änderungen

WMF 5.1 umfasst PowerShell, WMI und WinRM sowie SIL-Komponenten (Softwareinventurprotokollierung), die mit Windows Server 2016 veröffentlicht wurden. WMF 5.1 kann auf Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 und 2012 R2 installiert werden und bietet gegenüber WMF 5.0 eine Reihe von Vorteilen. Dazu zählen u. a.:

- Neue Cmdlets
- PowerShellGet-Verbesserungen wie z. B. die Durchsetzung von signierten Modulen und die Installation von JEA-Modulen
- Bei PackageManagement wurde Unterstützung für Container, CBS-Setup, EXE-basiertes Setup und CAB-Pakete hinzugefügt
- Debuggingverbesserungen für DSC und PowerShell-Klassen
- Sicherheitsverbesserungen wie u. a. die Durchsetzung von katalogsignierten Modulen vom Pullserver und bei Verwendung von PowerShellGet-Cmdlets
- Antworten auf verschiedene Benutzeranfragen und zu Problemen

> [!IMPORTANT]
> Vergewissern Sie sich vor der Installation von WMF 5.1 unter Windows Server 2008 oder Windows 7, dass WMF 3.0 nicht installiert ist. Weitere Informationen finden Sie unter [WMF 5.1-Voraussetzungen für Windows Server 2008 R2 SP1 und Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>PowerShell-Editionen

Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

### <a name="learn-more-about-using-powershell-editions"></a>Weitere Informationen zur Verwendung von PowerShell-Editionen

- [Determine running edition of PowerShell using $PSVersionTable (Bestimmen der ausgeführten Edition von PowerShell mit $PSVersionTable)](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filter Get-Module results by CompatiblePSEditions using PSEdition parameter (Filtern von Get-Module-Ergebnissen nach CompatiblePSEditions mithilfe des PSEdition-Parameters)](/powershell/module/microsoft.powershell.core/get-module)
- [Verhindern der Ausführung von Skripts außer bei Ausführung in einer kompatiblen Edition von PowerShell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [Deklarieren der Kompatibilität eines Moduls mit bestimmten Versionen von PowerShell](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Die Datei „ModuleAnalysisCache“

Ab Version 5.1 bietet PowerShell Kontrolle über die Datei, die zum Zwischenspeichern von Daten zu einem Modul verwendet wird, z. B. der Befehle, die es exportiert.

Standardmäßig wird dieser Cache in der Datei `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` gespeichert. Der Cache wird in der Regel beim Start der Suche nach einem Befehl gelesen und einige Zeit nach dem Import des Moduls in einem Hintergrundthread geschrieben.

Um den Standardspeicherort des Caches zu ändern, legen Sie die Umgebungsvariable `$env:PSModuleAnalysisCachePath` vor dem Starten von PowerShell fest. Änderungen an dieser Umgebungsvariablen betreffen nur untergeordnete Prozesse. Der Wert muss einen vollständigen Pfad (samt Dateiname) definieren, in dem PowerShell die Berechtigung zum Erstellen und Schreiben von Dateien hat. Zum Deaktivieren des Dateicaches kann dieser Wert auf einen ungültigen Speicherort festgelegt werden. Beispiel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermit wird der Pfad auf ein ungültiges Gerät festgelegt. Wenn PowerShell nicht in den Pfad schreiben kann, wird keine Fehlermeldung zurückgegeben. Mithilfe eines Ablaufverfolgungstools können Sie jedoch einen Fehlerbericht anzeigen:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Bei der Ausgabe aus dem Cache sucht PowerShell nach Modulen, die nicht mehr vorhanden sind, um einen unnötig großen Cache zu vermeiden. Mitunter sind diese Überprüfungen nicht wünschenswert, weshalb Sie sie deaktivieren können, indem Sie Folgendes festlegen:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Das Festlegen dieser Umgebungsvariablen wird im aktuellen Prozess sofort wirksam.

## <a name="specifying-module-version"></a>Angeben der Modulversion

In WMF 5.1 verhält sich `using module` genauso wie andere modulbezogene Konstruktionen in PowerShell.
Zuvor gab es keine Möglichkeit, eine bestimmte Modulversion anzugeben. Wenn mehrere Versionen vorhanden waren, führte dies zu einem Fehler.

In WMF 5.1:

- Sie können den [Konstruktor „ModuleSpecification“ (Hashtabelle)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) verwenden.

  Diese Hashtabelle hat das gleiche Format wie `Get-Module -FullyQualifiedName`.

  **Beispiel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Wenn mehrere Versionen des Moduls vorhanden sind, verwendet PowerShell **dieselbe Auflösungslogik** wie `Import-Module` und gibt keinen Fehler zurück, was dem Verhalten von `Import-Module` und `Import-DscResource` entspricht.

## <a name="improvements-to-pester"></a>Verbesserungen an Pester

In WMF 5.1 wurde die Version von Pester, die im Lieferumfang von PowerShell enthalten ist, von 3.3.5 auf 3.4.0 aktualisiert.
Dieses Update ermöglicht ein besseres Verhalten für Pester auf Nano Server.

Sie können die Änderungen in Pest überprüfen, indem Sie das [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) im GitHub-Repository durchgehen.
