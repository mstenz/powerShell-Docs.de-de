---
title: "DSC-Resource „Environment“"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4a51b56091aea23568674cdc7d4d4128c78b239c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-environment-resource"></a>DSC-Resource „Environment“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource __Environment__ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen.

## <a name="syntax"></a>Syntax
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Ensure| Gibt an, ob eine Variable vorhanden ist. Legen Sie diese Eigenschaft auf __Present__ fest, um die Umgebungsvariable zu erstellen, falls sie noch nicht vorhanden ist, oder um sicherzustellen, dass ihr Wert der Angabe durch die __Value__-Eigenschaft entspricht, wenn die Variable bereits vorhanden ist. Legen Sie sie auf __Absent__ fest, um die Variable zu löschen, falls sie vorhanden ist.| 
| Path| Definiert die Umgebungsvariable, die konfiguriert wird. Legen Sie diese Eigenschaft auf __$true__ fest, wenn die Variable die __Path__-Variable ist. Legen Sie sie andernfalls auf __$false__ fest. Der Standardwert ist __$false__. Wenn die konfigurierte Variable die __Path__-Variable ist, wird der von der __Value__-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
| Value| Der Wert, der der Umgebungsvariablen zugewiesen werden soll.| 

## <a name="example"></a>Beispiel

Im folgende Beispiel wird sichergestellt, dass __TestEnvironmentVariable__ vorhanden ist und den Wert __TestValue__ hat. Falls sie nicht vorhanden ist, wird sie erstellt.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

