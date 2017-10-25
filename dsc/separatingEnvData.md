---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Trennen von Konfiguration und Umgebungsdaten
ms.openlocfilehash: df3cfea08419c37716b408fdbd6b43e78be2331c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="separating-configuration-and-environment-data"></a>Trennen von Konfiguration und Umgebungsdaten

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Es kann sinnvoll sein, die in einer DSC-Konfiguration verwendeten Daten unter Verwendung der Konfigurationsdaten von der Konfiguration selbst zu trennen.
Auf diese Weise können Sie eine einzelne Konfiguration für mehrere Umgebungen verwenden.

Wenn Sie z.B. eine Anwendung entwickeln, können Sie eine Konfiguration für die Entwicklungs-und die Produktionsumgebung verwenden und mithilfe von Konfigurationsdaten Daten für jede Umgebung angeben.

## <a name="what-is-configuration-data"></a>Was sind Konfigurationsdaten?

Konfigurationsdaten sind Daten, die in einer Hashtabelle definiert sind und an eine DSC-Konfiguration übergeben wurden, wenn Sie diese Konfiguration kompilieren.

Eine ausführliche Beschreibung der Hashtabelle **ConfigurationData** finden Sie unter [Using configuration data (Verwenden von Konfigurationsdaten)](configData.md).

## <a name="a-simple-example"></a>Ein einfaches Beispiel

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
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
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
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

Die letzte Zeile in diesem Skript kompiliert die Konfiguration, die `$MyData` als Wert des Parameters **ConfigurationData** übergibt.

Als Ergebnis werden zwei MOF-Dateien erstellt:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
`$MyData` gibt die zwei verschiedene Knoten an, jeweils mit eigenem `NodeName` und `Role`. Die Konfiguration erstellt dynamisch **Node**-Blöcke, indem Sie die von `$MyData` (insbesondere `$AllNodes`) erhaltene Sammlung von Knoten nach der `Role`-Eigenschaft filtert.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Verwenden von Konfigurationsdaten für die Definition der Entwicklungs- und Produktionsumgebungen

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
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a>Konfiguration einer Skriptdatei

In der Konfiguration, die in einer `.ps1`-Datei definiert ist, filtern wir nun die in `DevProdEnvData.psd1` definierten Knoten nach ihrer Rolle (`MSSQL`, `Dev` oder beides) und konfigurieren sie entsprechend. In der Entwicklungsumgebung sind SQL Server und IIS auf demselben Knoten installiert, während sie sich in der Produktionsumgebung auf zwei verschiedenen Knoten befinden. Die Inhalte von „Site“ unterscheiden sich also gemäß der `SiteContents`-Eigenschaften.

Am Ende des Konfigurationsskripts, rufen wir die Konfiguration auf (kompilieren sie in einem MOF-Dokument) und übergeben `DevProdEnvData.psd1` als `$ConfigurationData`-Parameter.

>**Hinweis:** Für diese Konfiguration müssen die Module `xSqlPs` und `xWebAdministration` auf dem Zielknoten installiert sein.

Definieren wir nun die Konfiguration in einer Datei namens `MyWebApp.ps1`:

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

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

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
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

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

Wenn Sie diese Konfiguration ausführen, werden drei MOF-Dateien erstellt (für jeden benannten Eintrag im **AllNodes**-Array):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Verwenden von Daten ohne Knoten

Sie können zusätzliche Schlüssel zur Hashtabelle **ConfigurationData** für Daten hinzufügen, die nicht knotenspezifisch sind.
Die folgende Konfiguration gewährleistet das Vorhandensein von zwei Websites.
Daten für jede Website sind im **AllNodes**-Array definiert.
Die Datei `Config.xml` wird für beide Websites verwendet, sodass wir sie in einem zusätzlichen Schlüssel mit dem Namen `NonNodeData` definieren.
Beachten Sie, dass Sie über beliebig viele zusätzliche Schlüssel verfügen und diese beliebig benennen können.
`NonNodeData` ist kein reserviertes Wort, sondern einfach der Name, für den wir uns bei dem zusätzlichen Schlüssel entschieden haben.

Mit der speziellen Variable **$ConfigurationData** können Sie auf zusätzliche Schlüssel zugreifen.
In diesem Beispiel erfolgt der Zugriff auf `ConfigFileContents` mit der Zeile:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 im `File`-Ressourcenblock.


```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },
 
        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },
 
        
        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );
 
    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 
 
configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
 
    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }
 
        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
} 
```


## <a name="see-also"></a>Weitere Informationen
- [Using configuration data (Verwenden von Konfigurationsdaten)](configData.md)
- [Optionen für Anmeldeinformationen in den Konfigurationsdaten](configDataCredentials.md)
- [DSC-Konfigurationen](configurations.md)

