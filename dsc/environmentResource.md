---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Resource „Environment“"
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="dsc-environment-resource" class="xliff"></a>
# DSC-Resource „Environment“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource __Environment__ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen.

<a id="syntax" class="xliff"></a>
## Syntax
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

<a id="properties" class="xliff"></a>
## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Ensure| Gibt an, ob eine Variable vorhanden ist. Legen Sie diese Eigenschaft auf __Present__ fest, um die Umgebungsvariable zu erstellen, falls sie noch nicht vorhanden ist, oder um sicherzustellen, dass ihr Wert der Angabe durch die __Value__-Eigenschaft entspricht, wenn die Variable bereits vorhanden ist. Legen Sie sie auf __Absent__ fest, um die Variable zu löschen, falls sie vorhanden ist.| 
| Path| Definiert die Umgebungsvariable, die konfiguriert wird. Legen Sie diese Eigenschaft auf __$true__ fest, wenn die Variable die __Path__-Variable ist. Legen Sie sie andernfalls auf __$false__ fest. Der Standardwert ist __$false__. Wenn die konfigurierte Variable die __Path__-Variable ist, wird der von der __Value__-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
| Value| Der Wert, der der Umgebungsvariablen zugewiesen werden soll.| 

<a id="example" class="xliff"></a>
## Beispiel

Im folgende Beispiel wird sichergestellt, dass __TestEnvironmentVariable__ vorhanden ist und den Wert __TestValue__ hat. Falls sie nicht vorhanden ist, wird sie erstellt.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

