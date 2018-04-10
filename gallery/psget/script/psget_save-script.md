---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a>Save-Script

Mit dem Cmdlet „Save-Script“ können Sie die Skriptdatei überprüfen, indem Sie sie an einem angegebenen Speicherort speichern.

## <a name="description"></a>Beschreibung

Das Cmdlet „Save-Script“ speichert das angegebene Skript.

## <a name="cmdlet-syntax"></a>Cmdlet-Syntax

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Beispiele für Befehle

### <a name="example-1-save-a-script-from-a-repository"></a>Beispiel 1: Speichern eines Skripts aus einem Repository
Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Beispiel 2: Speichern einer Version eines Skripts durch Weiterreichen vom Cmdlet „Find-Script“

Der erste Befehl sucht nach Version 1.5 von „Fabrikam-ClientScript“ vom Repository „GalleryINT“ und speichert sie im Ordner „C:\ScriptSharingDemo“.

Der zweite Befehl überprüft die Metadaten des gespeicherten Skripts.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>Beispiel 3: Speichern einer Vorabversion eines Skripts aus einem Repository
Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```