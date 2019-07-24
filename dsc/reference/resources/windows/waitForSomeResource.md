---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: WaitForSome-Ressource in DSC
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726770"
---
# <a name="dsc-waitforsome-resource"></a>WaitForSome-Ressource in DSC

> Gilt für: Windows PowerShell 5.0 und höher

Die DSC-Ressource (Desired State Configuration) **WaitForSome** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](../../../configurations/configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.

Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die durch die Eigenschaft **NodeName** definiert sind, im gewünschten Zustand befindet.

> [!NOTE]
> Die Ressource **WaitForSome** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.
> Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="syntax"></a>Syntax

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   |
|---|---|
| NodeCount| Die Mindestanzahl von Knoten, die sich im gewünschten Zustand befinden muss, damit diese Ressource erfolgreich ist.|
| NodeName| Die Zielknoten der Ressource für die Abhängigkeit.|
| Ressourcenname| Der Ressourcenname für die Abhängigkeit. Wenn diese Ressource zu einer anderen Konfiguration gehört, müssen Sie den Namen als „[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]“ formatieren.|
| RetryIntervalSec| Die Anzahl von Sekunden bis zu einem Neuversuch. Der Mindestwert lautet 1.|
| RetryCount| Die maximal zulässige Anzahl von Neuversuchen.|
| ThrottleLimit| Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können. Per Voreinstellung wird der new-cimsession-Standardwert verwendet.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Informationen finden Sie unter [Verwenden von DSC mit Benutzeranmeldeinformationen](https://docs.microsoft.com/powershell/dsc/runasuser). |

## <a name="example"></a>Beispiel

Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](../../../configurations/crossNodeDependencies.md).
