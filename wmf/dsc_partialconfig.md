# Konfigurieren von Knoten mit mehreren Konfigurationsfragmenten (Teilkonfigurationen)

WMF 5.0 hilft Ihnen, Konfigurationsdokumente in Fragmenten an einen Knoten zu übermitteln. Damit ein Knoten mehrere Fragmente eines Konfigurationsdokuments empfangen kann, muss sein lokaler Konfigurations-Manager für das Angeben der erwarteten Fragmente eingerichtet sein (siehe das folgende Beispiel).

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

Bei einer Teilkonfiguration muss der Konfigurationsname der Definition im LCM entsprechen. Beim vorherigen Beispiel müssen die Konfigurationen `OSConfig` und `SQLConfig` heißen.

Das Festlegen des LCM für Teilkonfigurationen ermöglicht die Koordinierung der Konfiguration, bietet aber keine Sicherheitsfunktionen.<!--HONumber=Mar16_HO2-->
