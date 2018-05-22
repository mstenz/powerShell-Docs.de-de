---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Neue Szenarios und Features in WMF 5.1
ms.openlocfilehash: 77b439e61c5802f8ddbc4a0f39923cc8c0c36fe9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Neue Szenarios und Features in WMF 5.1

> Hinweis: Diese Dokumentation ist vorläufig und kann geändert werden.

## <a name="powershell-editions"></a>PowerShell-Editionen

Ab Version 5.1 ist PowerShell in verschiedenen Editionen verfügbar, die unterschiedliche Funktionen mitbringen und zu unterschiedlichen Plattformen kompatibel sind.

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

**Weitere Informationen zur Verwendung von PowerShell-Editionen**

- [Determine running edition of PowerShell using $PSVersionTable (Bestimmen der ausgeführten Edition von PowerShell mit $PSVersionTable)](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filter Get-Module results by CompatiblePSEditions using PSEdition parameter (Filtern von Get-Module-Ergebnissen nach CompatiblePSEditions mithilfe des PSEdition-Parameters)](/powershell/module/microsoft.powershell.core/get-module)
- [Verhindern der Ausführung von Skripts außer bei Ausführung in einer kompatiblen Edition von PowerShell](/powershell/gallery/psget/script/scriptwithpseditionsupport)
- [Deklarieren der Kompatibilität eines Moduls mit bestimmten Versionen von PowerShell](/powershell/gallery/psget/module/modulewithpseditionsupport)

## <a name="catalog-cmdlets"></a>Katalog-Cmdlets

Dem [Microsoft.PowerShell.Security](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security)-Modul wurden zwei neue Cmdlets hinzugefügt, die Windows-Katalogdateien generieren und überprüfen.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

„New-FileCatalog“ erstellt eine Windows-Katalogdatei für eine Gruppe von Ordnern und Dateien.
Diese Katalogdatei enthält die Hashes aller Dateien in bestimmten Pfaden.
Benutzer können den Satz von Ordnern zusammen mit den entsprechenden Katalogdateien verteilen, die diese Ordner darstellen.
Diese Informationen helfen bei der Überprüfung, ob seit der Erstellung des Katalogs Änderungen an den Ordnern vorgenommen wurden.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Die Katalogversionen 1 und 2 werden unterstützt.
Version 1 verwendet den SHA1-Hashalgorithmus, um Dateihashes zu erstellen, Version 2 verwendet SHA256.
Katalogversion 2 wird weder auf *Windows Server 2008 R2* noch auf *Windows 7* unterstützt.
Daher sollten Sie die Katalogversion 2 mit *Windows 8*, *Windows Server 2012* und späteren Betriebssystemen verwenden.

![](../images/NewFileCatalog.jpg)

Dadurch wird die Katalogdatei erstellt.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Melden Sie sich mit dem Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) an, um die Integrität der Katalogdatei zu überprüfen (im obigen Beispiel: „pester.cat“).

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

„Test-FileCatalog“ überprüft den Katalog, der einen Satz von Ordnern darstellt.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Dieses Cmdlet vergleicht alle Dateihashes und deren im *Katalog* enthaltenen relativen Pfade mit denen auf dem *Datenträger*.
Wenn das Cmdlet eine Unstimmigkeit zwischen den Dateihashes und den Pfaden entdeckt, gibt es den Status *ValidationFailed* zurück.
Benutzer können alle diese Informationen mithilfe des Parameters *-Detailed* abrufen.
Dieser Parameter zeigt in der Eigenschaft *Signature* auch den Signierstatus des Katalogs an, was dem Aufruf des Cmdlets [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) in der Katalogdatei entspricht.
Benutzer können außerdem jede Datei während der Überprüfung mithilfe des Parameters *-FilesToSkip* überspringen.

## <a name="module-analysis-cache"></a>Die Datei „ModuleAnalysisCache“

Ab Version 5.1 bietet PowerShell Kontrolle über die Datei, die zum Zwischenspeichern von Daten zu einem Modul verwendet wird, z. B. der Befehle, die es exportiert.

Standardmäßig wird dieser Cache in der Datei `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` gespeichert.
Der Cache wird in der Regel beim Start der Suche nach einem Befehl gelesen und einige Zeit nach dem Import des Moduls in einem Hintergrundthread geschrieben.

Um den Standardspeicherort des Caches zu ändern, legen Sie die Umgebungsvariable `$env:PSModuleAnalysisCachePath` vor dem Starten von PowerShell fest.
Änderungen an dieser Umgebungsvariablen betreffen nur untergeordnete Prozesse.
Der Wert muss einen vollständigen Pfad (samt Dateiname) definieren, in dem PowerShell die Berechtigung zum Erstellen und Schreiben von Dateien hat.
Zum Deaktivieren des Dateicaches kann dieser Wert auf einen ungültigen Speicherort festgelegt werden. Beispiel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermit wird der Pfad auf ein ungültiges Gerät festgelegt.
Wenn PowerShell nicht in den Pfad schreiben kann, wird keine Fehlermeldung zurückgegeben. Mithilfe eines Ablaufverfolgungstools können Sie jedoch einen Fehlerbericht anzeigen:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Bei der Ausgabe aus dem Cache sucht PowerShell nach Modulen, die nicht mehr vorhanden sind, um einen unnötig großen Cache zu vermeiden.
Mitunter sind diese Überprüfungen nicht wünschenswert, weshalb Sie sie deaktivieren können, indem Sie Folgendes festlegen:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Das Festlegen dieser Umgebungsvariablen wird im aktuellen Prozess sofort wirksam.

## <a name="specifying-module-version"></a>Angeben der Modulversion

In WMF 5.1 verhält sich `using module` genauso wie andere modulbezogene Konstruktionen in PowerShell.
Zuvor gab es keine Möglichkeit, eine bestimmte Modulversion anzugeben. Wenn mehrere Versionen vorhanden waren, führte dies zu einem Fehler.

In WMF 5.1:

- Sie können den [Konstruktor „ModuleSpecification“ (Hashtabelle)](https://msdn.microsoft.com/library/jj136290) verwenden.
Diese Hashtabelle hat das gleiche Format wie `Get-Module -FullyQualifiedName`.

**Beispiel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Wenn mehrere Versionen des Moduls vorhanden sind, verwendet PowerShell **dieselbe Auflösungslogik** wie `Import-Module` und gibt keinen Fehler zurück, was dem Verhalten von `Import-Module` und `Import-DscResource` entspricht.

## <a name="improvements-to-pester"></a>Verbesserungen an Pester

In WMF 5.1 wurde die in PowerShell mitgelieferte Pester-Version von 3.3.5 auf 3.4.0 aktualisiert und um die „commit“-Funktion https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e ergänzt, die die Funktionsweise von Pester auf Nano Server verbessert.

Überprüfen Sie die Veränderungen in Version 3.4.0 im Vergleich zu Version 3.3.5 durch Untersuchen der ChangeLog.md-Datei unter: https://github.com/pester/Pester/blob/master/CHANGELOG.md
