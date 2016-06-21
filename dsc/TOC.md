# [Übersicht](overview.md)

# [Konfigurationen](configurations.md)
## [Inkraftsetzung von Konfigurationen](enactingConfigurations.md)
## [Verwenden von Ressourcen mit mehreren Versionen](sxsResource.md)
## [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md)
## [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md)
## [Konfigurationsdaten](configData.md)
### [Optionen für Anmeldeinformationen in Konfigurationsdaten](configDataCredentials.md)
## [Schützen der MOF-Konfigurationsdatei](secureMOF.md)
## [Teilkonfigurationen](partialConfigs.md)
## [Schreiben von Hilfe für DSC-Konfigurationen](configHelp.md)

# [Ressourcen](resources.md)
## [Integrierte Ressourcen](builtInResource.md)
### [Ressource „Archive“](archiveResource.md)
### [Ressource „Environment“](environmentResource.md)
### [Ressource „File“](fileResource.md)
### [Ressource „Group“](groupResource.md)
### [Ressource „Log“](logResource.md)
### [Ressource „Package“](packageResource.md)
### [Ressource „Registry“](registryResource.md)
### [Ressource „Script“](scriptResource.md)
### [Ressource „Service“](serviceResource.md)
### [Benutzerressource](userResource.md)
### [Ressource „WindowsFeature“](windowsfeatureResource.md)
### [Ressource „WindowsProcess“](windowsProcessResource.md)
## [Erstellen benutzerdefinierter Ressourcen](authoringResource.md) 
### [MOF-basierte benutzerdefinierte Ressourcen](authoringResourceMOF.md)
#### [MOF-basierte Ressourcen in C#](authoringResourceMofCS.md)
### [Klassenbasierte benutzerdefinierte Ressourcen](authoringResourceClass.md)
### [Zusammengesetzte Ressourcen](authoringResourceComposite.md)
### [Schreiben einer Einzelinstanz-DSC-Ressource (empfohlen)](singleInstance.md)
### [Prüfliste für die Ressourcenerstellung](resourceAuthoringChecklist.md)
## [Debuggen von DSC-Ressourcen](debugResource.md)
## [Direktes Aufrufen von DSC-Ressourcenmethoden](directCallResource.md)

# [Konfigurieren des lokalen Konfigurations-Managers (LCM)](metaConfig.md)
## [Konfigurieren des LCM in PowerShell 4.0](metaConfig4.md)

# Das DSC-Pullmodell
## [Einrichten eines Webpullservers](pullServer.md)
## [Einrichten eines DSC-SMB-Pullservers](pullServerSMB.md)
## [Einrichten eines Pullclients](pullClient.md)
### [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md)
### [Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md)
## [Verwenden eines DSC-Berichtsservers](reportServer.md)
## [Bewährte Methoden für Pullserver](secureServer.md)

# [Problembehandlung bei DSC](troubleshooting.md)

# [Verwenden von DSC auf Nano Server](nanoDsc.md)

# DSC für Linux
## [Erste Schritte mit DSC für Linux](lnxGettingStarted.md)
## [Integrierte Ressourcen für Linux](lnxBuiltInResources.md)
### [Ressource „nxArchive“](lnxArchiveResource.md)
### [Ressource „nxEnvironment“](lnxEnvironmentResource.md)
### [Ressource „nxFile“](lnxFileResource.md)
### [Ressource „nxFileLine“](lnxFileLineResource.md)
### [Ressource „nxGroup“](lnxGroupResource.md)
### [Ressource „nxPackage“](lnxPackageResource.md)
### [Ressource „nxService“](lnxServiceResource.md)
### [Ressource „nxSshAuthorizedKeys“](lnxSshAuthorizedKeysResource.md)
### [Resource „nxUser“](lnxUserResource.md)

# DSC MOF-Referenz
## [MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager.md)
### [ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-applyconfiguration.md)
### [DisableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)
### [EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)
### [GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-getconfiguration.md)
### [GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)
### [GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)
### [GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)
### [PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
### [RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-removeconfiguration.md)
### [ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-resourceget.md)
### [ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-resourceset.md)
### [ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-resourcetest.md)
### [RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-rollback.md)
### [SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-sendconfiguration.md)
### [SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)
### [SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)
### [SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)
### [StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-stopconfiguration.md)
### [TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Weitere Ressourcen
## [Whitepapers](whitepapers.md)



<!--HONumber=Jun16_HO3-->


