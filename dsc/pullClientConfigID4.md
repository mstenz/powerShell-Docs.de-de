---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID in PowerShell 4.0
ms.openlocfilehash: 19328018d276cddd0877869b0ec69c14c51e4b85
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="9422f-103">Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID in PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="9422f-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="9422f-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9422f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9422f-105">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL angegeben werden, unter der der Pullserver zum Abrufen von Konfigurationen kontaktiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="9422f-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="9422f-106">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9422f-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="9422f-107">Zum Konfigurieren des LCM müssen Sie einen besonderen Typ von Konfiguration erstellen, die als „Metakonfiguration“ bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="9422f-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="9422f-108">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Windows PowerShell 4.0 DSC – Lokaler Konfigurations-Manager](metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="9422f-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="9422f-109">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „PullServer“:</span><span class="sxs-lookup"><span data-stu-id="9422f-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="9422f-110">Im Skript übergibt **DownloadManagerCustomData** die URL des Pullservers und lässt (bei diesem Beispiel) eine unsichere Verbindung zu.</span><span class="sxs-lookup"><span data-stu-id="9422f-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span> 

<span data-ttu-id="9422f-111">Nachdem das Skript ausgeführt wurde, erstellt es einen neuen Ausgabeordner mit dem Namen **SimpleMetaConfigurationForPull**, der eine MOF-Datei mit der Metakonfiguration enthält.</span><span class="sxs-lookup"><span data-stu-id="9422f-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="9422f-112">Um die Konfiguration anzuwenden, verwenden Sie das Cmdlet **Set DscLocalConfigurationManager** mit Parametern für **ComputerName** (verwenden Sie „localhost“) und **Path** (der Pfad zum Speicherort der Datei „localhost.meta.mof“ für den Zielknoten).</span><span class="sxs-lookup"><span data-stu-id="9422f-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="9422f-113">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="9422f-113">For example:</span></span> 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="9422f-114">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="9422f-114">Configuration ID</span></span>
<span data-ttu-id="9422f-115">Das Skript legt die **ConfigurationID**-Eigenschaft des LCM auf eine GUID fest, die zuvor für diesen Zweck erstellt wurde (Sie können eine GUID mit dem Cmdlet **New-Guid** erstellen).</span><span class="sxs-lookup"><span data-stu-id="9422f-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="9422f-116">Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver.</span><span class="sxs-lookup"><span data-stu-id="9422f-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="9422f-117">Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="9422f-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="9422f-118">Abrufen per Pull von einem SMB-Server</span><span class="sxs-lookup"><span data-stu-id="9422f-118">Pulling from an SMB server</span></span>

<span data-ttu-id="9422f-119">Wenn der Pullserver nicht als Webdienst, sondern als SMB-Dateifreigabe konfiguriert wurde, legen Sie **DscFileDownloadManager** anstelle von **WebDownLoadManager** fest.</span><span class="sxs-lookup"><span data-stu-id="9422f-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="9422f-120">**DscFileDownloadManager** verwendet eine **SourcePath**-Eigenschaft anstelle von **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="9422f-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="9422f-121">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einer SMB-Freigabe namens „SmbDscShare“ auf einem Server namens „CONTOSO-SERVER“:</span><span class="sxs-lookup"><span data-stu-id="9422f-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
{ 
    LocalConfigurationManager 
    { 
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30; 
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    } 
} 
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="9422f-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9422f-122">See Also</span></span>

- [<span data-ttu-id="9422f-123">Einrichten eines DSC-Webpullservers</span><span class="sxs-lookup"><span data-stu-id="9422f-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="9422f-124">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="9422f-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)

