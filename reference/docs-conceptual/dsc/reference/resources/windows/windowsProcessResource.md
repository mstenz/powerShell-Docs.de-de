---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsProcess“
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952837"
---
# <a name="dsc-windowsprocess-resource"></a>DSC-Ressource „WindowsProcess“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x

Die Ressource **WindowsProcess** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.

## <a name="syntax"></a>Syntax

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |Beschreibung |
|---|---|
|Argumente |Gibt eine Zeichenfolge von Argumenten an, die wie vorhanden an den Prozess übergeben wird. Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu. |
|Pfad |Der Pfad zur ausführbaren Prozessdatei. Wenn es sich um den Namen der ausführbaren Datei (keinen vollqualifizierten Pfad) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable `$env:Path`, um die ausführbare Datei zu ermitteln. Wenn der Werte dieser Eigenschaft ein vollqualifizierter Pfad ist, verwendet DSC nicht die Umgebungsvariable `$env:Path`, um die Dateien zu finden, und löst einen Fehler aus, wenn der Pfad nicht vorhanden ist. Relative Pfade sind nicht zulässig. |
|Credential |Gibt die Anmeldeinformationen zum Starten des Prozesses an. |
|StandardErrorPath |Gibt den Verzeichnispfad an, in den der Standardfehler geschrieben wird. Eine vorhandene Datei wird überschrieben. |
|StandardInputPath |Gibt den Standardpfad für die Eingabe an. |
|StandardOutputPath |Gibt den Speicherort an, in den die Standardausgabe geschrieben wird. Eine vorhandene Datei wird überschrieben. |
|WorkingDirectory |Gibt den Speicherort an, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |Beschreibung |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Gibt an, ob der Prozess vorhanden ist. Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass der Prozess vorhanden ist. Legen Sie sie andernfalls auf **Absent** fest. Der Standardwert ist **Present**. |
|PsDscRunAsCredential |Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest. |