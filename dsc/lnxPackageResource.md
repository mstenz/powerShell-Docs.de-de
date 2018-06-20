---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxPackage“
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218704"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC für Linux-Resource „nxPackage“

Die Ressource **nxPackage** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Paketen auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft |  Beschreibung |
|---|---|
| Name| Der Name des Pakets, für das Sie einen bestimmten Zustand sicherstellen möchten.|
| Ensure| Bestimmt, ob das Vorhandensein des Pakets geprüft werden soll. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass das Paket vorhanden ist. Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass das Paket nicht vorhanden ist. Der Standardwert ist „Present“.|
| PackageManager| Unterstützte Werte sind „yum“, „apt“ und „zypper“. Gibt den Paket-Manager an, der zum Installieren von Paketen verwendet werden soll. Wenn **FilePath** angegeben ist, dient der angegebene Pfad zum Installieren des Pakets. Andernfalls wird ein Paket-Manager zum Installieren des Pakets aus einem vorkonfigurierten Repository verwendet. Wenn weder **PackageManager** noch **FilePath** angegeben ist, wird der standardmäßige Paket-Manager für das System verwendet.|
| FilePath| Der Dateipfad, in dem das Paket gespeichert ist.|
| PackageGroup| Falls **$true**, soll **Name** dem Namen einer Paketgruppe für die Verwendung mit einem **PackageManager** entsprechen. **PackageGroup** ist ungültig, wenn **FilePath** angegeben wird.|
| Arguments| Eine Zeichenfolge mit Argumenten, die exakt wie angegeben an das Paket übergeben wird.|
| ReturnCode| Der erwartete Rückgabecode. Wenn der tatsächliche Rückgabecode nicht dem erwarteten Wert entspricht, gibt die Konfiguration einen Fehler zurück.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Beispiel

Im folgende Beispiel wird sichergestellt, dass das Paket mit dem Namen „httpd“ mit dem Paket-Manager „Yum“ auf einem Linux-Computer installiert wird.

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```