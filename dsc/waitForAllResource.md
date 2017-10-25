---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: WaitForAll-Ressource in DSC
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a>WaitForAll-Ressource in DSC

> Gilt für: Windows PowerShell 5.0 und höher.

Die DSC-Ressource (Desired State Configuration) **WaitForAll** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.

Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf allen der in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.


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
| Ressourcenname| Der Ressourcenname für die Abhängigkeit.| 
| NodeName| Die Zielknoten der Ressource für die Abhängigkeit.| 
| RetryIntervalSec| Die Anzahl von Sekunden bis zu einem Neuversuch. Der Mindestwert lautet 1.| 
| RetryCount| Die maximal zulässige Anzahl von Neuversuchen.| 
| ThrottleLimit| Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können. Per Voreinstellung wird der new-cimsession-Standardwert verwendet.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md).

