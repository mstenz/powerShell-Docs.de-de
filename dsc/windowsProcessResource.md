---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsProcess“
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187026"
---
# <a name="dsc-windowsprocess-resource"></a>DSC-Ressource „WindowsProcess“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **WindowsProcess** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.

## <a name="syntax"></a>Syntax

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Eigenschaften
|  Eigenschaft  |  Beschreibung   |
|---|---|
| Argumente| Gibt eine Zeichenfolge von Argumenten an, die wie vorhanden an den Prozess übergeben wird. Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.|
| Pfad| Der Pfad zur ausführbaren Prozessdatei. Wenn es sich um den Namen der ausführbaren Datei (keinen vollqualifizierten Pfad) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable **Path** (`$env:Path`), um die ausführbare Datei zu ermitteln. Wenn der Werte dieser Eigenschaft ein vollqualifizierter Pfad ist, verwendet DSC nicht die Umgebungsvariable **Path**, um die Dateien zu finden, und löst einen Fehler aus, wenn der Pfad nicht vorhanden ist. Relative Pfade sind nicht zulässig.|
| Credential| Gibt die Anmeldeinformationen zum Starten des Prozesses an.|
| Ensure| Gibt an, ob der Prozess vorhanden ist. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist. Legen Sie sie andernfalls auf „Absent“ fest. Die Standardeinstellung ist „Present“.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.|
| StandardErrorPath| Gibt den Verzeichnispfad an, in den der Standardfehler geschrieben wird. Eine vorhandene Datei wird überschrieben.|
| StandardInputPath| Gibt den Standardpfad für die Eingabe an.|
| StandardOutputPath| Gibt den Speicherort an, in den die Standardausgabe geschrieben wird. Eine vorhandene Datei wird überschrieben.|
| WorkingDirectory| Gibt den Speicherort an, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.|