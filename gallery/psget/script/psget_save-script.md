---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="save-script" class="xliff"></a>
# Save-Script

Mit dem Cmdlet „Save-Script“ können Sie die Skriptdatei überprüfen, indem Sie sie an einem angegebenen Speicherort speichern.

<a id="description" class="xliff"></a>
## Beschreibung

Das Cmdlet „Save-Script“ speichert das angegebene Skript.

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet-Syntax

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet-Onlinehilfe

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

<a id="example-commands" class="xliff"></a>
## Beispiele für Befehle

<a id="example-1-save-a-script-from-a-repository" class="xliff"></a>
### Beispiel 1: Speichern eines Skripts aus einem Repository
Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

<a id="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet" class="xliff"></a>
### Beispiel 2: Speichern einer Version eines Skripts durch Weiterreichen vom Cmdlet „Find-Script“

Der erste Befehl sucht nach Version 1.5 von „Fabrikam-ClientScript“ vom Repository „GalleryINT“ und speichert sie im Ordner „C:\ScriptSharingDemo“.

Der zweite Befehl überprüft die Metadaten des gespeicherten Skripts.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

