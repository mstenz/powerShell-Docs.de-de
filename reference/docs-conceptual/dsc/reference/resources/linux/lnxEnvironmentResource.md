---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxEnvironment“
ms.openlocfilehash: 64de54fbde15f9d4d7fac425af27b6ef11347dce
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560894"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC für Linux-Resource „nxEnvironment“

Die Ressource **nxEnvironment** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|Name |Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten. |
|value |Der Wert, der der Umgebungsvariablen zugewiesen werden soll. |
|`Path` |Definiert die Umgebungsvariable, die konfiguriert wird. Legen Sie diese Eigenschaft auf `$true` fest, wenn die Variable die **Path**-Variable ist. Legen Sie sie andernfalls auf `$false` fest. Der Standardwert lautet `$false`. Wenn die konfigurierte Variable die **Path**-Variable ist, wird der von der **Value**-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Bestimmt, ob das Vorhandensein der Variablen geprüft werden soll. Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass die Variable vorhanden ist. Legen Sie sie auf **Absent** fest, um sicherzustellen, dass die Variable nicht vorhanden ist. Der Standardwert ist **Present**. |

## <a name="additional-information"></a>Zusätzliche Informationen

- Wenn **Path** fehlt oder auf `$false` festgelegt ist, werden Umgebungsvariablen in `/etc/environment` verwaltet.
  Ihre Programme oder Skripts erfordern möglicherweise das Konfigurieren des Abrufs der Datei `/etc/environment` für den Zugriff auf die verwalteten Umgebungsvariablen.
- Wenn **Path** auf `$true` festgelegt ist, wird die Umgebungsvariable in der Datei `/etc/profile.d/DSCenvironment.sh` verwaltet. Falls sie noch nicht vorhanden ist, wird die Datei erstellt. Wenn **Ensure** auf **Absent** und **Path** auf `$true` festgelegt ist, wird eine vorhandene Umgebungsvariable nur aus `/etc/profile.d/DSCenvironment.sh` und nicht aus anderen Dateien entfernt.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht das Verwenden der Ressource **nxEnvironment** zum Sicherstellen, dass **TestEnvironmentVariable** vorhanden ist und den Wert „Test-Value“ hat. Wenn **TestEnvironmentVariable** nicht vorhanden ist, wird die Variable erstellt.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
