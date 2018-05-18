---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Trennen von Konfiguration und Umgebungsdaten
ms.openlocfilehash: 3308b83555b3a917e2aa993efcbfa0b946e44048
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="0b47e-103">Trennen von Konfiguration und Umgebungsdaten</span><span class="sxs-lookup"><span data-stu-id="0b47e-103">Separating configuration and environment data</span></span>

><span data-ttu-id="0b47e-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0b47e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0b47e-105">Es kann sinnvoll sein, die in einer DSC-Konfiguration verwendeten Daten unter Verwendung der Konfigurationsdaten von der Konfiguration selbst zu trennen.</span><span class="sxs-lookup"><span data-stu-id="0b47e-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="0b47e-106">Auf diese Weise können Sie eine einzelne Konfiguration für mehrere Umgebungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="0b47e-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="0b47e-107">Wenn Sie z.B. eine Anwendung entwickeln, können Sie eine Konfiguration für die Entwicklungs-und die Produktionsumgebung verwenden und mithilfe von Konfigurationsdaten Daten für jede Umgebung angeben.</span><span class="sxs-lookup"><span data-stu-id="0b47e-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="0b47e-108">Was sind Konfigurationsdaten?</span><span class="sxs-lookup"><span data-stu-id="0b47e-108">What is configuration data?</span></span>

<span data-ttu-id="0b47e-109">Konfigurationsdaten sind Daten, die in einer Hashtabelle definiert sind und an eine DSC-Konfiguration übergeben wurden, wenn Sie diese Konfiguration kompilieren.</span><span class="sxs-lookup"><span data-stu-id="0b47e-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="0b47e-110">Eine ausführliche Beschreibung der Hashtabelle **ConfigurationData** finden Sie unter [Using configuration data (Verwenden von Konfigurationsdaten)](configData.md).</span><span class="sxs-lookup"><span data-stu-id="0b47e-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="0b47e-111">Ein einfaches Beispiel</span><span class="sxs-lookup"><span data-stu-id="0b47e-111">A simple example</span></span>

<span data-ttu-id="0b47e-112">Sehen wir uns ein sehr einfaches Beispiel zur Funktionsweise an.</span><span class="sxs-lookup"><span data-stu-id="0b47e-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="0b47e-113">Wir erstellen eine einzelne Konfiguration, die sicherstellt, dass auf einigen Knoten **IIS** und auf anderen **Hyper-V** vorliegt:</span><span class="sxs-lookup"><span data-stu-id="0b47e-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

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

<span data-ttu-id="0b47e-114">Die letzte Zeile in diesem Skript kompiliert die Konfiguration, die `$MyData` als Wert des Parameters **ConfigurationData** übergibt.</span><span class="sxs-lookup"><span data-stu-id="0b47e-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="0b47e-115">Als Ergebnis werden zwei MOF-Dateien erstellt:</span><span class="sxs-lookup"><span data-stu-id="0b47e-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="0b47e-116">`$MyData` gibt die zwei verschiedene Knoten an, jeweils mit eigenem `NodeName` und `Role`.</span><span class="sxs-lookup"><span data-stu-id="0b47e-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="0b47e-117">Die Konfiguration erstellt dynamisch **Node**-Blöcke, indem Sie die von `$MyData` (insbesondere `$AllNodes`) erhaltene Sammlung von Knoten nach der `Role`-Eigenschaft filtert.</span><span class="sxs-lookup"><span data-stu-id="0b47e-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="0b47e-118">Verwenden von Konfigurationsdaten für die Definition der Entwicklungs- und Produktionsumgebungen</span><span class="sxs-lookup"><span data-stu-id="0b47e-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="0b47e-119">Sehen wir uns ein vollständiges Beispiel an, in dem eine einzelne Konfiguration dazu verwendet wird, die Entwicklungs- und Produktionsumgebungen einer Website einzurichten.</span><span class="sxs-lookup"><span data-stu-id="0b47e-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="0b47e-120">In der Entwicklungsumgebung werden IIS und SQL Server auf demselben Knoten installiert.</span><span class="sxs-lookup"><span data-stu-id="0b47e-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="0b47e-121">In der Produktionsumgebung werden sowohl IIS als auch SQL Server auf jeweils eigenen Knoten installiert.</span><span class="sxs-lookup"><span data-stu-id="0b47e-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="0b47e-122">Wir verwenden eine PSD1-Konfigurationsdatendatei, um die Daten für die zwei verschiedenen Umgebungen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="0b47e-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

 ### <a name="configuration-data-file"></a><span data-ttu-id="0b47e-123">Die Konfigurationsdatendatei</span><span class="sxs-lookup"><span data-stu-id="0b47e-123">Configuration data file</span></span>

<span data-ttu-id="0b47e-124">Wir definieren die Entwicklungs- und die Produktionsumgebungsdaten in einer Datei namens `DevProdEnvData.psd1` wie folgt:</span><span class="sxs-lookup"><span data-stu-id="0b47e-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
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

### <a name="configuration-script-file"></a><span data-ttu-id="0b47e-125">Konfiguration einer Skriptdatei</span><span class="sxs-lookup"><span data-stu-id="0b47e-125">Configuration script file</span></span>

<span data-ttu-id="0b47e-126">In der Konfiguration, die in einer `.ps1`-Datei definiert ist, filtern wir nun die in `DevProdEnvData.psd1` definierten Knoten nach ihrer Rolle (`MSSQL`, `Dev` oder beides) und konfigurieren sie entsprechend.</span><span class="sxs-lookup"><span data-stu-id="0b47e-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="0b47e-127">In der Entwicklungsumgebung sind SQL Server und IIS auf demselben Knoten installiert, während sie sich in der Produktionsumgebung auf zwei verschiedenen Knoten befinden.</span><span class="sxs-lookup"><span data-stu-id="0b47e-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="0b47e-128">Die Inhalte von „Site“ unterscheiden sich also gemäß der `SiteContents`-Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="0b47e-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="0b47e-129">Am Ende des Konfigurationsskripts, rufen wir die Konfiguration auf (kompilieren sie in einem MOF-Dokument) und übergeben `DevProdEnvData.psd1` als `$ConfigurationData`-Parameter.</span><span class="sxs-lookup"><span data-stu-id="0b47e-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="0b47e-130">**Hinweis:** Für diese Konfiguration müssen die Module `xSqlPs` und `xWebAdministration` auf dem Zielknoten installiert sein.</span><span class="sxs-lookup"><span data-stu-id="0b47e-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="0b47e-131">Definieren wir nun die Konfiguration in einer Datei namens `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="0b47e-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
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
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="0b47e-132">Wenn Sie diese Konfiguration ausführen, werden drei MOF-Dateien erstellt (für jeden benannten Eintrag im **AllNodes**-Array):</span><span class="sxs-lookup"><span data-stu-id="0b47e-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="0b47e-133">Verwenden von Daten ohne Knoten</span><span class="sxs-lookup"><span data-stu-id="0b47e-133">Using non-node data</span></span>

<span data-ttu-id="0b47e-134">Sie können zusätzliche Schlüssel zur Hashtabelle **ConfigurationData** für Daten hinzufügen, die nicht knotenspezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="0b47e-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="0b47e-135">Die folgende Konfiguration gewährleistet das Vorhandensein von zwei Websites.</span><span class="sxs-lookup"><span data-stu-id="0b47e-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="0b47e-136">Daten für jede Website sind im **AllNodes**-Array definiert.</span><span class="sxs-lookup"><span data-stu-id="0b47e-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="0b47e-137">Die Datei `Config.xml` wird für beide Websites verwendet, sodass wir sie in einem zusätzlichen Schlüssel mit dem Namen `NonNodeData` definieren.</span><span class="sxs-lookup"><span data-stu-id="0b47e-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="0b47e-138">Beachten Sie, dass Sie über beliebig viele zusätzliche Schlüssel verfügen und diese beliebig benennen können.</span><span class="sxs-lookup"><span data-stu-id="0b47e-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="0b47e-139">`NonNodeData` ist kein reserviertes Wort, sondern einfach der Name, für den wir uns bei dem zusätzlichen Schlüssel entschieden haben.</span><span class="sxs-lookup"><span data-stu-id="0b47e-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="0b47e-140">Mit der speziellen Variable **$ConfigurationData** können Sie auf zusätzliche Schlüssel zugreifen.</span><span class="sxs-lookup"><span data-stu-id="0b47e-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="0b47e-141">In diesem Beispiel erfolgt der Zugriff auf `ConfigFileContents` mit der Zeile:</span><span class="sxs-lookup"><span data-stu-id="0b47e-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="0b47e-142">im `File`-Ressourcenblock.</span><span class="sxs-lookup"><span data-stu-id="0b47e-142">in the `File` resource block.</span></span>


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


## <a name="see-also"></a><span data-ttu-id="0b47e-143">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0b47e-143">See Also</span></span>
- [<span data-ttu-id="0b47e-144">Using configuration data (Verwenden von Konfigurationsdaten)</span><span class="sxs-lookup"><span data-stu-id="0b47e-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="0b47e-145">Optionen für Anmeldeinformationen in den Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="0b47e-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="0b47e-146">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="0b47e-146">DSC Configurations</span></span>](configurations.md)
