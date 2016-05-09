---
title: Anhang 1: Kompatibilitätsaliase
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
---
# Anhang 1: Kompatibilitätsaliase
Windows PowerShell hat mehrere Übergangsaliase, die es UNIX- und Cmd-Benutzern ermöglichen, vertraut Befehlsnamen in Windows PowerShell zu verwenden. Die am häufigsten verwendeten Aliase sind in der folgenden Tabelle zusammengestellt. Außerdem sind die Windows PowerShell-Befehle, die zu den Aliasen gehören, sowie die standardmäßigen Windows PowerShell-Aliase (sofern vorhanden) aufgeführt.

Sie können den Windows PowerShell-Befehl, auf den ein Alias verweist, in Windows PowerShell mit dem Cmdlet „Get-Alias“ ermitteln. Geben Sie z. B. **get-alias cls** ein.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD-Befehl|UNIX-Befehl|PS-Befehl|PS-Alias|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-ChildItem**|**gci**|
|**cls**|**clear**|**Clear-Host** (Funktion)|Nicht zutreffend|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**copy**|**cp**|**Copy-Item**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**rename**|**mv**|**Rename-Item**|**rni**|
|**Typ**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Set-Location**|**sl**|
|**md**|**mkdir**|**New-Item**|**ni**|
|Nicht zutreffend|**pushd**|**Push-Location**|Nicht zutreffend|
|Nicht zutreffend|**popd**|**Pop-Location**|Nicht zutreffend|



<!--HONumber=Apr16_HO1-->


