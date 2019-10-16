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
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367069"
---
# <a name="installing-a-powershell-module"></a>Installieren eines PowerShell-Moduls

Nachdem Sie das PowerShell-Modul erstellt haben, möchten Sie das Modul wahrscheinlich auf einem System installieren, damit Sie von Ihnen oder anderen Benutzern verwendet werden können. Im Allgemeinen besteht dies darin, die Moduldateien (d. psm1. die binäre Assembly, das Modul Manifest und alle zugehörigen Dateien) in ein Verzeichnis auf diesem Computer zu kopieren. Bei einem sehr kleinen Projekt kann dies so einfach sein wie das Kopieren und Einfügen der Dateien mit Windows-Explorer auf einem einzelnen Remote Computer. bei größeren Lösungen möchten Sie jedoch möglicherweise einen komplexeren Installationsprozess verwenden. Unabhängig davon, wie Sie Ihr Modul auf das System übernehmen, kann PowerShell eine Reihe von Techniken verwenden, mit denen Benutzer Ihre Module suchen und verwenden können. Das Hauptproblem bei der Installation besteht daher darin, sicherzustellen, dass PowerShell das Modul finden kann. Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).

## <a name="rules-for-installing-modules"></a>Regeln für die Installation von Modulen

Die folgenden Informationen beziehen sich auf alle Module, einschließlich der Module, die Sie für Ihre eigene Verwendung erstellen, der Module, die Sie von anderen Anbietern erhalten, sowie von Modulen, die Sie an andere Benutzer verteilen.

### <a name="install-modules-in-psmodulepath"></a>Installieren von Modulen in psmodulepath

Installieren Sie nach Möglichkeit alle Module in einem Pfad, der in der **psmodulepath** -Umgebungsvariablen aufgelistet ist, oder fügen Sie den Modulpfad dem Wert der Umgebungsvariablen **psmodulepath** hinzu.

Die **psmodulepath** -Umgebungsvariable ($env:P smodulepath) enthält die Speicherorte von Windows PowerShell-Modulen. Die Cmdlets basieren auf dem Wert dieser Umgebungsvariablen, um Module zu suchen.

Standardmäßig enthält der Wert der Umgebungsvariablen **psmodulepath** die folgenden System-und Benutzermodul Verzeichnisse, aber Sie können den Wert hinzufügen und bearbeiten.

- `$PSHome\Modules` (%windir%\system32\WindowsPowerShell\v1.0\modules)

  > [!WARNING]
  > Dieser Speicherort ist für Module reserviert, die mit Windows ausgeliefert werden. Installieren Sie keine Module an diesem Speicherort.

- `$Home\Documents\WindowsPowerShell\Modules` (%USERPROFILE%\documents\windowspowershell\modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\windowspowershell\modules)

  Um den Wert der **psmodulepath** -Umgebungsvariablen abzurufen, verwenden Sie einen der folgenden Befehle.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Verwenden Sie das folgende Befehls Format, um dem Wert des Umgebungsvariablen Werts **psmodulepath** einen Modulpfad hinzuzufügen. Dieses Format verwendet die Methode "* **tenvironmentvariable** " der Klasse " **System. Environment** ", um eine Sitzungs unabhängige Änderung an der **psmodulepath** -Umgebungsvariablen vorzunehmen.

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Nachdem Sie den Pfad zu **psmodulepath**hinzugefügt haben, sollten Sie eine Umgebungs Meldung über die Änderung übertragen. Durch das Senden der Änderung können andere Anwendungen, wie z. b. die Shell, die Änderung übernehmen. Um die Änderung zu übertragen, lassen Sie Ihren Produkt Installationscode eine **WM_SETTINGCHANGE** -Nachricht senden, wobei `lParam` auf die Zeichenfolge "Environment" festgelegt ist. Stellen Sie sicher, dass Sie die Nachricht senden, nachdem der Installationscode des Moduls " **psmodulepath**" aktualisiert hat.

### <a name="use-the-correct-module-directory-name"></a>Richtigen Modul Verzeichnisnamen verwenden

Ein wohl geformtes Modul ist ein Modul, das in einem Verzeichnis gespeichert ist, das denselben Namen wie der Basis Name mindestens einer Datei im Modul Verzeichnis hat. Wenn ein Modul nicht wohl geformt ist, wird es von Windows PowerShell nicht als Modul erkannt.

Der "Basisname" einer Datei ist der Name ohne die Dateinamenerweiterung. In einem wohlgeformten Modul muss der Name des Verzeichnisses, das die Moduldateien enthält, mit dem Basis Namen von mindestens einer Datei im Modul identisch sein.

Beispielsweise heißt das Verzeichnis im Fabrikam-Beispielmodul, das die Moduldateien enthält, den Namen Fabrikam, und mindestens eine Datei hat den Basisnamen "Fabrikam". In diesem Fall haben sowohl "fabrikam. psd1" als auch "fabrikam. dll" den Basisnamen "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Auswirkungen falscher Installation

Wenn das Modul nicht wohl geformt ist und sein Speicherort nicht im Wert der **psmodulepath** -Umgebungsvariablen enthalten ist, funktionieren die grundlegenden Ermittlungs Features von Windows PowerShell, wie z. b. die folgenden, nicht.

- Die Funktion zum automatischen Laden von Modulen kann das Modul nicht automatisch importieren.

- Der Parameter "`ListAvailable`" des Cmdlets " [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) " kann das Modul nicht finden.

- Das [Import-Module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet kann das Modul nicht finden. Zum Importieren des Moduls müssen Sie den vollständigen Pfad zur Stamm Modul Datei oder zur Modul Manifest-Datei angeben.

  Weitere Funktionen, wie z. b. die folgenden, funktionieren nicht, es sei denn, das Modul wird in die Sitzung importiert. In wohlgeformten Modulen in der **psmodulepath** -Umgebungsvariablen funktionieren diese Features auch dann, wenn das Modul nicht in die Sitzung importiert wird.

- Das [Get-Command-](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet kann Befehle im Modul nicht finden.

- Die Cmdlets " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " und " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " können die Hilfe für das Modul nicht aktualisieren oder speichern.

- Das Cmdlet " [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) " kann die Befehle im Modul nicht finden und anzeigen.

  Die Befehle im Modul fehlen im Fenster "`Show-Command`" in Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Installationsort von Modulen

In diesem Abschnitt wird erläutert, wo im Dateisystem Windows PowerShell-Module installiert werden. Der Speicherort hängt davon ab, wie das Modul verwendet wird.

### <a name="installing-modules-for-a-specific-user"></a>Installieren von Modulen für einen bestimmten Benutzer

Wenn Sie ein eigenes Modul erstellen oder ein Modul von einer anderen Partei (z. b. eine Windows PowerShell-Communitywebsite) erstellen möchten, und Sie möchten, dass das Modul nur für Ihr Benutzerkonto verfügbar ist, installieren Sie das Modul in Ihrem benutzerspezifischen Modul Verzeichnis.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

Das Verzeichnis für benutzerspezifische Module wird standardmäßig dem Wert der **psmodulepath** -Umgebungsvariablen hinzugefügt.

### <a name="installing-modules-for-all-users-in-program-files"></a>Installieren von Modulen für alle Benutzer in Programmdateien

Wenn Sie möchten, dass ein Modul für alle Benutzerkonten auf dem Computer verfügbar ist, installieren Sie das Modul im Speicherort der Programmdateien.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> Der Speicherort der Programmdateien wird standardmäßig in Windows PowerShell 4,0 und höher dem Wert der Umgebungsvariablen psmodulepath hinzugefügt. Bei früheren Versionen von Windows PowerShell können Sie den Speicherort der Programmdateien ((%ProgramFiles%\windowspowershell\modules) manuell erstellen und diesen Pfad der Umgebungsvariablen psmodulepath hinzufügen, wie oben beschrieben.

### <a name="installing-modules-in-a-product-directory"></a>Installieren von Modulen in einem Produktverzeichnis

Wenn Sie das Modul an andere Parteien verteilen, verwenden Sie den oben beschriebenen Standard Speicherort für Programmdateien, oder erstellen Sie ein eigenes unternehmensspezifisches oder produktspezifisches Unterverzeichnis des Verzeichnisses "% Program Files%".

Beispielsweise wird von Fabrikam Technologies, einem fiktiven Unternehmen, ein Windows PowerShell-Modul für das Fabrikam Manager-Produkt versendet. Der modulinstallerinstaller erstellt im Unterverzeichnis "Fabrikam Manager Product" ein Unterverzeichnis "modules".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Zum Aktivieren der Ermittlungs Funktionen des Windows PowerShell-Moduls für die Suche nach dem Modul "Fabrikam" fügt das Installationsprogramm des Fabrikam-Moduls den Speicherort des Moduls dem Wert der **psmodulepath** -Umgebungsvariablen hinzu.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Installieren von Modulen im Verzeichnis "gemeinsame Dateien"

Wenn ein Modul von mehreren Komponenten eines Produkts oder von mehreren Produktversionen verwendet wird, installieren Sie das Modul in einem modulspezifischen Unterverzeichnis des Unterverzeichnisses "%ProgramFiles%\Common files\modules".

Im folgenden Beispiel wird das Modul "Fabrikam" in einem Unterverzeichnis "Fabrikam" des Unterverzeichnisses "`%ProgramFiles%\Common Files\Modules`" installiert. Beachten Sie, dass sich jedes Modul in einem eigenen Unterverzeichnis im Unterverzeichnis "modules" befindet.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Das Installationsprogramm stellt dann sicher, dass der Wert der **psmodulepath** -Umgebungsvariablen den Pfad des Unterverzeichnisses der allgemeinen Datei Module enthält.

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

Wenn Sie mehrere Versionen desselben Moduls installieren möchten, verwenden Sie das folgende Verfahren.

1. Erstellen Sie ein Verzeichnis für jede Version des Moduls. Fügen Sie die Versionsnummer in den Verzeichnisnamen ein.
2. Erstellen Sie ein Modul Manifest für jede Version des Moduls. Geben Sie im Manifest im Wert des **moduleversion** -Schlüssels die Modulversionsnummer ein. Speichern Sie die Manifest-Datei (. psd1) im Versions spezifischen Verzeichnis für das Modul.
3. Fügen Sie den Pfad des Modul Stamm Ordners zum Wert der **psmodulepath** -Umgebungsvariablen hinzu, wie in den folgenden Beispielen gezeigt.

Um eine bestimmte Version des Moduls zu importieren, kann der Endbenutzer die `MinimumVersion`-oder `RequiredVersion`-Parameter des [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Cmdlets verwenden.

Wenn das Modul Fabrikam beispielsweise in den Versionen 8,0 und 9,0 verfügbar ist, könnte die Fabrikam-Modul Verzeichnisstruktur wie folgt aussehen.

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

Das Installationsprogramm fügt dem Wert der Umgebungsvariablen **psmodulepath** beide Modul Pfade hinzu.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Wenn diese Schritte ausgeführt werden, ruft der **listavailable** -Parameter des [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlets beide Fabrikam-Module ab. Um ein bestimmtes Modul zu importieren, verwenden Sie die Parameter "`MinimumVersion`" oder "`RequiredVersion`" des Cmdlets " [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ".

Wenn beide Module in dieselbe Sitzung importiert werden und die Module Cmdlets mit denselben Namen enthalten, sind die zuletzt importierten Cmdlets in der Sitzung gültig.

## <a name="handling-command-name-conflicts"></a>Behandeln von Befehlsnamen Konflikten

Konflikte mit Befehlsnamen können auftreten, wenn die Befehle, die ein Modul exportiert, denselben Namen wie die Befehle in der Benutzersitzung haben.

Wenn eine Sitzung zwei Befehle mit demselben Namen enthält, führt Windows PowerShell den Befehlstyp aus, der Vorrang hat. Wenn eine Sitzung zwei Befehle mit demselben Namen und demselben Typ enthält, führt Windows PowerShell den Befehl aus, der der Sitzung zuletzt hinzugefügt wurde. Um einen Befehl auszuführen, der nicht standardmäßig ausgeführt wird, können Benutzer den Befehlsnamen mit dem Modulnamen qualifizieren.

Wenn die Sitzung z. b. eine `Get-Date`-Funktion und das `Get-Date`-Cmdlet enthält, führt Windows PowerShell die Funktion standardmäßig aus. Um das Cmdlet auszuführen, stellen Sie dem Befehl den Namen des Moduls voran, z. b.:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Um Namenskonflikte zu verhindern, können Modul Autoren den **defaultcommandprefix** -Schlüssel im Modul Manifest verwenden, um ein Substantiv-Präfix für alle Befehle anzugeben, die vom Modul exportiert werden.

Benutzer können den **prefix** -Parameter des `Import-Module`-Cmdlets verwenden, um ein alternatives Präfix zu verwenden. Der Wert des **prefix** -Parameters hat Vorrang vor dem Wert des **defaultcommandprefix** -Schlüssels.

## <a name="see-also"></a>Weitere Informationen

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Schreiben eines Windows PowerShell-Moduls](./writing-a-windows-powershell-module.md)
