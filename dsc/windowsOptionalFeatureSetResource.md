---
title: "DSC-Ressource „WindowsOptionalFeatureSet“"
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 1fab04dfcd4ce927bbe526b93c826cf3749a42a5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC-Ressource „WindowsOptionalFeatureSet“

> Gilt für: Windows PowerShell 5.0

Die Ressource **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass optionale Features auf einem Zielknoten aktiviert werden. Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [WindowsOptionalFeature](windowsOptionalFeatureResource.md) für jedes Feature aufruft, das in der `Name`-Eigenschaft angegeben ist.

Verwenden Sie diese Ressource, wenn Sie verschiedene optionale Windows-Features mit demselben Status konfigurieren möchten.

## <a name="syntax"></a>Syntax

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen der Features an, die aktiviert oder deaktiviert werden sollen.| 
| Ensure| Gibt an, ob die Features aktiviert sind. Um sicherzustellen, dass die Feature aktiviert sind, legen Sie diese Eigenschaft auf „Present“ fest. Um sicherzustellen, dass die Feature deaktiviert sind, legen Sie diese Eigenschaft auf „Absent“ fest.|
| Source| Nicht implementiert.|
| NoWindowsUpdateCheck| Gibt an, ob Windows Update (WU) von DISM kontaktiert wird, wenn die Quelldateien zum Aktivieren von Features gesucht werden. Falls „$true“, wird WU nicht von DISM kontaktiert.|
| RemoveFilesOnDisable| Legen Sie diese Einstellung auf **$true** fest, um alle zu den Features gehörigen Dateien zu entfernen, wenn sie deaktiviert werden (d. h. wenn **Ensure** auf „Absent“ festgelegt wird).|
| LogLevel| Die maximale Ausgabeebene, die in den Protokollen angezeigt wird. Die zulässigen Werte lauten: „ErrorsOnly“ (nur Fehler werden protokolliert), „ErrorsAndWarning“ (Fehler und Warnungen werden protokolliert) und „ErrorsAndWarningAndInformation“ (Fehler, Warnungen und Debuginformationen werden protokolliert).|
| LogPath| Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.| 
| DependsOn| Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
 



