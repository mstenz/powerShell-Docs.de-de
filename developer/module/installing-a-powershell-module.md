---
title: Installieren eines PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: f7899713dd273b793017adfa0a20b3ff3352b62a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862166"
---
# <a name="installing-a-powershell-module"></a>Installieren eines PowerShell-Moduls

Nachdem Sie Ihre PowerShell-Modul erstellt haben, möchten Sie wahrscheinlich das Modul auf einem System installieren, damit Sie oder andere Personen verwendet werden können. Im Allgemeinen besteht dies einfach die Moduldateien (z. B. die. psm1, oder die binäre Assembly, das modulmanifest und anderen zugehörigen Dateien) auf ein Verzeichnis auf diesem Computer kopieren. Für einen sehr kleinen Projekten kann dies so einfach wie das Kopieren und Einfügen von Dateien mit dem Windows-Explorer auf einem einzelnen Remotecomputer sein; Möglicherweise möchten Sie jedoch, für größere Lösungen einen komplexeren Installationsprozess verwenden. Unabhängig davon, wie Sie Ihr Modul auf dem System erhalten können PowerShell über eine Reihe von Techniken verwenden, mit denen Benutzer suchen und verwenden Ihre Module. (Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).) Aus diesem Grund ist das das größte Problem dar, für die Installation sicherstellen, dass PowerShell auf Ihrem Modul suchen kann.

Dieses Thema enthält die folgenden Abschnitte:

- Regeln für die Installation von Modulen

- Zur Installation von Modulen

- Installieren mehrerer Versionen eines Moduls

- Konflikte bei Befehlsnamen Behandlung

## <a name="rules-for-installing-modules"></a>Regeln für die Installation von Modulen

Die folgende Informationen bezieht sich auf alle Module, einschließlich Module, die Sie erstellen, für die eigene Verwendung, Module, die Sie von anderen Seiten zu erhalten und Module, die Sie an andere Benutzer verteilen.

### <a name="install-modules-in-psmodulepath"></a>Installieren Sie in der PSModulePath-Module

Wann immer möglich, installieren Sie alle Module in einen Pfad, der in aufgeführt ist die **PSModulePath** Umgebungsvariable oder Hinzufügen von der Modulpfad zu der **PSModulePath** umgebungsvariablenwert.

Die **PSModulePath** Umgebungsvariablen ($Env: PSModulePath) enthält die Speicherorte der Windows PowerShell-Module. Cmdlets basieren auf den Wert der diese Umgebungsvariable, um Module zu suchen.

In der Standardeinstellung die **PSModulePath** umgebungsvariablenwert enthält die folgenden und die Benutzerverzeichnisse-Modul, aber Sie können hinzufügen und bearbeiten Sie den Wert.

- $PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Dieser Speicherort ist für Module reserviert, die mit Windows ausgeliefert. Installieren Sie Module nicht an diesen Speicherort.

- $Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)

  Den Wert des abzurufenden der **PSModulePath** Umgebungsvariable, verwenden Sie eine der folgenden Befehle.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Wert von einem Modulpfad hinzuzufügende der **PSModulePath** Umgebungsvariable Wert können Sie das folgende Befehlsformat. Dieses Format wird verwendet die **SetEnvironmentVariable** Methode der **"System.Environment"** Klasse, um eine Sitzung unabhängige Änderung an der **PSModulePath** Umgebung Variable.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Nachdem Sie den Pfad zum hinzugefügt haben **PSModulePath**, sollten Sie eine Umgebung-Nachricht über die Änderung übertragen. Übertragen die Änderung kann andere Anwendungen, z. B. der Shell, um die Änderung zu übernehmen. Die Änderung gesendet wird, haben Sie Ihre Installation-Produktcode, die beim Senden einer **WM_SETTINGCHANGE** -Nachricht mit `lParam` auf die Zeichenfolge "Umgebung" festgelegt. Achten Sie darauf, dass Sie zum Senden der Nachricht, nachdem der Code für die Installation der Module aktualisiert hat **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Verwenden Sie den richtige Modul Verzeichnisnamen

Ein "wohlgeformte"-Modul ist ein Modul, das in einem Verzeichnis gespeichert ist, die den gleichen Namen wie der Basisname der mindestens eine Datei im Modulverzeichnis gespeichert wurde. Wenn ein Modul nicht wohlgeformt ist, werden Sie von Windows PowerShell nicht als Modul erkannt.

"Name der Basisname" eine Datei ist der Name ohne die Dateinamenerweiterung. In einem wohlgeformten-Modul muss der Namen des Verzeichnisses, das die Moduldateien enthält, der Basisname der mindestens eine Datei im Modul übereinstimmen.

Im Beispiel Fabrikam-Modul, beispielsweise das Verzeichnis, das die Moduldateien enthält, heißt "Fabrikam" und mindestens eine Datei wurde den Basisnamen "Fabrikam". In diesem Fall müssen sowohl für Fabrikam.psd1 Fabrikam.dll den Basisnamen "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Auswirkungen der falsche Installation

Wenn das Modul nicht ordnungsgemäß formatiert ist und der Speicherort sich nicht im Wert des befindet der **PSModulePath** Umgebungsvariable, grundlegende Suchfunktionen von Windows PowerShell, wie die folgende, funktionieren nicht.

- Das Modul Automatisches Laden von Feature kann nicht für das Modul automatisch importiert werden.

- Die `ListAvailable` Parameter, der die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet wurde das Modul nicht gefunden.

- Die [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet wurde das Modul nicht gefunden. Um das Modul zu importieren, müssen Sie den vollständigen Pfad zu der Stamm-Moduldatei oder modulmanifestdatei angeben.

  Zusätzliche Features wie die folgende, funktionieren nicht, es sei denn, das Modul in die Sitzung importiert wird. In wohlgeformte Module in der **PSModulePath** Umgebungsvariable, diese Features funktionieren, auch wenn das Modul nicht in die Sitzung importiert wird.

- Die [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet Befehle in das Modul nicht finden kann.

- Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlets kann nicht aktualisiert oder Speichern der Hilfe für das Modul.

- Die [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) Cmdlet kann nicht gefunden und die Befehle im Modul angezeigt.

  Die Befehle im Modul fehlen die `Show-Command` Fenster in Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Zur Installation von Modulen

In diesem Abschnitt wird erläutert, wo im Dateisystem Windows PowerShell-Module zu installieren. Der Speicherort hängt davon ab, wie das Modul verwendet wird.

### <a name="installing-modules-for-a-specific-user"></a>Installation von Modulen für einen bestimmten Benutzer

Wenn Sie Ihr eigenes Modul erstellen, oder fordern Sie ein Modul von einer anderen Partei, wie z. B. eine Windows PowerShell-Community-Website, und das Modul nur für Ihr Benutzerkonto verfügbar sein soll, installieren Sie das Modul in Ihrem Verzeichnis der benutzerspezifischen Module.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

Benutzerspezifische Modulverzeichnis wird hinzugefügt, auf den Wert des der **PSModulePath** Umgebungsvariable standardmäßig.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installation von Modulen für alle Benutzer in Program Files

Wenn Sie ein Modul für alle Benutzerkonten auf dem Computer verfügbar sein soll, installieren Sie das Modul in den Speicherort der Programmdateien an.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> Der Speicherort der Programmdateien wird standardmäßig in Windows PowerShell 4.0 und höher den Wert der PSModulePath-Umgebungsvariablen hinzugefügt. Informationen zu früheren Versionen von Windows PowerShell manuell die Programmdateien Speicherort ((%ProgramFiles%\WindowsPowerShell\Modules) erstellen und diesen Pfad der Umgebungsvariablen PSModulePath hinzufügen, wie oben beschrieben.

### <a name="installing-modules-in-a-product-directory"></a>Installation von Modulen in einem Produktverzeichnis

Wenn Sie das Modul an andere Parteien verteilen, verwenden Sie die oben beschriebenen Programmdateien Standardspeicherort, oder erstellen Sie Ihre eigenen unternehmensspezifischen oder produktspezifische Unterverzeichnis von Verzeichnis "% ProgramFiles%".

Z. B. wird Fabrikam Technologies, einem fiktiven Unternehmen, ein Windows PowerShell-Modul für die Fabrikam-Manager-Produkt ausgeliefert. Die Modul-Installationsprogramm erstellt ein Unterverzeichnis Module im Unterverzeichnis "Fabrikam-Manager-Produkt".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Um die Suchfunktionen von Windows PowerShell-Modul finden Sie das Fabrikam-Modul zu aktivieren, fügt der Fabrikam-Modulinstallation der Speicherort auf den Wert des der **PSModulePath** -Umgebungsvariablen angegeben.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technolgies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installieren von Modulen in das Verzeichnis für gemeinsame Dateien

Wenn ein Modul von mehreren Komponenten eines Produkts oder mehrere Versionen eines Produkts verwendet wird, installieren Sie das Modul in einem Unterverzeichnis modulspezifischen des Unterverzeichnisses Files\Modules %ProgramFiles%\Common.

Im folgenden Beispiel wird das Fabrikam-Modul in einem Unterverzeichnis Fabrikam des Unterverzeichnisses Files\Modules %ProgramFiles%\Common installiert. Beachten Sie, dass jedes Modul in ein eigenes Unterverzeichnis im Unterverzeichnis "Module" befindet.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Klicken Sie dann das Installationsprogramm den Wert des gewährleistet die **PSModulePath** Umgebungsvariable enthält den Pfad des Unterverzeichnisses Module gemeinsame Dateien.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Installieren mehrerer Versionen eines Moduls

Um mehrere Versionen desselben Moduls zu installieren, verwenden Sie das folgende Verfahren aus.

1. Erstellen Sie ein Verzeichnis für jede Version des Moduls an. Schließen Sie die Versionsnummer in den Namen des Verzeichnisses an.

2. Erstellen Sie ein modulmanifest für jede Version des Moduls an. In den Wert des der **"moduleversion"** -Schlüssel im Manifest, geben Sie die Versionsnummer des Moduls. Speichern Sie die Manifestdatei (psd1), in dem versionsspezifischen-Verzeichnis für das Modul.

3. Den Pfad des Stammordners Modul hinzufügen, auf den Wert des der **PSModulePath** Umgebungsvariablen wie in den folgenden Beispielen gezeigt.

Um eine bestimmte Version des Moduls zu importieren, können Sie der Endbenutzer die `MinimumVersion` oder `RequiredVersion` Parameter von der [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet.

Wenn das Fabrikam-Modul in Versionen 8.0 und 9.0 verfügbar ist, kann die Verzeichnisstruktur der Fabrikam-Modul z. B. folgendermaßen aussehen.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Das Installationsprogramm fügt beide die Modulpfade zu den **PSModulePath** umgebungsvariablenwert.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Nachdem diese Schritte abgeschlossen ist, sind die **ListAvailable** Parameter, der die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet wird sowohl der Fabrikam-Module. Um ein bestimmtes Modul zu importieren, verwenden die `MiminumVersion` oder `RequiredVersion` Parameter von der [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet.

Wenn beide Module sind in der gleichen Sitzung importiert, und die Module Cmdlets, mit dem gleichen Namen enthalten, gelten die Sitzung die Cmdlets, die zuletzt importiert werden.

## <a name="handling-command-name-conflicts"></a>Konflikte bei Befehlsnamen Behandlung

Konflikte bei Befehlsnamen können auftreten, wenn die Befehle, die ein Modul exportiert den gleichen Namen wie Befehle in der Sitzung des Benutzers verfügen.

Wenn eine Sitzung zwei Befehle, die den gleichen Namen haben enthält, führt Windows PowerShell den Befehlstyp, der Vorrang hat. Wenn eine Sitzung zwei Befehle, die den gleichen Namen und den gleichen Typ aufweisen enthält, führt Windows PowerShell den Befehl aus, der die der Sitzung zuletzt hinzugefügt wurde. Zum Ausführen eines Befehls, das nicht standardmäßig ausgeführt wird, können Benutzer den Namen des Befehls mit dem Modulnamen qualifizieren.

Wenn die Sitzung enthält z. B. eine `Get-Date` Funktion und die `Get-Date` Windows PowerShell-Cmdlet führt die Funktion standardmäßig. Stellen Sie den Befehl mit den Namen des Moduls, wie z. B. zum Ausführen des Cmdlets:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Modulautoren können um Namenskonflikte zu vermeiden, verwenden die **DefaultCommandPrefix** Schlüssel im modulmanifest an ein nomenpräfix für alle Befehle aus dem Modul exportiert.

Benutzer können die **Präfix** Parameter, der die `Import-Module` Cmdlet, um ein anderes Präfix verwenden. Der Wert des der **Präfix** Parameter hat Vorrang vor den Wert des der **DefaultCommandPrefix** Schlüssel.

## <a name="see-also"></a>Weitere Informationen

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
