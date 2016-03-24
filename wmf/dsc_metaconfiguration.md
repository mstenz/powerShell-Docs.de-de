# Konfigurieren des LCM von DSC mit neuem Metakonfigurationsattribut

Das `DscLocalConfigurationManager`-Attribut kennzeichnet einen Konfigurationsblock als Metakonfiguration, die zum Konfigurieren des lokalen Konfigurations-Managers von DSC verwendet wird. Dieses Attribut beschränkt eine Konfiguration auf ausschließlich Elemente, die zum Konfigurieren des lokalen Konfigurations-Managers von DSC dienen. Während der Verarbeitung generiert diese Konfiguration eine `*.meta.mof`-Datei, die dann mit dem Cmdlet `Set-DscLocalConfigurationManager` an die entsprechenden Zielknoten gesendet wird.

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

Im obigen Beispiel wird der Aktualisierungsmodus für den LCM als Pullmodus konfiguriert, der Konfigurationsmodus in „ApplyAndAutocorrect“ geändert und der Typ und Ort des Pullservers definiert.

Dieses neue Konfigurationsattribut ersetzt und erweitert die Funktionalität der Ressource „LocalConfigurationManager“ von PowerShell 4.0. Dieser „LocalConfigurationManager“ wird weiterhin zwecks Abwärtskompatibilität in Konfigurationen ohne dieses Attribut unterstützt.

Metaressourcen:

| **Ressourcenname**            | **Beschreibung**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | Verschiedene Einstellungen für die Ausführung des DSC-Moduls      |
| PartialConfiguration         | Teilkonfigurationseinstellungen                 |
| ConfigurationRepositoryWeb   | Webbasiertes Konfigurationsrepository             |
| ConfigurationRepositoryShare | Dateifreigabebasiertes Konfigurationsrepository      |
| ResourceRepositoryWeb        | Webbasiertes Ressourcenrepository                  |
| ResourceRepositoryShare      | Dateibasiertes Ressourcenrepository                 |
| ReportServerWeb              | Webbasierter Berichterstellungsendpunkt für Pullszenario |
<!--HONumber=Mar16_HO2-->
