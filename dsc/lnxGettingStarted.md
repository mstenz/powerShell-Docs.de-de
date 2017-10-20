---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Erste Schritte mit DSC für Linux"
ms.openlocfilehash: f88167cd039077574c3a84aa07ba78186adfa181
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2017
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="4c453-103">Erste Schritte mit DSC für Linux</span><span class="sxs-lookup"><span data-stu-id="4c453-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="4c453-104">In diesem Thema werden die ersten Schritte mit PowerShell DSC für Linux erläutert.</span><span class="sxs-lookup"><span data-stu-id="4c453-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="4c453-105">Allgemeine Informationen zu DSC finden Sie unter [Erste Schritte mit Windows PowerShell DSC](overview.md).</span><span class="sxs-lookup"><span data-stu-id="4c453-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="4c453-106">Unterstützte Linux-Betriebssystemversionen</span><span class="sxs-lookup"><span data-stu-id="4c453-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="4c453-107">Die folgenden Linux-Betriebssystemversionen werden für DSC unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4c453-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="4c453-108">CentOS 5, 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="4c453-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="4c453-109">Debian GNU/Linux 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="4c453-109">Debian GNU/Linux 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="4c453-110">Oracle Linux 5, 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="4c453-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="4c453-111">Red Hat Enterprise Linux Server 5, 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="4c453-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="4c453-112">SUSE Linux Enterprise Server 10, 11 und 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="4c453-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="4c453-113">Ubuntu Server 12.04 LTS und 14.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="4c453-113">Ubuntu Server 12.04 LTS and 14.04 LTS (x86/x64)</span></span>

<span data-ttu-id="4c453-114">In der folgenden Tabelle werden die erforderlichen Paketabhängigkeiten für DSC für Linux beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4c453-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="4c453-115">Erforderliches Paket</span><span class="sxs-lookup"><span data-stu-id="4c453-115">Required package</span></span> |  <span data-ttu-id="4c453-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4c453-116">Description</span></span> |  <span data-ttu-id="4c453-117">Mindestversion</span><span class="sxs-lookup"><span data-stu-id="4c453-117">Minimum version</span></span> | 
|---|---|---|
| <span data-ttu-id="4c453-118">glibc</span><span class="sxs-lookup"><span data-stu-id="4c453-118">glibc</span></span>| <span data-ttu-id="4c453-119">GNU-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4c453-119">GNU Library</span></span>| <span data-ttu-id="4c453-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="4c453-120">2…4 – 31.30</span></span>| 
| <span data-ttu-id="4c453-121">python</span><span class="sxs-lookup"><span data-stu-id="4c453-121">python</span></span>| <span data-ttu-id="4c453-122">Python</span><span class="sxs-lookup"><span data-stu-id="4c453-122">Python</span></span>| <span data-ttu-id="4c453-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="4c453-123">2.4 – 3.4</span></span>| 
| <span data-ttu-id="4c453-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="4c453-124">omiserver</span></span>| <span data-ttu-id="4c453-125">Open Management Infrastructure</span><span class="sxs-lookup"><span data-stu-id="4c453-125">Open Management Infrastructure</span></span>| <span data-ttu-id="4c453-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="4c453-126">1.0.8.1</span></span>| 
| <span data-ttu-id="4c453-127">openssl</span><span class="sxs-lookup"><span data-stu-id="4c453-127">openssl</span></span>| <span data-ttu-id="4c453-128">OpenSSL-Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="4c453-128">OpenSSL Libraries</span></span>| <span data-ttu-id="4c453-129">0.9.8 oder 1.0</span><span class="sxs-lookup"><span data-stu-id="4c453-129">0.9.8 or 1.0</span></span>| 
| <span data-ttu-id="4c453-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="4c453-130">ctypes</span></span>| <span data-ttu-id="4c453-131">Python CTypes-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="4c453-131">Python CTypes library</span></span>| <span data-ttu-id="4c453-132">Muss mit Python-Version übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="4c453-132">Must match Python version</span></span>| 
| <span data-ttu-id="4c453-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="4c453-133">libcurl</span></span>| <span data-ttu-id="4c453-134">cURL http-Clientbibliothek</span><span class="sxs-lookup"><span data-stu-id="4c453-134">cURL http client library</span></span>| <span data-ttu-id="4c453-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="4c453-135">7.15.1</span></span>| 

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="4c453-136">Installieren von DSC für Linux</span><span class="sxs-lookup"><span data-stu-id="4c453-136">Installing DSC for Linux</span></span>

<span data-ttu-id="4c453-137">Sie müssen vor der Installation von DSC für Linux die [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) installieren.</span><span class="sxs-lookup"><span data-stu-id="4c453-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="4c453-138">Installieren von OMI</span><span class="sxs-lookup"><span data-stu-id="4c453-138">Installing OMI</span></span>

<span data-ttu-id="4c453-139">DSC für Linux erfordert den Open Management Infrastructure (OMI) CIM-Server, Version 1.0.8.1 oder höher.</span><span class="sxs-lookup"><span data-stu-id="4c453-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="4c453-140">OMI kann unter The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="4c453-141">Zum Installieren von OMI installieren Sie das Ihrem Linux-System entsprechende Paket (RPM oder DEB), die OpenSSL-Version (ssl_098 oder ssl_100) und die Architektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="4c453-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="4c453-142">RPM-Pakete eignen sich für CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="4c453-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="4c453-143">DEB-Pakete sind für Debian GNU/Linux und Ubuntu Server geeignet.</span><span class="sxs-lookup"><span data-stu-id="4c453-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="4c453-144">Die ssl_098-Pakete eignen sich für Computer mit installiertem OpenSSL 0.9.8, während die ssl_100 Pakete für Computer mit installiertem OpenSSL 1.0 geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="4c453-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="4c453-145">**Hinweis**: Um die installierte OpenSSL-Version zu bestimmen, führen Sie den Befehl `openssl version` aus.</span><span class="sxs-lookup"><span data-stu-id="4c453-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="4c453-146">Führen Sie den folgenden Befehl aus, um OMI auf einem CentOS 7 x64-System zu installieren.</span><span class="sxs-lookup"><span data-stu-id="4c453-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="4c453-147">Installieren von DSC</span><span class="sxs-lookup"><span data-stu-id="4c453-147">Installing DSC</span></span>

<span data-ttu-id="4c453-148">DSC für Linux kann [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span> 

<span data-ttu-id="4c453-149">Zum Installieren von DSC installieren Sie das Ihrem Linux-System entsprechende Paket (RPM oder DEB), die OpenSSL-Version (ssl_098 oder ssl_100) und die Architektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="4c453-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="4c453-150">RPM-Pakete eignen sich für CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="4c453-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="4c453-151">DEB-Pakete sind für Debian GNU/Linux und Ubuntu Server geeignet.</span><span class="sxs-lookup"><span data-stu-id="4c453-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="4c453-152">Die ssl_098-Pakete eignen sich für Computer mit installiertem OpenSSL 0.9.8, während die ssl_100 Pakete für Computer mit installiertem OpenSSL 1.0 geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="4c453-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="4c453-153">**Hinweis**: Um die installierte OpenSSL-Version zu bestimmen, führen Sie den Befehl „openssl“ aus.</span><span class="sxs-lookup"><span data-stu-id="4c453-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>
 
<span data-ttu-id="4c453-154">Führen Sie den folgenden Befehl aus, um DSC auf einem CentOS 7 x64-System zu installieren.</span><span class="sxs-lookup"><span data-stu-id="4c453-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="4c453-155">Verwenden von DSC für Linux</span><span class="sxs-lookup"><span data-stu-id="4c453-155">Using DSC for Linux</span></span>

<span data-ttu-id="4c453-156">In den folgenden Abschnitten wird erläutert, wie DSC-Konfigurationen erstellt und auf Linux-Computern ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="4c453-157">Erstellen eines MOF-Konfigurationsdokuments</span><span class="sxs-lookup"><span data-stu-id="4c453-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="4c453-158">Das Windows PowerShell-Schlüsselwort „Configuration“ wird wie für Windows-Computer verwendet, um eine Konfiguration für Linux-Computer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4c453-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="4c453-159">Es folgen die Schritte zum Erstellen eines Konfigurationsdokuments für einen Linux-Computer mithilfe von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c453-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="4c453-160">Importieren Sie das Modul „nx“.</span><span class="sxs-lookup"><span data-stu-id="4c453-160">Import the nx module.</span></span> <span data-ttu-id="4c453-161">Das Windows PowerShell-Modul „nx“ enthält das Schema für integrierte Ressourcen für DSC für Linux und muss auf dem lokalen Computer installiert und in die Konfiguration importiert werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="4c453-162">Zum Installieren des Moduls „nx“ kopieren Sie das Verzeichnis dieses Moduls in entweder `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` oder `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="4c453-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="4c453-163">Das Modul „nx“ ist im Installationspaket (MSI) von DSC für Linux enthalten.</span><span class="sxs-lookup"><span data-stu-id="4c453-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="4c453-164">Verwenden Sie zum Importieren des Moduls „nx“ in Ihre Konfiguration den Befehl __Import-DSCResource__:</span><span class="sxs-lookup"><span data-stu-id="4c453-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="4c453-165">Definieren Sie eine Konfiguration, und generieren Sie das Konfigurationsdokument:</span><span class="sxs-lookup"><span data-stu-id="4c453-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="4c453-166">Übertragen der Konfiguration per Push auf den Linux-Computer</span><span class="sxs-lookup"><span data-stu-id="4c453-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="4c453-167">Konfigurationsdokumente (MOF-Dateien) können mit dem Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) per Push auf den Linux-Computer übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="4c453-168">Verwenden Sie eine CIMSession, um dieses Cmdlet zusammen mit den Cmdlets [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) und [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) remote auf einem Linux-Computer zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4c453-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="4c453-169">Das Cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) dient zum Starten einer CIMSession mit dem Linux-Computer.</span><span class="sxs-lookup"><span data-stu-id="4c453-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="4c453-170">Der folgende Code zeigt, wie Sie eine CIMSession für DSC für Linux starten.</span><span class="sxs-lookup"><span data-stu-id="4c453-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> <span data-ttu-id="4c453-171">**Hinweis**:</span><span class="sxs-lookup"><span data-stu-id="4c453-171">**Note**:</span></span>
* <span data-ttu-id="4c453-172">Im Pushmodus müssen die Anmeldeinformationen des Benutzers denen des Benutzers „root“ auf dem Linux-Computer entsprechen.</span><span class="sxs-lookup"><span data-stu-id="4c453-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="4c453-173">Für DSC für Linux werden nur SSL/TLS-Verbindungen unterstützt. Der Befehl „New-CimSession“ muss mit auf „$true“ festgelegtem „–UseSSL“-Parameter aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="4c453-174">Das von OMI (für DSC) verwendete SSL-Zertifikat wird in der Datei `/opt/omi/etc/omiserver.conf` mit den Eigenschaften „pemfile“ und „keyfile“ angegeben.</span><span class="sxs-lookup"><span data-stu-id="4c453-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="4c453-175">Wenn diesem Zertifikat vom Windows-Computer nicht vertraut wird, auf dem Sie das Cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) ausführen, können Sie in den Optionen für „CIMSession“ die Überprüfung des Zertifikats ignorieren: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="4c453-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="4c453-176">Führen Sie den folgenden Befehl aus, um die DSC-Konfiguration per Push auf den Linux-Knoten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="4c453-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="4c453-177">Verteilen der Konfiguration mit einem Pullserver</span><span class="sxs-lookup"><span data-stu-id="4c453-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="4c453-178">Konfigurationen können mithilfe eines Pullservers wie bei Windows-Computern auch an Linux-Computer verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="4c453-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="4c453-179">Eine Anleitung zur Verwendung eines Pullservers finden Sie unter [Windows PowerShell DSC – Pullserver](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="4c453-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="4c453-180">Weitere Informationen und Einschränkungen im Zusammenhang mit der Verwendung von Linux-Computern mit einem Pullserver finden Sie die Versionshinweisen zu DSC für Linux.</span><span class="sxs-lookup"><span data-stu-id="4c453-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="4c453-181">Arbeiten mit lokalen Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4c453-181">Working with configurations locally</span></span>

<span data-ttu-id="4c453-182">DSC für Linux bietet Skripts für das Ausführen von Konfigurationsaufgaben auf einem lokalen Linux-Computer.</span><span class="sxs-lookup"><span data-stu-id="4c453-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="4c453-183">Diese Skripts befinden sich in `/opt/microsoft/dsc/Scripts` und umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="4c453-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="4c453-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="4c453-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="4c453-185">Gibt die aktuell auf dem Computer installierte Konfiguration zurück.</span><span class="sxs-lookup"><span data-stu-id="4c453-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="4c453-186">Vergleichbar mit dem Windows PowerShell-Cmdlet „Get-DscConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="4c453-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="4c453-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="4c453-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="4c453-188">Gibt die aktuell auf dem Computer installierte Metakonfiguration zurück.</span><span class="sxs-lookup"><span data-stu-id="4c453-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="4c453-189">Vergleichbar mit dem Cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c453-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="4c453-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="4c453-190">InstallModule.py</span></span>

 <span data-ttu-id="4c453-191">Installiert ein benutzerdefiniertes DSC-Ressourcenmodul.</span><span class="sxs-lookup"><span data-stu-id="4c453-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="4c453-192">Erfordert den Pfad zu einer ZIP-Datei, die die freigegebene Objektbibliothek des Moduls und die MOF-Dateien mit dem Schema enthält.</span><span class="sxs-lookup"><span data-stu-id="4c453-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="4c453-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="4c453-193">RemoveModule.py</span></span>

 <span data-ttu-id="4c453-194">Entfernt ein benutzerdefiniertes DSC-Ressourcenmodul.</span><span class="sxs-lookup"><span data-stu-id="4c453-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="4c453-195">Erfordert die Angabe des Namens des Moduls, das entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="4c453-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="4c453-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="4c453-196">StartDscLocalConfigurationManager.py</span></span> 

 <span data-ttu-id="4c453-197">Wendet eine MOF-Konfigurationsdatei auf den Computer an.</span><span class="sxs-lookup"><span data-stu-id="4c453-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="4c453-198">Vergleichbar mit dem Cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c453-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="4c453-199">Erfordert die Angabe des Pfads zur anzuwendenden MOF-Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="4c453-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="4c453-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="4c453-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="4c453-201">Wendet eine MOF-Metakonfigurationsdatei auf den Computer an.</span><span class="sxs-lookup"><span data-stu-id="4c453-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="4c453-202">Vergleichbar mit dem Cmdlet [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx).</span><span class="sxs-lookup"><span data-stu-id="4c453-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="4c453-203">Erfordert die Angabe des Pfads zur anzuwendenden MOF-Metakonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="4c453-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="4c453-204">PowerShell – DSC für Linux – Protokolldateien</span><span class="sxs-lookup"><span data-stu-id="4c453-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="4c453-205">Die folgenden Protokolldateien werden für DSC-für-Linux-Nachrichten generiert.</span><span class="sxs-lookup"><span data-stu-id="4c453-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="4c453-206">Protokolldatei</span><span class="sxs-lookup"><span data-stu-id="4c453-206">Log file</span></span>|<span data-ttu-id="4c453-207">Verzeichnis</span><span class="sxs-lookup"><span data-stu-id="4c453-207">Directory</span></span>|<span data-ttu-id="4c453-208">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4c453-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="4c453-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="4c453-209">omiserver.log</span></span>|<span data-ttu-id="4c453-210">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="4c453-210">/var/opt/omi/log</span></span>|<span data-ttu-id="4c453-211">Meldungen im Zusammenhang mit dem Betrieb des OMI CIM-Servers.</span><span class="sxs-lookup"><span data-stu-id="4c453-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="4c453-212">dsc.log</span><span class="sxs-lookup"><span data-stu-id="4c453-212">dsc.log</span></span>|<span data-ttu-id="4c453-213">/var/opt/omi/log</span><span class="sxs-lookup"><span data-stu-id="4c453-213">/var/opt/omi/log</span></span>|<span data-ttu-id="4c453-214">Meldungen im Zusammenhang mit dem Betrieb des lokalen Konfigurations-Managers (LCM) und DSC-Ressourcenvorgängen.</span><span class="sxs-lookup"><span data-stu-id="4c453-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|

