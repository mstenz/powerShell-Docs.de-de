# Trennung von Konfigurations-, Ressourcen- und Berichtsrepositorys

In dieser Version bieten wir Ihnen die Flexibilität, die Sie brauchen, um Konfigurationen per Pull von einem oder mehreren DSC-Pullservern zu beziehen und Berichte dazu zu erstellen. Jeder Endpunkt kann separat definiert werden, damit Sie Konfigurationen von einem Speicherort, Ressourcen von einem anderen und Berichte von noch einem anderen per Pull beziehen können. Mit der folgenden Metakonfiguration wird genau dies umgesetzt.

```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
    }

    ConfigurationRepositoryWeb Configurations
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```

Darüber hinaus können Sie eine beliebige Kombination dieser Speicherorte nutzen. Die folgende Metakonfiguration konfiguriert einen Zielknoten im Pushmodus, doch der Knoten bezieht Ressourcen, die er nicht installiert hat, per Pull von einem DSC-Pullserver, und meldet seinen Status einem weiteren DSC-Pullserver.


```PowerShell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "Push";
        RebootNodeIfNeeded = $true;
    }

    ResourceRepositoryWeb Resources
    {
        ServerURL = “https://ResourceServer:8080/psdscpullserver.svc”
        RegistrationKey = "aaaf952b-b9d6-406b-b416-e0f759c6e000"
    }

    ReportServerWeb Reports
    {
        ServerURL = “https://ReportServer:8080/psdscpullserver.svc”
        RegistrationKey = "fefe592b-b9d6-046b-b146-e0f759c0c0c0"
    }
}
```<!--HONumber=Mar16_HO2-->
