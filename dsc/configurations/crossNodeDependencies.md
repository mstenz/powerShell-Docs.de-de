---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Angeben knotenübergreifender Abhängigkeiten
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734675"
---
# <a name="specifying-cross-node-dependencies"></a>Angeben knotenübergreifender Abhängigkeiten

> Gilt für: Windows PowerShell 5.0

DSC bietet spezielle Ressourcen **WaitForAll**, **WaitForAny** und **WaitForSome**, die in Konfigurationen zum Angeben von Abhängigkeiten von Konfigurationen auf anderen Knoten verwendet werden können. Die Ressourcen verhalten sich wie folgt:

- **WaitForAll**: Ist erfolgreich, wenn die angegebene Ressource auf allen Zielknoten, die in der **NodeName**-Eigenschaft definiert sind, den gewünschten Zustand aufweist.
- **WaitForAny**: Ist erfolgreich, wenn die angegebene Ressource auf mindestens einem der Zielknoten, die in der **NodeName**-Eigenschaft definiert sind, den gewünschten Zustand aufweist.
- **WaitForSome**: Gibt zusätzlich zu einer **NodeName**-Eigenschaft eine **NodeCount**-Eigenschaft an. Die Ressource ist erfolgreich, wenn sich die Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die von der **NodeName**-Eigenschaft definiert sind, im gewünschten Zustand befindet.

## <a name="syntax"></a>Syntax

Die **WaitForAll**- und **WaitForAny**-Ressourcen verwenden die gleiche Syntax. Ersetzen Sie \<ResourceType\> im folgenden Beispiel durch **WaitForAny** oder durch **WaitForAll**.
Wie beim Schlüsselwort **DependsOn** müssen Sie den Namen als „[RessourcenTyp]RessourcenName“ formatieren. Wenn die Ressource zu einer separaten [Konfiguration](configurations.md) gehört, fügen Sie den **KonfigurationsNamen** in die formatierte Zeichenfolge „[RessourcenTyp]RessourcenName::[KonfigurationsName]::[KonfigurationsName]“ ein. Der **NodeName** ist der Computer oder Knoten, auf den die aktuelle Ressource warten soll.

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

Die Ressource **WaitForSome** hat eine ähnliche Syntax wie das Beispiel oben, fügt aber den Schlüssel **NodeCount** hinzu. Der **NodeCount** gibt an, auf wie viele Knoten die aktuelle Ressource warten soll.

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

Alle **WaitForXXXX**-Ressourcen verwenden die folgenden Syntaxschlüssel gemeinsam.

|Eigenschaft|  Beschreibung   |
|---------|---------------------|
| RetryIntervalSec| Die Anzahl von Sekunden bis zu einem Neuversuch. Der Mindestwert lautet 1.|
| RetryCount| Die maximal zulässige Anzahl von Neuversuchen.|
| ThrottleLimit| Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können. Die Standardeinstellung lautet `New-CimSession`.|
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Weitere Informationen finden Sie unter [DependsOn](resource-depends-on.md).|
| PsDscRunAsCredential | Informationen finden Sie unter [Verwenden von DSC mit Benutzeranmeldeinformationen](./runAsUser.md). |

## <a name="using-waitforxxxx-resources"></a>Verwenden von WaitForXXXX-Ressourcen

Jede **WaitForXXXX**-Ressource wartet darauf, dass die angegebenen Ressourcen auf dem angegebenen Knoten abgeschlossen werden.
Andere Ressourcen in derselben Konfiguration können dann von der **WaitForXXXX**-Ressource mit dem Schlüssel **DependsOn** als *abhängig* gekennzeichnet werden.

Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource **xADDomain** auf dem Knoten **MyDC** (bei einer maximalen Anzahl von 30 Wiederholungen in 15-Sekunden-Intervallen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.

Standardmäßig führen die **WaitForXXXX**-Ressourcen einen Versuch durch und verursachen dann einen Fehler. Auch wenn dies nicht erforderlich ist, sollten Sie in der Regel **RetryCount** sowie **RetryIntervalSec** angeben.

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

Wenn Sie die Konfiguration kompilieren, werden zwei MOF-Dateien generiert. Wenden Sie beide MOF-Dateien mit dem Cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) auf die Zielknoten an.

> [!NOTE]
> Die Ressource **WaitForXXX** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.
> Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="see-also"></a>Weitere Informationen

- [DSC-Konfigurationen](configurations.md)
- [Verwenden von Ressourcenabhängigkeiten](resource-depends-on.md)
- [DSC-Ressourcen](../resources/resources.md)
- [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md)
