---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954607"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="4c227-103">Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC</span><span class="sxs-lookup"><span data-stu-id="4c227-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c227-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4c227-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="4c227-105">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="4c227-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="4c227-106">Der in diesem Thema beschriebene Registrierungsschlüssel **DSCAutomationHostEnabled** ist in PowerShell 4.0 nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4c227-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="4c227-107">Informationen dazu, wie Sie neue virtuelle Computer beim ersten Hochfahren in PowerShell 4.0 konfigurieren, finden Sie unter [Sie möchten Ihre Computer mithilfe von DSC beim ersten Hochfahren automatisch konfigurieren?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span><span class="sxs-lookup"><span data-stu-id="4c227-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="4c227-108">Um diese Beispiele auszuführen, benötigen Sie:</span><span class="sxs-lookup"><span data-stu-id="4c227-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="4c227-109">Eine startbare virtuelle Festplatte (VHD).</span><span class="sxs-lookup"><span data-stu-id="4c227-109">A bootable VHD to work with.</span></span> <span data-ttu-id="4c227-110">Sie können ein ISO-Image mit einer Evaluierungsversion von Windows Server 2016 aus dem [TechNet-Evaluierungscenter](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="4c227-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="4c227-111">Anweisungen finden Sie zum Erstellen einer VHD aus einem ISO-Image finden Sie unter [Erstellen startbarer virtueller Festplatten](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="4c227-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="4c227-112">Ein Hostcomputer, auf dem Hyper-V aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="4c227-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="4c227-113">Informationen hierzu finden Sie unter [Übersicht über Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="4c227-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="4c227-114">Mithilfe von DSC können Sie die Installation und Konfiguration von Software beim ersten Hochfahren eines Computers automatisieren.</span><span class="sxs-lookup"><span data-stu-id="4c227-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="4c227-115">Sie können dazu entweder ein MOF-Konfigurationsdokument oder eine Metakonfiguration zu startbaren Medien (z. B. einer VHD) hinzufügen, die beim ersten Startvorgang ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4c227-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="4c227-116">Dieses Verhalten wird vom [DSCAutomationHostEnabled-Registrierungsschlüssel](DSCAutomationHostEnabled.md) unter `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` angegeben.</span><span class="sxs-lookup"><span data-stu-id="4c227-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="4c227-117">Standardmäßig ist der Wert dieses Schlüssels 2, wodurch DSC zur Startzeit ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="4c227-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="4c227-118">Wenn DSC nicht zur Startzeit ausgeführt werden soll, legen Sie den Wert des Registrierungsschlüssels [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) auf 0 fest.</span><span class="sxs-lookup"><span data-stu-id="4c227-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="4c227-119">Hinzufügen eines MOF-Konfigurationsdokuments zu einer VHD</span><span class="sxs-lookup"><span data-stu-id="4c227-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="4c227-120">Hinzufügen einer Metakonfiguration zu einer VHD</span><span class="sxs-lookup"><span data-stu-id="4c227-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="4c227-121">Deaktivieren von DSC zur Startzeit</span><span class="sxs-lookup"><span data-stu-id="4c227-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="4c227-122">Sie können zu einem Computer gleichzeitig `Pending.mof` und `MetaConfig.mof` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4c227-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="4c227-123">Wenn beide Dateien vorhanden sind, haben die Einstellungen von `MetaConfig.mof` Vorrang.</span><span class="sxs-lookup"><span data-stu-id="4c227-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="4c227-124">Hinzufügen eines MOF-Konfigurationsdokuments zu einer VHD</span><span class="sxs-lookup"><span data-stu-id="4c227-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="4c227-125">Um eine Konfiguration beim ersten Hochfahren anzuwenden, können Sie ein kompiliertes MOF-Konfigurationsdokument als `Pending.mof`-Datei zur VHD hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4c227-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="4c227-126">Ist der Registrierungsschlüssel **DSCAutomationHostEnabled** auf 2 (Standardwert) festgelegt, wird die in `Pending.mof` definierte Konfiguration von DSC angewendet, sobald der Computer zum ersten Mal gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="4c227-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="4c227-127">In diesem Beispiel wird die folgende Konfiguration verwendet, durch die IIS auf dem neuen Computer installiert wird:</span><span class="sxs-lookup"><span data-stu-id="4c227-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="4c227-128">So fügen Sie ein MOF-Konfigurationsdokument zur VHD hinzu</span><span class="sxs-lookup"><span data-stu-id="4c227-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="4c227-129">Stellen Sie die VHD, zu der Sie die Konfiguration hinzufügen möchten, mit dem Cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) bereit.</span><span class="sxs-lookup"><span data-stu-id="4c227-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="4c227-130">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4c227-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="4c227-131">Auf einem Computer mit PowerShell 5.0 oder höher speichern Sie die oben stehende Konfiguration (**SampleIISInstall**) als PowerShell-Skriptdatei (.ps1).</span><span class="sxs-lookup"><span data-stu-id="4c227-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="4c227-132">Navigieren Sie in einer PowerShell-Konsole zu dem Ordner, in dem Sie die PS1-Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="4c227-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="4c227-133">Führen Sie die folgenden PowerShell-Befehle zum Kompilieren des MOF-Dokuments aus (Informationen zum Kompilieren von DSC-Konfigurationen finden Sie unter [DSC-Konfigurationen](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="4c227-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="4c227-134">Dadurch wird eine `localhost.mof`-Datei in einen neuen Ordner namens `SampleIISInstall` erstellt.</span><span class="sxs-lookup"><span data-stu-id="4c227-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="4c227-135">Benennen Sie die Datei in `Pending.mof`um, und verschieben Sie sie an den richtigen Speicherort auf der virtuellen Festplatte. Verwenden Sie dazu das Cmdlet [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="4c227-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="4c227-136">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4c227-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="4c227-137">Heben Sie die VHD-Bereitstellung durch Aufrufen des Cmdlets [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) auf.</span><span class="sxs-lookup"><span data-stu-id="4c227-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="4c227-138">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4c227-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="4c227-139">Erstellen Sie einen virtuellen Computer mithilfe der VHD, auf der Sie das DSC MOF-Dokument installiert haben.</span><span class="sxs-lookup"><span data-stu-id="4c227-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="4c227-140">IIS wird nach dem ersten Hochfahren und der Installation des Betriebssystems installiert.</span><span class="sxs-lookup"><span data-stu-id="4c227-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="4c227-141">Sie können dies überprüfen, indem Sie das Cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4c227-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="4c227-142">Hinzufügen einer Metakonfiguration zu einer VHD</span><span class="sxs-lookup"><span data-stu-id="4c227-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="4c227-143">Sie können einen Computer auch so konfigurieren, dass eine Konfiguration beim ersten Hochfahren abgerufen wird, indem Sie eine Metakonfiguration als `MetaConfig.mof`-Datei zur VHD hinzufügen (siehe [Configuring the Local Configuration Manager (LCM) (Konfigurieren des lokalen Konfigurations-Managers)](../managing-nodes/metaConfig.md)).</span><span class="sxs-lookup"><span data-stu-id="4c227-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="4c227-144">Ist der Registrierungsschlüssel **DSCAutomationHostEnabled** auf 2 (Standardwert) festgelegt, wird die in `MetaConfig.mof` definierte Metakonfiguration von DSC auf den LCM angewendet, sobald der Computer zum ersten Mal gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="4c227-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="4c227-145">Wenn in der Metakonfiguration festgelegt ist, dass Konfigurationen durch den lokalen Konfigurations-Manager von einem Pullserver abgerufen werden sollen, versucht der Computer beim ersten Hochfahren, die Konfiguration von diesem Pullserver abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4c227-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="4c227-146">Weitere Informationen zum Einrichten von DSC-Pullservern finden Sie unter [Einrichten eines DSC-Webpullservers](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="4c227-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="4c227-147">In diesem Beispiel wird sowohl die im vorherigen Abschnitt beschriebene Konfiguration (**SampleIISInstall**) als auch die folgenden Metakonfiguration verwendet:</span><span class="sxs-lookup"><span data-stu-id="4c227-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="4c227-148">So fügen Sie ein MOF-Metakonfigurationsdokument zur VHD hinzu</span><span class="sxs-lookup"><span data-stu-id="4c227-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="4c227-149">Stellen Sie die VHD, zu der Sie die Metakonfiguration hinzufügen möchten, mit dem Cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) bereit.</span><span class="sxs-lookup"><span data-stu-id="4c227-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="4c227-150">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4c227-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="4c227-151">[Richten Sie einen DSC-Webpullserver ein](../pull-server/pullServer.md), und speichern Sie die **SampleIISInstall**-Konfiguration im entsprechenden Ordner.</span><span class="sxs-lookup"><span data-stu-id="4c227-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="4c227-152">Auf einem Computer mit PowerShell 5.0 oder höher speichern Sie die oben stehende Metakonfiguration (**PullClientBootstrap**) als PowerShell-Skriptdatei (.ps1).</span><span class="sxs-lookup"><span data-stu-id="4c227-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="4c227-153">Navigieren Sie in einer PowerShell-Konsole zu dem Ordner, in dem Sie die PS1-Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="4c227-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="4c227-154">Führen Sie die folgenden PowerShell-Befehle zum Kompilieren des MOF-Metakonfigurationsdokuments aus (Informationen zum Kompilieren von DSC-Konfigurationen finden Sie unter [DSC-Konfigurationen](../configurations/configurations.md):</span><span class="sxs-lookup"><span data-stu-id="4c227-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="4c227-155">Dadurch wird eine `localhost.meta.mof`-Datei in einen neuen Ordner namens `PullClientBootstrap` erstellt.</span><span class="sxs-lookup"><span data-stu-id="4c227-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="4c227-156">Benennen Sie die Datei in `MetaConfig.mof`um, und verschieben Sie sie an den richtigen Speicherort auf der virtuellen Festplatte. Verwenden Sie dazu das Cmdlet [Move-Item](/powershell/module/microsoft.powershell.management/move-item).</span><span class="sxs-lookup"><span data-stu-id="4c227-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="4c227-157">Heben Sie die VHD-Bereitstellung durch Aufrufen des Cmdlets [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) auf.</span><span class="sxs-lookup"><span data-stu-id="4c227-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="4c227-158">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4c227-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="4c227-159">Erstellen Sie einen virtuellen Computer mithilfe der VHD, auf der Sie das DSC MOF-Dokument installiert haben.</span><span class="sxs-lookup"><span data-stu-id="4c227-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="4c227-160">Nach dem ersten Hochfahren und der Installation des Betriebssystems wird die Konfiguration durch DSC vom Pullserver abgerufen, und IIS wird installiert.</span><span class="sxs-lookup"><span data-stu-id="4c227-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="4c227-161">Sie können dies überprüfen, indem Sie das Cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4c227-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="4c227-162">Deaktivieren von DSC zur Startzeit</span><span class="sxs-lookup"><span data-stu-id="4c227-162">Disable DSC at boot time</span></span>

<span data-ttu-id="4c227-163">Standardmäßig wird der Wert des Schlüssels `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` auf „2“ festgelegt ist, wodurch eine DSC-Konfiguration ausgeführt werden kann, wenn der Computer einen ausstehenden oder aktuellen Zustand aufweist.</span><span class="sxs-lookup"><span data-stu-id="4c227-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="4c227-164">Wenn beim ersten Hochfahren keine Konfiguration ausgeführt werden soll, müssen Sie den Wert dieses Schlüssels auf 0 festgelegt:</span><span class="sxs-lookup"><span data-stu-id="4c227-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="4c227-165">Stellen Sie die VHD bereit, indem Sie das Cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="4c227-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="4c227-166">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4c227-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="4c227-167">Laden Sie den Registrierungsunterschlüssel `HKLM\Software` durch Aufrufen von `reg load` aus der VHD.</span><span class="sxs-lookup"><span data-stu-id="4c227-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="4c227-168">Navigieren Sie mithilfe des PowerShell-Registrierungsanbieters zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span><span class="sxs-lookup"><span data-stu-id="4c227-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="4c227-169">Ändern Sie den Wert von `DSCAutomationHostEnabled` in 0.</span><span class="sxs-lookup"><span data-stu-id="4c227-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="4c227-170">Entladen Sie die Registrierung, indem Sie die folgenden Befehle ausführen:</span><span class="sxs-lookup"><span data-stu-id="4c227-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="4c227-171">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4c227-171">See Also</span></span>

[<span data-ttu-id="4c227-172">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4c227-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="4c227-173">DSCAutomationHostEnabled (Registrierungsschlüssel)</span><span class="sxs-lookup"><span data-stu-id="4c227-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="4c227-174">Konfigurieren des lokalen Konfigurations-Managers (LCM)</span><span class="sxs-lookup"><span data-stu-id="4c227-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="4c227-175">Einrichten eines DSC-Webpullservers</span><span class="sxs-lookup"><span data-stu-id="4c227-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
