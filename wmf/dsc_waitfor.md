# Angeben knotenübergreifender Abhängigkeiten

Mithilfe der integrierten Ressourcen des Typs „WaitFor*“ (WaitForAll, WaitForAny, WaitForSome) können Sie jetzt computerübergreifende Abhängigkeiten während der Ausführungen ohne externe Orchestrierung angeben. Das Verhalten der „WaitFor*“-Ressource ist wie folgt:

* **WaitForAll**: Wartet darauf, dass die angegebene Ressource auf *allen* Zielknoten, die in der „NodeName“-Eigenschaft angegeben sind, den gewünschten Zustand hat.
* **WaitForAny**: Wartet darauf, dass die angegebene Ressource auf *beliebigen* Zielknoten, die in der „NodeName“-Eigenschaft angegeben sind, den gewünschten Zustand hat.
* **WaitForSome**: Wartet darauf, dass die angegebene Ressource auf einer bestimmten Anzahl von Zielknoten, die in der „NodeName“-Eigenschaft angegeben sind, den gewünschten Zustand hat.

Diese Ressourcen ermöglichen eine Synchronisierung zwischen Knoten mithilfe von CIM-Verbindungen über das Protokoll „WS-Man“. Mithilfe dieser Ressourcen kann eine Konfiguration warten, bis sich der Zustand einer bestimmten Ressource eines anderen Computers geändert hat, ehe sie selbst fortgesetzt wird. 

Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource **xADDomain** auf dem Knoten **MyDC** (mit einigen Wiederholungen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

    WaitForAll DC
    {
        ResourceName      = '[xADDomain]NewDomain'
        NodeName          = 'MyDC'
        RetryIntervalSec  = 15
        RetryCount        = 30
    }

    xComputer JoinDomain
    {
        Name             = 'MyPC'
        DomainName       = 'Contoso.com'
        Credential       = (get-credential)
        DependsOn        ='[WaitForAll]DC'
    }
}
```
**Hinweis:** Standardmäßig haben die „WaitFor*“-Ressourcen nur einen Versuch, weshalb Sie, wenngleich nicht erforderlich, ein Intervall und eine Anzahl von Wiederholungen angeben sollten.
<!--HONumber=Mar16_HO2-->
