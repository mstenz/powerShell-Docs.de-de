---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: WaitForAll-Ressource in DSC
ms.openlocfilehash: 367f95caaa71ebec9c8e0a7c31fa5c0f5be27945
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226099"
---
# <a name="dsc-waitforall-resource"></a>WaitForAll-Ressource in DSC

> Gilt für: Windows PowerShell 5.0 und höher.

Die DSC-Ressource (Desired State Configuration) **WaitForAll** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.

Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf allen in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.


## <a name="syntax"></a>Syntax

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   |
|---|---|
| Ressourcenname| Der Ressourcenname für die Abhängigkeit. Wenn diese Ressource zu einer anderen Konfiguration gehört, müssen Sie den Namen als „[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]“ formatieren.|
| NodeName| Die Zielknoten der Ressource für die Abhängigkeit.|
| RetryIntervalSec| Die Anzahl von Sekunden bis zu einem Neuversuch. Der Mindestwert lautet 1.|
| RetryCount| Die maximal zulässige Anzahl von Neuversuchen.|
| ThrottleLimit| Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können. Per Voreinstellung wird der new-cimsession-Standardwert verwendet.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md).