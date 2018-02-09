# [Übersicht](overview.md)

## [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](decisionMaker.md)

## [Desired State Configuration (DSC): Übersicht für Ingenieure](DscForEngineers.md)

## [DSC quick start (DSC-Schnellstart)](quickStart.md)

# [Konfigurationen](configurations.md)

## [Inkraftsetzung von Konfigurationen](enactingConfigurations.md)

## [Trennen von Konfiguration und Umgebungsdaten](separatingEnvData.md)

## [Verwenden von Ressourcen mit mehreren Versionen](sxsResource.md)

## [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md)

## [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md)

## [Konfigurationsdaten](configData.md)

### [Optionen für Anmeldeinformationen in Konfigurationsdaten](configDataCredentials.md)

## [Verschachteln von Konfigurationen](compositeConfigs.md)

## [Schützen der MOF-Konfigurationsdatei](secureMOF.md)

## [Teilkonfigurationen](partialConfigs.md)

## [Schreiben von Hilfe für DSC-Konfigurationen](configHelp.md)

## [Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC](bootstrapDsc.md)

### [DSCAutomationHostEnabled (Registrierungsschlüssel)](DSCAutomationHostEnabled.md)

# [Ressourcen](resources.md)

## [Integrierte Ressourcen](builtInResource.md)

### [Archive-Ressource](archiveResource.md)

### [Environment-Ressource](environmentResource.md)

### [File-Ressource](fileResource.md)

### [Group-Ressource](groupResource.md)

### [GroupSet-Ressource](groupSetResource.md)

### [Log-Ressource](logResource.md)

### [Package-Ressource](packageResource.md)

### [ProcessSet-Ressource](processSetResource.md)

### [Registry-Ressource](registryResource.md)

### [Script-Ressource](scriptResource.md)

### [Service-Ressource](serviceResource.md)

### [ServiceSet-Ressource](serviceSetResource.md)

### [User-Ressource](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [WindowsFeature-Ressource](windowsfeatureResource.md)

### [WindowsFeatureSet-Ressource](windowsFeatureSetResource.md)

### [WindowsOptionalFeature-Ressource](windowsOptionalFeatureResource.md)

### [WindowsOptionalFeatureSet-Ressource](windowsOptionalFeatureSetResource.md)

### [WindowsPackageCab-Ressource](windowsPackageCabResource.md)

### [WindowsProcess-Ressource](windowsProcessResource.md)

## [Erstellen benutzerdefinierter Ressourcen](authoringResource.md) 

### [MOF-basierte benutzerdefinierte Ressourcen](authoringResourceMOF.md)

#### [MOF-basierte Ressourcen in C#](authoringResourceMofCS.md)

### [Klassenbasierte benutzerdefinierte Ressourcen](authoringResourceClass.md)

### [Zusammengesetzte Ressourcen](authoringResourceComposite.md)

### [Schreiben einer Einzelinstanz-DSC-Ressource (empfohlen)](singleInstance.md)

### [Prüfliste für die Ressourcenerstellung](resourceAuthoringChecklist.md)

## [Debuggen von DSC-Ressourcen](debugResource.md)

## [Direktes Aufrufen von DSC-Ressourcenmethoden](directCallResource.md)

# Lokaler Konfigurationsmanager (LCM)

## [Konfigurieren des lokalen Konfigurations-Managers (LCM)](metaConfig.md)

## [Konfigurieren des LCM in PowerShell 4.0](metaConfig4.md)

# Das DSC-Pullmodell

## [DSC-Pulldienst](pullServer.md)

## [Einrichten eines DSC-SMB-Pullservers](pullServerSMB.md)

## [Einrichten eines Pullclients](pullClient.md)

### [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md)

### [Einrichten eines Pullclients mithilfe einer Konfigurations-ID](pullClientConfigID.md)

## [Verwenden eines DSC-Berichtsservers](reportServer.md)

## [Bewährte Methoden für Pullserver](secureServer.md)

# [DSC-Beispiele](dscExamples.md)

## [Erstellen einer CI/CD-Pipeline mit DSC, Pester und Visual Studio Team Services](dscCiCd.md)

## [Trennen von Konfiguration und Umgebungsdaten](separatingEnvData.md)

# [Problembehandlung bei DSC](troubleshooting.md)

# [Verwenden von DSC unter Nano Server](nanoDsc.md)

# DSC für Linux

## [Erste Schritte mit DSC für Linux](lnxGettingStarted.md)

## [Integrierte Ressourcen für Linux](lnxBuiltInResources.md)

### [nxArchive Ressource](lnxArchiveResource.md)

### [nxEnvironment-Ressource](lnxEnvironmentResource.md)

### [nxFile-Ressource](lnxFileResource.md)

### [nxFileLine-Ressource](lnxFileLineResource.md)

### [nxGroup-Ressource](lnxGroupResource.md)

### [nxPackage-Ressource](lnxPackageResource.md)

### [nxService-Ressource](lnxServiceResource.md)

### [nxSshAuthorizedKeys-Ressource](lnxSshAuthorizedKeysResource.md)

### [nxUser-Ressource](lnxUserResource.md)

# [Verwenden von DSC in Microsoft Azure](azureDsc.md)

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
