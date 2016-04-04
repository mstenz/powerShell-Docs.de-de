# Angeben knotenübergreifender Abhängigkeiten

Mithilfe der integrierten Ressourcen des Typs „WaitFor*“ (WaitForAll, WaitForAny, WaitForSome) können Sie jetzt computerübergreifende Abhängigkeiten während der Ausführungen ohne externe Orchestrierung angeben. Das Verhalten der „WaitFor*“-Ressource ist wie folgt:

* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAll</ctype="x-NOTFOUND">: Wartet darauf, dass die angegebene Ressource auf <ctype="x-NOTFOUND" mdpre="*" mdpost="*">allen</ctype="x-NOTFOUND"> Zielknoten, die in der „NodeName“-Eigenschaft angegeben sind, den gewünschten Zustand hat.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForAny</ctype="x-NOTFOUND">: Wartet darauf, dass die angegebene Ressource auf <ctype="x-NOTFOUND" mdpre="*" mdpost="*">beliebigen</ctype="x-NOTFOUND"> Zielknoten, die in der „NodeName“-Eigenschaft angegeben sind, den gewünschten Zustand hat.
* <ctype="x-NOTFOUND" mdpre="**" mdpost="**">WaitForSome</ctype="x-NOTFOUND">: Wartet darauf, dass die angegebene Ressource auf einer bestimmten Anzahl von Zielknoten, die in der „NodeName“-Eigenschaft angegeben sind, den gewünschten Zustand hat.

Diese Ressourcen ermöglichen eine Synchronisierung zwischen Knoten mithilfe von CIM-Verbindungen über das Protokoll „WS-Man“. Mithilfe dieser Ressourcen kann eine Konfiguration warten, bis sich der Zustand einer bestimmten Ressource eines anderen Computers geändert hat, ehe sie selbst fortgesetzt wird. 

Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource <ctype="x-NOTFOUND" mdpre="**" mdpost="**">xADDomain</ctype="x-NOTFOUND"> auf dem Knoten <ctype="x-NOTFOUND" mdpre="**" mdpost="**">MyDC</ctype="x-NOTFOUND"> (mit einigen Wiederholungen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.

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
<ctype="x-NOTFOUND" mdpre="**" mdpost="**">Hinweis:</ctype="x-NOTFOUND"> Standardmäßig haben die „WaitFor\*“-Ressourcen nur einen Versuch, weshalb Sie, wenngleich nicht erforderlich, ein Intervall und eine Anzahl von Wiederholungen angeben sollten.


<!--HONumber=Mar16_HO3-->


