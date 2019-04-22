---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Erste Schritte mit DSC für Linux
ms.openlocfilehash: a18b226d4b2d8b8e1ba8b4168ec6ad8f73c73c42
ms.sourcegitcommit: 3f6002e7109373eda31cc65fc84d2600447cb7e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59506834"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="fcbea-103">Erste Schritte mit DSC für Linux</span><span class="sxs-lookup"><span data-stu-id="fcbea-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="fcbea-104">In diesem Thema werden die ersten Schritte mit PowerShell DSC für Linux erläutert.</span><span class="sxs-lookup"><span data-stu-id="fcbea-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="fcbea-105">Allgemeine Informationen zu DSC finden Sie unter [Erste Schritte mit Windows PowerShell DSC](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="fcbea-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="fcbea-106">Unterstützte Linux-Betriebssystemversionen</span><span class="sxs-lookup"><span data-stu-id="fcbea-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="fcbea-107">Die folgenden Linux-Betriebssystemversionen werden für DSC unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fcbea-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="fcbea-108">CentOS 5, 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="fcbea-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="fcbea-109">Debian GNU/Linux 6, 7 und 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="fcbea-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="fcbea-110">Oracle Linux 5, 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="fcbea-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="fcbea-111">Red Hat Enterprise Linux Server 5, 6 und 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="fcbea-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="fcbea-112">SUSE Linux Enterprise Server 10, 11 und 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="fcbea-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="fcbea-113">Ubuntu Server 12.04 LTS, 14.04 LTS und 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="fcbea-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="fcbea-114">In der folgenden Tabelle werden die erforderlichen Paketabhängigkeiten für DSC für Linux beschrieben.</span><span class="sxs-lookup"><span data-stu-id="fcbea-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="fcbea-115">Erforderliches Paket</span><span class="sxs-lookup"><span data-stu-id="fcbea-115">Required package</span></span> |  <span data-ttu-id="fcbea-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fcbea-116">Description</span></span> |  <span data-ttu-id="fcbea-117">Mindestversion</span><span class="sxs-lookup"><span data-stu-id="fcbea-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="fcbea-118">glibc</span><span class="sxs-lookup"><span data-stu-id="fcbea-118">glibc</span></span>| <span data-ttu-id="fcbea-119">GNU-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="fcbea-119">GNU Library</span></span>| <span data-ttu-id="fcbea-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="fcbea-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="fcbea-121">python</span><span class="sxs-lookup"><span data-stu-id="fcbea-121">python</span></span>| <span data-ttu-id="fcbea-122">Python</span><span class="sxs-lookup"><span data-stu-id="fcbea-122">Python</span></span>| <span data-ttu-id="fcbea-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="fcbea-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="fcbea-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="fcbea-124">omiserver</span></span>| <span data-ttu-id="fcbea-125">Open Management Infrastructure</span><span class="sxs-lookup"><span data-stu-id="fcbea-125">Open Management Infrastructure</span></span>| <span data-ttu-id="fcbea-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="fcbea-126">1.0.8.1</span></span>|
| <span data-ttu-id="fcbea-127">openssl</span><span class="sxs-lookup"><span data-stu-id="fcbea-127">openssl</span></span>| <span data-ttu-id="fcbea-128">OpenSSL-Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="fcbea-128">OpenSSL Libraries</span></span>| <span data-ttu-id="fcbea-129">0.9.8 oder 1.0</span><span class="sxs-lookup"><span data-stu-id="fcbea-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="fcbea-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="fcbea-130">ctypes</span></span>| <span data-ttu-id="fcbea-131">Python CTypes-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="fcbea-131">Python CTypes library</span></span>| <span data-ttu-id="fcbea-132">Muss mit Python-Version übereinstimmen</span><span class="sxs-lookup"><span data-stu-id="fcbea-132">Must match Python version</span></span>|
| <span data-ttu-id="fcbea-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="fcbea-133">libcurl</span></span>| <span data-ttu-id="fcbea-134">cURL http-Clientbibliothek</span><span class="sxs-lookup"><span data-stu-id="fcbea-134">cURL http client library</span></span>| <span data-ttu-id="fcbea-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="fcbea-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="fcbea-136">Installieren von DSC für Linux</span><span class="sxs-lookup"><span data-stu-id="fcbea-136">Installing DSC for Linux</span></span>

<span data-ttu-id="fcbea-137">Sie müssen vor der Installation von DSC für Linux die [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) installieren.</span><span class="sxs-lookup"><span data-stu-id="fcbea-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="fcbea-138">Installieren von OMI</span><span class="sxs-lookup"><span data-stu-id="fcbea-138">Installing OMI</span></span>

<span data-ttu-id="fcbea-139">DSC für Linux erfordert den Open Management Infrastructure (OMI) CIM-Server, Version 1.0.8.1 oder höher.</span><span class="sxs-lookup"><span data-stu-id="fcbea-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="fcbea-140">OMI kann von The Open Group heruntergeladen werden: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="fcbea-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="fcbea-141">Zum Installieren von OMI installieren Sie das Ihrem Linux-System entsprechende Paket (RPM oder DEB), die OpenSSL-Version (ssl_098 oder ssl_100) und die Architektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="fcbea-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="fcbea-142">RPM-Pakete eignen sich für CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="fcbea-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="fcbea-143">DEB-Pakete sind für Debian GNU/Linux und Ubuntu Server geeignet.</span><span class="sxs-lookup"><span data-stu-id="fcbea-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="fcbea-144">Die ssl_098-Pakete eignen sich für Computer mit installiertem OpenSSL 0.9.8, während die ssl_100 Pakete für Computer mit installiertem OpenSSL 1.0 geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="fcbea-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="fcbea-145">Um die installierte OpenSSL-Version zu bestimmen, führen Sie den Befehl `openssl version` aus.</span><span class="sxs-lookup"><span data-stu-id="fcbea-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="fcbea-146">Führen Sie den folgenden Befehl aus, um OMI auf einem CentOS 7 x64-System zu installieren.</span><span class="sxs-lookup"><span data-stu-id="fcbea-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="fcbea-147">Installieren von DSC</span><span class="sxs-lookup"><span data-stu-id="fcbea-147">Installing DSC</span></span>

<span data-ttu-id="fcbea-148">DSC für Linux kann [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="fcbea-149">Zum Installieren von DSC installieren Sie das Ihrem Linux-System entsprechende Paket (RPM oder DEB), die OpenSSL-Version (ssl_098 oder ssl_100) und die Architektur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="fcbea-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="fcbea-150">RPM-Pakete eignen sich für CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server und Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="fcbea-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="fcbea-151">DEB-Pakete sind für Debian GNU/Linux und Ubuntu Server geeignet.</span><span class="sxs-lookup"><span data-stu-id="fcbea-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="fcbea-152">Die ssl_098-Pakete eignen sich für Computer mit installiertem OpenSSL 0.9.8, während die ssl_100 Pakete für Computer mit installiertem OpenSSL 1.0 geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="fcbea-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="fcbea-153">Um die installierte OpenSSL-Version zu bestimmen, führen Sie den Befehl „openssl version“ aus.</span><span class="sxs-lookup"><span data-stu-id="fcbea-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="fcbea-154">Führen Sie den folgenden Befehl aus, um DSC auf einem CentOS 7 x64-System zu installieren.</span><span class="sxs-lookup"><span data-stu-id="fcbea-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="fcbea-155">Verwenden von DSC für Linux</span><span class="sxs-lookup"><span data-stu-id="fcbea-155">Using DSC for Linux</span></span>

<span data-ttu-id="fcbea-156">In den folgenden Abschnitten wird erläutert, wie DSC-Konfigurationen erstellt und auf Linux-Computern ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="fcbea-157">Erstellen eines MOF-Konfigurationsdokuments</span><span class="sxs-lookup"><span data-stu-id="fcbea-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="fcbea-158">Das Windows PowerShell-Schlüsselwort „Configuration“ wird wie für Windows-Computer verwendet, um eine Konfiguration für Linux-Computer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fcbea-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="fcbea-159">Es folgen die Schritte zum Erstellen eines Konfigurationsdokuments für einen Linux-Computer mithilfe von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcbea-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="fcbea-160">Importieren Sie das Modul „nx“.</span><span class="sxs-lookup"><span data-stu-id="fcbea-160">Import the nx module.</span></span> <span data-ttu-id="fcbea-161">Das Windows PowerShell-Modul „nx“ enthält das Schema für integrierte Ressourcen für DSC für Linux und muss auf dem lokalen Computer installiert und in die Konfiguration importiert werden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="fcbea-162">Zum Installieren des Moduls „nx“ kopieren Sie das Verzeichnis dieses Moduls entweder in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` oder in `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="fcbea-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="fcbea-163">Das Modul „nx“ ist im Installationspaket von DSC für Linux enthalten.</span><span class="sxs-lookup"><span data-stu-id="fcbea-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="fcbea-164">Verwenden Sie zum Importieren des Moduls „nx“ in Ihre Konfiguration den Befehl `Import-DSCResource`:</span><span class="sxs-lookup"><span data-stu-id="fcbea-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="fcbea-165">Definieren Sie eine Konfiguration, und generieren Sie das Konfigurationsdokument:</span><span class="sxs-lookup"><span data-stu-id="fcbea-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="fcbea-166">Übertragen der Konfiguration per Push auf den Linux-Computer</span><span class="sxs-lookup"><span data-stu-id="fcbea-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="fcbea-167">Konfigurationsdokumente (MOF-Dateien) können mit dem Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) per Push auf den Linux-Computer übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="fcbea-168">Verwenden Sie eine CIMSession, um dieses Cmdlet zusammen mit den Cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) und [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) remote auf einem Linux-Computer zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="fcbea-169">Das Cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) dient zum Starten einer CIMSession mit dem Linux-Computer.</span><span class="sxs-lookup"><span data-stu-id="fcbea-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="fcbea-170">Der folgende Code zeigt, wie Sie eine CIMSession für DSC für Linux starten.</span><span class="sxs-lookup"><span data-stu-id="fcbea-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="fcbea-171">Im Pushmodus müssen die Anmeldeinformationen des Benutzers denen des Benutzers „root“ auf dem Linux-Computer entsprechen.</span><span class="sxs-lookup"><span data-stu-id="fcbea-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="fcbea-172">Für DSC für Linux werden nur SSL/TLS-Verbindungen unterstützt. Der Befehl `New-CimSession` muss mit auf „$true“ festgelegtem „–UseSSL“-Parameter aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="fcbea-173">Das von OMI (für DSC) verwendete SSL-Zertifikat wird in der Datei `/opt/omi/etc/omiserver.conf` mit den Eigenschaften „pemfile“ und „keyfile“ angegeben.</span><span class="sxs-lookup"><span data-stu-id="fcbea-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="fcbea-174">Wenn diesem Zertifikat vom Windows-Computer, auf dem Sie das Cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) ausführen, nicht vertraut wird, können Sie in den Optionen für „CIMSession“ die Überprüfung des Zertifikats ignorieren:</span><span class="sxs-lookup"><span data-stu-id="fcbea-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options:</span></span> `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`

<span data-ttu-id="fcbea-175">Führen Sie den folgenden Befehl aus, um die DSC-Konfiguration per Push auf den Linux-Knoten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="fcbea-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="fcbea-176">Verteilen der Konfiguration mit einem Pullserver</span><span class="sxs-lookup"><span data-stu-id="fcbea-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="fcbea-177">Konfigurationen können mithilfe eines Pullservers wie bei Windows-Computern auch an Linux-Computer verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="fcbea-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="fcbea-178">Eine Anleitung zur Verwendung eines Pullservers finden Sie unter [Windows PowerShell DSC – Pullserver](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="fcbea-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="fcbea-179">Weitere Informationen und Einschränkungen im Zusammenhang mit der Verwendung von Linux-Computern mit einem Pullserver finden Sie die Versionshinweisen zu DSC für Linux.</span><span class="sxs-lookup"><span data-stu-id="fcbea-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="fcbea-180">Arbeiten mit lokalen Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="fcbea-180">Working with configurations locally</span></span>

<span data-ttu-id="fcbea-181">DSC für Linux bietet Skripts für das Ausführen von Konfigurationsaufgaben auf einem lokalen Linux-Computer.</span><span class="sxs-lookup"><span data-stu-id="fcbea-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="fcbea-182">Diese Skripts befinden sich in `/opt/microsoft/dsc/Scripts` und umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="fcbea-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="fcbea-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="fcbea-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="fcbea-184">Gibt die aktuell auf dem Computer installierte Konfiguration zurück.</span><span class="sxs-lookup"><span data-stu-id="fcbea-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="fcbea-185">Dies ist vergleichbar mit dem Windows PowerShell-Cmdlet `Get-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="fcbea-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="fcbea-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="fcbea-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="fcbea-187">Gibt die aktuell auf dem Computer installierte Metakonfiguration zurück.</span><span class="sxs-lookup"><span data-stu-id="fcbea-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="fcbea-188">Vergleichbar mit dem Cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="fcbea-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="fcbea-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="fcbea-189">InstallModule.py</span></span>

<span data-ttu-id="fcbea-190">Installiert ein benutzerdefiniertes DSC-Ressourcenmodul.</span><span class="sxs-lookup"><span data-stu-id="fcbea-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="fcbea-191">Erfordert den Pfad zu einer ZIP-Datei, die die freigegebene Objektbibliothek des Moduls und die MOF-Dateien mit dem Schema enthält.</span><span class="sxs-lookup"><span data-stu-id="fcbea-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="fcbea-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="fcbea-192">RemoveModule.py</span></span>

<span data-ttu-id="fcbea-193">Entfernt ein benutzerdefiniertes DSC-Ressourcenmodul.</span><span class="sxs-lookup"><span data-stu-id="fcbea-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="fcbea-194">Erfordert die Angabe des Namens des Moduls, das entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fcbea-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="fcbea-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="fcbea-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="fcbea-196">Wendet eine MOF-Konfigurationsdatei auf den Computer an.</span><span class="sxs-lookup"><span data-stu-id="fcbea-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="fcbea-197">Vergleichbar mit dem Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="fcbea-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="fcbea-198">Erfordert die Angabe des Pfads zur anzuwendenden MOF-Konfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="fcbea-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="fcbea-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="fcbea-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="fcbea-200">Wendet eine MOF-Metakonfigurationsdatei auf den Computer an.</span><span class="sxs-lookup"><span data-stu-id="fcbea-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="fcbea-201">Vergleichbar mit dem Cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="fcbea-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="fcbea-202">Erfordert die Angabe des Pfads zur anzuwendenden MOF-Metakonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="fcbea-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="fcbea-203">PowerShell – DSC für Linux – Protokolldateien</span><span class="sxs-lookup"><span data-stu-id="fcbea-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="fcbea-204">Die folgenden Protokolldateien werden für DSC-für-Linux-Nachrichten generiert.</span><span class="sxs-lookup"><span data-stu-id="fcbea-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="fcbea-205">Protokolldatei</span><span class="sxs-lookup"><span data-stu-id="fcbea-205">Log file</span></span>|<span data-ttu-id="fcbea-206">Verzeichnis</span><span class="sxs-lookup"><span data-stu-id="fcbea-206">Directory</span></span>|<span data-ttu-id="fcbea-207">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fcbea-207">Description</span></span>|
|---|---|---|
|**<span data-ttu-id="fcbea-208">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="fcbea-208">omiserver.log</span></span>**|`/var/opt/omi/log`|<span data-ttu-id="fcbea-209">Meldungen im Zusammenhang mit dem Betrieb des OMI CIM-Servers.</span><span class="sxs-lookup"><span data-stu-id="fcbea-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|**<span data-ttu-id="fcbea-210">dsc.log</span><span class="sxs-lookup"><span data-stu-id="fcbea-210">dsc.log</span></span>**|`/var/opt/omi/log`|<span data-ttu-id="fcbea-211">Meldungen im Zusammenhang mit dem Betrieb des lokalen Konfigurations-Managers (LCM) und DSC-Ressourcenvorgängen.</span><span class="sxs-lookup"><span data-stu-id="fcbea-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
