---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Anhang 1 – Kompatibilitätsaliase
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030328"
---
# <a name="appendix-1---compatibility-aliases"></a>Anhang 1: Kompatibilitätsaliase

Windows PowerShell hat mehrere Übergangsaliase, die es UNIX- und Cmd-Benutzern ermöglichen, vertraut Befehlsnamen in Windows PowerShell zu verwenden. Die am häufigsten verwendeten Aliase sind in der folgenden Tabelle zusammengestellt. Außerdem sind die Windows PowerShell-Befehle, die zu den Aliasen gehören, sowie die standardmäßigen Windows PowerShell-Aliase (sofern vorhanden) aufgeführt.

Sie können den Windows PowerShell-Befehl, auf den ein Alias verweist, in Windows PowerShell mit dem Cmdlet „Get-Alias“ ermitteln. Geben Sie z.B. **get-alias cls** ein.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD-Befehl|UNIX-Befehl|PS-Befehl|PS-Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (Funktion)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**type**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|**pushd**|**pushd**|**Push-Location**|**pushd**|
|**popd**|**popd**|**Pop-Location**|**popd**|
