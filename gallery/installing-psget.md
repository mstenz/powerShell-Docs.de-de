---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: 35be7d02ea856ea39218f05d32b43c60fa1bd53e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219350"
---
# <a name="installing-powershellget"></a>Installieren von PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:

- [Windows 10](https://www.microsoft.com/windows/get-windows-10) oder höher
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) oder höher
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Abrufen des PowerShellGet-Moduls für PowerShell 3.0 und 4.0

- [PackageManagement-MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Herunterladen der neuesten Version aus dem PowerShell-Katalog

- Bevor Sie PowerShellGet aktualisieren, sollten Sie immer den neuesten NuGet-Anbieter installieren. Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren

- Führen Sie hierzu unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Verwenden Sie „Update-Module“, um neuere Version abzurufen.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>Systeme mit PowerShell 3 oder PowerShell 4 mit installierter [PackageManagement-MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Verwenden Sie das nachstehende PowerShellGet-Cmdlet aus einer PowerShell-Sitzung mit erhöhten Rechten, um die Module in einem lokalen Verzeichnis zu speichern.

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Stellen Sie sicher, dass die PowerShellGet- und PackageManagment-Module nicht in anderen Prozessen geladen sind.
- Löschen Sie die Inhalte der Ordner `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` und `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
- Öffnen Sie die PS-Konsole erneut mit erhöhten Rechten, und führen Sie dann die folgenden Befehle aus.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```