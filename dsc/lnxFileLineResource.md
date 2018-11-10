---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxFileLine“
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225589"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC für Linux-Resource „nxFileLine“

Die Ressource **nxFileLine** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Zeilen in einer Konfigurationsdatei auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft |  Beschreibung |
|---|---|
| FilePath| Der vollständige Pfad zu der Datei zum Verwalten von Zeilen auf dem Zielknoten.|
| ContainsLine| Eine Zeile, um sicherzustellen, dass sie in der Datei vorhanden ist. Diese Zeile wird an die Datei angefügt, wenn sie in der Datei nicht vorhanden ist. **ContainsLine** ist obligatorisch, kann jedoch auf eine leere Zeichenfolge (`ContainsLine = ""`) festgelegt werden, falls nicht benötigt.|
| DoesNotContainPattern| Muster eines regulären Ausdrucks für Zeilen, die in der Datei nicht vorhanden sein dürfen. Alle in der Datei vorhandenen Zeilen, die mit diesem regulären Ausdruck übereinstimmen, werden aus der Datei entfernt.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht die Verwendung der Ressource **nxFileLine** zum Konfigurieren der Datei `/etc/sudoers`, um sicherzustellen, dass der Benutzer „monuser“ nicht mit „requiretty“ konfiguriert ist.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```