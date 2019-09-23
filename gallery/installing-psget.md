---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143590"
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

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>Systeme mit PowerShell 3 oder PowerShell 4 mit installierter PackageManagement-Vorschau

1. Verwenden Sie `Save-Module` in einer PowerShell-Sitzung mit erhöhten Rechten, um die Module in einem lokalen Verzeichnis zu speichern.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. Stellen Sie sicher, dass die Module **PowerShellGet** und **PackageManagement** nicht in anderen Prozessen geladen sind.
1. Löschen Sie den Inhalt der Ordner „`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\`“ und „`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`“.
1. Öffnen Sie die PowerShell-Konsole erneut mit erhöhten Rechten, und führen Sie die folgenden Befehle aus.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
