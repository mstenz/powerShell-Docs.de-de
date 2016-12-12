---
title: "Anhang 1: Kompatibilitätsaliase"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: fc715f9ba2a1dc61d2549d5370371fe2b29fa063
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

