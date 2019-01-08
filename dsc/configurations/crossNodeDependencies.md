---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Angeben knotenübergreifender Abhängigkeiten
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401163"
---
# <a name="specifying-cross-node-dependencies"></a>Angeben knotenübergreifender Abhängigkeiten

> Gilt für: Windows PowerShell 5.0

DSC bietet spezielle Ressourcen **WaitForAll**, **WaitForAny** und **WaitForSome**, die in Konfigurationen zum Angeben von Abhängigkeiten von Konfigurationen auf anderen Knoten verwendet werden können. Die Ressourcen verhalten sich wie folgt:

- **WaitForAll**: Ist erfolgreich, wenn die angegebene Ressource auf allen Zielknoten, die definiert, die den gewünschten Zustand der **NodeName** Eigenschaft.
- **WaitForAny**: Ist erfolgreich, wenn die angegebene Ressource auf mindestens einem der Zielknoten im gewünschten Zustand wird die **NodeName** Eigenschaft.
- **WaitForSome**: Gibt an, eine **NodeCount** Eigenschaft zusätzlich zu einem **NodeName** Eigenschaft. Die Ressource ist erfolgreich, wenn sich die Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die von der **NodeName**-Eigenschaft definiert sind, im gewünschten Zustand befindet.

## <a name="syntax"></a>Syntax

Die **WaitForAll** und **WaitForAny** Ressourcen freigeben, die gleiche Syntax. Ersetzen Sie dies \<ResourceType\> im folgenden Beispiel mit einem **WaitForAny** oder **WaitForAll**.
Wie die **"DependsOn"** -Schlüsselwort, Sie müssen den Namen wie "[ResourceType] ResourceName" zu formatieren. Wenn die Ressource, zu einem eigenen gehört [Konfiguration](configurations.md), enthalten die **ConfigurationName** in der formatierten Zeichenfolge "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]". Die **NodeName** wird vom Computer bzw. der Knoten, auf dem die aktuelle Ressource warten muss.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

Die **WaitForSome** Ressource verfügt über eine ähnliche Syntax im obigen Beispiel, jedoch fügt die **NodeCount** Schlüssel. Die **NodeCount** gibt an, wie viele Knoten, die die aktuelle Ressource sollte auf warten.

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

Alle **WaitForXXXX** Teilen Sie die folgende Syntax-Schlüssel.

|  Eigenschaft |  Beschreibung || RetryIntervalSec | Die Anzahl der Sekunden, bevor der Vorgang wird wiederholt. Der Mindestwert lautet 1. | | RetryCount | Die maximale Anzahl der Wiederholungsversuche. | | ThrottleLimit | Anzahl von Computern gleichzeitig eine Verbindung herstellen. Der Standardwert ist `New-CimSession` Standard. | | "DependsOn" | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist. Weitere Informationen finden Sie unter ["DependsOn"](resource-depends-on.md)|| "Psdscrunascredential" | Finden Sie unter [unter Verwendung von DSC mit Benutzeranmeldeinformationen](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Verwenden von WaitForXXXX-Ressourcen

Jede **WaitForXXXX** ressourcenwartevorgänge für die angegebenen Ressourcen auf dem angegebenen Knoten ausführen. Andere Ressourcen in der gleichen Konfiguration können Sie *hängen* der **WaitForXXXX** Ressource mit der **"DependsOn"** Schlüssel.

Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource **xADDomain** auf dem Knoten **MyDC** (bei einer maximalen Anzahl von 30 Wiederholungen in 15-Sekunden-Intervallen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Wenn Sie die Konfiguration kompilieren, werden zwei "MOF"-Dateien generiert. Sowohl "MOF"-Dateien anwenden, an die Zielknoten, die mit der [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet

>**Hinweis:** Standardmäßig ist die Waitforxxxx Ressourcen einen Versuch und schlägt fehl. Obwohl es nicht erforderlich ist, wird in der Regel angeben möchten einer **RetryCount** und **RetryIntervalSec**.

## <a name="see-also"></a>Weitere Informationen

- [DSC-Konfigurationen](configurations.md)
- [Verwenden Sie die Ressourcenabhängigkeiten](resource-depends-on.md)
- [DSC-Ressourcen](../resources/resources.md)
- [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md)
