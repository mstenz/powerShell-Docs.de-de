---
title: Trennen von Konfiguration und Umgebungsdaten
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 3038854786edaa9f24b6cf39b7c0c49b3d5206e3
ms.openlocfilehash: 448cddf17a67ace9d228d1d8a9dc39109d0c91d5

---

# <a name="separating-configuration-and-environment-data"></a>Trennen von Konfiguration und Umgebungsdaten

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Mithilfe des integrierten DSC-Parameters **ConfigurationData** können Sie Daten definieren, die innerhalb einer Konfiguration verwendet werden können. Dadurch können Sie eine einzige Konfiguration erstellen, die für mehrere Knoten oder für unterschiedliche Umgebungen verwendet werden kann. Wenn Sie z.B. eine Anwendung entwickeln, können Sie eine Konfiguration für die Entwicklungs-und die Produktionsumgebung verwenden und mithilfe von Konfigurationsdaten Daten für jede Umgebung angeben.

Sehen wir uns ein sehr einfaches Beispiel zur Funktionsweise an. Wir erstellen eine einzelne Konfiguration, die sicherstellt, dass auf einigen Knoten **IIS** und auf anderen **Hyper-V** vorliegt: 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData = 
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

Die letzte Zeile in diesem Skript kompiliert die Konfiguration in MOF-Dokumente und übergibt `$MyData` als Wert des **ConfigurationData**-Parameters. `$MyData` gibt die zwei verschiedene Knoten an, jeweils mit eigenem `NodeName` und `Role`. Die Konfiguration erstellt dynamisch **Node**-Blöcke, indem Sie die von `$MyData` (insbesondere `$AllNodes`) erhaltene Sammlung von Knoten nach der `Role`-Eigenschaft filtert.

Gehen wir nun tiefer ins Detail.

## <a name="the-configurationdata-parameter"></a>Der Parameter „ConfigurationData“

Eine DSC-Konfiguration besitzt einen Parameter namens **ConfigurationData**, den Sie beim Kompilieren der Konfiguration angeben. Informationen zum Kompilieren von Konfigurationen finden Sie unter [DSC-Konfigurationen](configurations.md).

Der Parameter **ConfigurationData** ist eine Hashtabelle, die mindestens einen Schlüssel namens **AllNodes** benötigt. Er kann auch andere Schlüssel besitzen:

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

Der Wert des **AllNodes**-Schlüssels ist ein Array. Jedes Element dieses Arrays ist ebenfalls eine Hashtabelle, die mindestens einen Schlüssel namens **NodeName** benötigt:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

Sie können jeder Hashtabelle auch andere Schlüssel hinzufügen:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

Um allen Knoten eine Eigenschaft zuzuweisen, können Sie ein Member des **AllNodes**-Arrays erstellen, dessen **NodeName** gleich `*` ist. Verwenden Sie z.B. folgenden Code, um allen Knoten die Eigenschaft `LogPath` zuzuweisen:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Dies entspricht dem Hinzufügen einer Eigenschaft namens `LogPath` mit einem Wert `"C:\Logs"` zu jedem der anderen Blöcke (`VM-1`, `VM-2` und `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definieren der ConfigurationData-Hashtabelle

Sie können **ConfigurationData** entweder als eine Variable innerhalb derselben Skriptdatei als Konfiguration (wie in unseren bisherigen Beispielen) oder in einer separaten PSD1-Datei definieren. Erstellen Sie zum Definieren von **ConfigurationData** in einer PSD1-Datei eine Datei, die nur die Hashtabelle enthält, die die Konfigurationsdaten darstellt.

Sie könnten z.B. eine Datei namens `MyData.psd1` mit folgendem Inhalt erstellen:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

Um Konfigurationsdaten zu verwenden, die in einer PSD1-Datei definiert sind, übergeben Sie Pfad und Namen der Datei bei der Kompilierung der Konfiguration als Wert des Parameters **ConfigurationData**:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Verwenden von ConfigurationData-Variablen in einer Konfiguration

DSC stellt drei spezielle Variablen bereit, die in einem Skript verwendet werden können: **$AllNodes**, **$Node** und **$ConfigurationData**.

- **$AllNodes** bezieht sich auf die gesamte, in **ConfigurationData** definierte Knotensammlung. Sie können die **AllNodes**-Sammlung mit **.Where()** und **.ForEach()**´filtern.
- **Nodes** bezieht sich auf einen bestimmten Eintrag in der **AllNodes**-Sammlung, nachdem sie mithilfe von **.Where()** oder **.ForEach()** gefiltert wurde.
- **ConfigurationData** bezieht sich auf die gesamte Hashtabelle, die beim Kompilieren einer Konfiguration als Parameter übergeben wird.

## <a name="devops-example"></a>DevOps-Beispiel

Sehen wir uns ein vollständiges Beispiel an, in dem eine einzelne Konfiguration dazu verwendet wird, die Entwicklungs- und Produktionsumgebungen einer Website einzurichten. In der Entwicklungsumgebung werden IIS und SQL Server auf demselben Knoten installiert. In der Produktionsumgebung werden sowohl IIS als auch SQL Server auf jeweils eigenen Knoten installiert. Wir verwenden eine PSD1-Konfigurationsdatendatei, um die Daten für die zwei verschiedenen Umgebungen anzugeben.

### <a name="configuration-data-file"></a>Die Konfigurationsdatendatei

Wir definieren die Entwicklungs- und die Produktionsumgebungsdaten in einer Datei namens `DevProdEnvData.psd1` wie folgt:

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>Konfigurationsdatei

In der Konfiguration filtern wir nun die in `DevProdEnvData.psd1` definierten Knoten nach ihrer Rolle (`MSSQL`, `Dev` oder beides) und konfigurieren sie entsprechend. In der Entwicklungsumgebung sind SQL Server und IIS auf demselben Knoten installiert, während sie sich in der Produktionsumgebung auf zwei verschiedenen Knoten befinden. Die Inhalte von „Site“ unterscheiden sich also gemäß der `SiteContents`-Eigenschaften.

Am Ende des Konfigurationsskripts, rufen wir die Konfiguration auf (kompilieren sie in einem MOF-Dokument) und übergeben `DevProdEnvData.psd1` als `$ConfigurationData`-Parameter.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {            
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where($_.Role -contains "Web")
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite 
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }       


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

MyWebApp -ConfigurationData DevProdEnvData.psd1

}
```

## <a name="see-also"></a>Weitere Informationen
- [Optionen für Anmeldeinformationen in den Konfigurationsdaten](configDataCredentials.md)
- [DSC-Konfigurationen](configurations.md)


<!--HONumber=Nov16_HO1-->


