---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: f42eb0df101eb63a5dc267196fa9f666747b8e35
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83727794"
---
# <a name="installing-powershellget"></a>Installieren von PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:

- [Windows 10](https://www.microsoft.com/windows) oder höher
- [Windows Server 2016](/windows-server/windows-server) oder höher
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Herunterladen der neuesten Version aus dem PowerShell-Katalog

Bevor Sie **PowerShellGet** aktualisieren, sollten Sie immer den neuesten **NuGet**-Anbieter installieren. Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren

Zum Installieren von PowerShellGet führen Sie unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

Verwenden Sie `Update-Module`, um neuere Versionen zu beziehen.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>Computer mit PowerShell 3.0 oder PowerShell 4.0

Diese Anweisungen gelten für Computer, auf denen die **PackageManagement-Vorschauversion** oder keine Version von **PowerShellGet** installiert ist.

Das Cmdlet `Save-Module` wird in beiden Anweisungssätzen verwendet. `Save-Module` lädt ein Modul und alle Abhängigkeiten aus einem registrierten Repository herunter und speichert sie. Die neueste Version des Moduls wird in einem bestimmten Pfad auf dem lokalen Computer gespeichert, wird aber nicht installiert. Kopieren Sie die in Modulen gespeicherten Ordner in `$env:ProgramFiles\WindowsPowerShell\Modules`, um die Module in PowerShell 3.0 oder 4.0 zu installieren.

Weitere Informationen finden Sie unter [Save-Module](/powershell/module/PowershellGet/Save-Module).

> [!NOTE]
> PowerShell 3.0 und PowerShell 4.0 unterstützten nur eine Version eines Moduls Ab PowerShell 5.0 werden Module in `<modulename>\<version>` installiert. Dadurch können Sie mehrere Versionen nebeneinander installieren. Nachdem Sie das Modul mithilfe von `Save-Module` heruntergeladen haben, müssen Sie die Datei aus `<modulename>\<version>` in den Ordner `<modulename>` auf dem Zielcomputer kopieren.

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Computer mit installierter PackageManagement-Vorschauversion

1. Verwenden Sie `Save-Module` in einer PowerShell-Sitzung, um die Module in einem lokalen Verzeichnis zu speichern.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Stellen Sie sicher, dass die Module **PowerShellGet** und **PackageManagement** nicht in anderen Prozessen geladen sind.
1. Löschen Sie den Inhalt der Ordner „`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\`“ und „`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`“.
1. Öffnen Sie die PowerShell-Konsole erneut mit erhöhten Rechten, und führen Sie die folgenden Befehle aus.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>Computer ohne PowerShellGet

Für Computer ohne installierte Version von **PowerShellGet** wird zum Herunterladen der Module ein Computer benötigt, auf dem **PowerShellGet** installiert ist.

1. Verwenden Sie `Save-Module` auf dem Computer, auf dem **PowerShellGet** installiert ist, um die aktuelle Version von **PowerShellGet** herunterzuladen. Es werden zwei Ordner heruntergeladen: **PowerShellGet** und **PackageManagement**. Jeder Ordner enthält einen Unterordner mit einer Versionsnummer.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Kopieren Sie die Ordner **PowerShellGet** und **PackageManagement** auf den Computer ohne **PowerShellGet**-Installation.

   Das Zielverzeichnis lautet: `$env:ProgramFiles\WindowsPowerShell\Modules`
