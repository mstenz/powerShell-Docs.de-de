---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 343c296dad2a3df35f13393b3796a1d484f5f535
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="update-module"></a>Update-Module

Lädt die neueste Version der angegebenen Module aus einem Onlinekatalog auf den lokalen Computer herunter und installiert diese

## <a name="description"></a>Beschreibung

Das Cmdlet „Update-Module“ installiert eine neuere Version des Windows PowerShell-Moduls, das durch das Ausführen von „Install-Module“ aus dem Onlinekatalog auf dem lokalen Computer installiert wurde.

Standardmäßig wird die neueste Version des im Onlinekatalog verfügbaren angegebenen Moduls installiert, sofern Sie nicht eine erforderliche Version angeben. Sie können ein vorhandenes installiertes Modul aktualisieren, indem Sie den Namen des Moduls angeben. „Update-Module“ sucht nach „$env:PSModulePath“ für das zu aktualisierende Modul.

Durch das Ausführen von „Update-Module“ ohne den Name-Parameter werden alle Module aktualisiert, die auf dem lokalen Computer aktualisiert werden können.

### <a name="notes"></a>Hinweise

- Dieses Cmdlet wird unter Windows PowerShell 3.0 oder auf höheren Versionen von Windows PowerShell ausgeführt. Ebenso wird es unter Windows 7 oder Windows 2008 R2 und höheren Versionen von Windows ausgeführt.
- Wenn das Modul, das Sie mit dem Name-Parameter angeben, nicht mithilfe von „Install-Module“ installiert wurde, tritt ein Fehler auf. Sie können „Update-Module“ nur auf Modulen ausführen, die Sie durch Ausführen von „Install-Module“ aus dem Onlinekatalog installiert haben.
- Wenn „Update-Module“ versucht, Binärdateien zu aktualisieren, die gerade verwendet werden, gibt „Update-Module“ einen Fehler zurück, der die Problemprozesse identifiziert und den Benutzer nach Beenden der Prozesse darüber informiert, „Update-Module“ erneut auszuführen.
- Unter PowerShell 5.0 oder neueren Versionen fügt „Update-Module“ beim Aktualisieren eines Moduls die neueste (oder angegebene) Version des Moduls hinzu, damit sich die ältere und neuere Version nun im gleichen Verzeichnis befindet. Es wäre hilfreich, den Benutzer darauf hinzuweisen und ein Beispiel der Ausgabe dieser Befehle anzuzeigen.


## <a name="cmdlet-syntax"></a>Cmdlet-Syntax
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a>Beispiele für Befehle

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Aktualisieren Sie das Modul „TestDepWithNestedRequiredModules1“ mit Abhängigkeiten.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

