---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC für Linux-Resource „nxGroup“"
ms.openlocfilehash: bc01f6ae5ed61aff63958fe55f30d82f9b81b2b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC für Linux-Resource „nxGroup“

Die Ressource **nxGroup** in PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| GroupName| Gibt den Namen der Gruppe an, für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Ensure| Bestimmt, ob das Vorhandensein der Gruppe geprüft werden soll. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass die Gruppe vorhanden ist. Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass die Gruppe nicht vorhanden ist. Der Standardwert ist „Present“.| 
| Members| Gibt die Mitglieder an, die die Gruppe bilden.| 
| MembersToInclude| Gibt die Benutzer an, die Mitglied dieser Gruppe werden sollen.| 
| MembersToExclude| Gibt die Benutzer an, die nicht Mitglied dieser Gruppe werden sollen.| 
| PreferredGroupID| Legt nach Möglichkeit die Gruppen-ID auf den angegebenen Wert fest. Wenn die Gruppen-ID derzeit verwendet wird, wird die nächste verfügbare Gruppen-ID verwendet.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird sichergestellt, dass der Benutzer „monuser“ vorhanden und Mitglied der Gruppe „DBusers“ ist.

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

