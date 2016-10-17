---
title: "Übertragen einer Namenskonvention für eine partielle Konfiguration mithilfe von Pull"
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##Übertragen einer Namenskonvention für eine partielle Konfiguration mithilfe von Pull
In den vorherigen Releases galt für die Namenskonvention einer partiellen Konfiguration, dass der MOF-Dateiname im Pull-Server/-Dienst dem Namen der partiellen Konfiguration entsprechen sollte, der in den Einstellungen des lokalen Konfigurations-Managers (Local Configuration Manager, LCM) angegeben ist. Dieser wiederum muss dem in der MOF-Datei eingebetteten Konfigurationsnamen entsprechen. Sehen Sie sich die nachfolgenden Momentaufnahmen an: •   lokale Konfigurationseinstellungen, die eine partielle Konfiguration definieren, die von einem Knoten empfangen werden darf.

![Beispiel einer Metakonfiguration](../../images/MetaConfigPartialOne.png)

•   Beispieldefinition einer partiellen Konfiguration 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   ConfigurationName, eingebettet in der generierten MOF-Datei

![Beispiel einer generierten MOF-Datei](../../images/PartialGeneratedMof.png)

•   FileName im Repository der Pull-Konfiguration 

![FileName im Repository der Konfiguration](../../images/PartialInConfigRepository.png)

Basierend auf dem Namen des Azure Automation-Diensts generierte MOF-Dateien nach dem Schema „``<ConfigurationName>.<NodeName>.mof``“. Daher wurde die nachstehende Konfiguration in „PartialOne.Localhost.mof“ kompiliert.  
Aus diesem Grund war es nicht möglich, eine Teilkonfiguration aus dem Azure Automation-Dienst mithilfe von Pull zu übertragen.

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

In WMF 5.1 kann die Teilkonfiguration im Pullserver/-dienst nach dem Schema „``<ConfigurationName>.<NodeName>.mof``“ benannt werden. Darüber hinaus kann das Konfigurationsdokument auf dem Konfigurationsrepository des Pull-Servers einen beliebigen Namen haben, wenn ein Computer eine einzelne Konfiguration von einem Pull-Server/-Dienst mithilfe von Pull überträgt. Diese Benennungsflexibilität ermöglicht das Verwalten einer Teilkonfiguration eines Knotens sowohl mithilfe des lokalen Pull-Servers als auch mithilfe des Pull-Servers von Azure Automation. Beispielsweise können Sie Basisteilkonfiguration haben, die lokal mit Push übertragen wird, sowie eine andere Teilkonfiguration, die durch den Azure Automation-Dienst mit Pull übertragen wird.

Die nachfolgende Metakonfiguration richtet einen Knoten ein, der sowohl lokal als auch über den Azure Automation-Dienst verwaltet wird.

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```





<!--HONumber=Aug16_HO3-->


