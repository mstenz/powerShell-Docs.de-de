---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC
ms.openlocfilehash: 2f228a38379d1e65b31c03594e876f7226474fc3
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893351"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC

> [!IMPORTANT]
> Gilt für: Windows PowerShell 5.0

## <a name="requirements"></a>Anforderungen

> [!NOTE] 
> Der in diesem Thema beschriebene Registrierungsschlüssel **DSCAutomationHostEnabled** ist in PowerShell 4.0 nicht verfügbar.
> Informationen dazu, wie Sie neue virtuelle Computer beim ersten Hochfahren in PowerShell 4.0 konfigurieren, finden Sie unter [Sie möchten Ihre Computer mithilfe von DSC beim ersten Hochfahren automatisch konfigurieren?]> (https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Um diese Beispiele auszuführen, benötigen Sie:

- Eine startbare virtuelle Festplatte (VHD). Sie können ein ISO-Image mit einer Evaluierungsversion von Windows Server 2016 aus dem [TechNet-Evaluierungscenter](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) herunterladen. Anweisungen finden Sie zum Erstellen einer VHD aus einem ISO-Image finden Sie unter [Erstellen startbarer virtueller Festplatten](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Ein Hostcomputer, auf dem Hyper-V aktiviert ist. Informationen hierzu finden Sie unter [Übersicht über Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Mithilfe von DSC können Sie die Installation und Konfiguration von Software beim ersten Hochfahren eines Computers automatisieren.
  Sie können dazu entweder ein MOF-Konfigurationsdokument oder eine Metakonfiguration zu startbaren Medien (z. B. einer VHD) hinzufügen, die beim ersten Startvorgang ausgeführt werden.
  Dieses Verhalten wird vom [DSCAutomationHostEnabled-Registrierungsschlüssel](DSCAutomationHostEnabled.md) unter `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies` angegeben.
  Standardmäßig ist der Wert dieses Schlüssels 2, wodurch DSC zur Startzeit ausgeführt werden kann.

  Wenn DSC nicht zur Startzeit ausgeführt werden soll, legen Sie den Wert des Registrierungsschlüssels [DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) auf 0 fest.

- Hinzufügen eines MOF-Konfigurationsdokuments zu einer VHD
- Hinzufügen einer Metakonfiguration zu einer VHD
- Deaktivieren von DSC zur Startzeit

> [!NOTE]
> Sie können zu einem Computer gleichzeitig `Pending.mof` und `MetaConfig.mof` hinzufügen.
> Wenn beide Dateien vorhanden sind, haben die Einstellungen von `MetaConfig.mof` Vorrang.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Hinzufügen eines MOF-Konfigurationsdokuments zu einer VHD

Um eine Konfiguration beim ersten Hochfahren anzuwenden, können Sie ein kompiliertes MOF-Konfigurationsdokument als `Pending.mof`-Datei zur VHD hinzufügen.
Ist der Registrierungsschlüssel **DSCAutomationHostEnabled** auf 2 (Standardwert) festgelegt, wird die in `Pending.mof` definierte Konfiguration von DSC angewendet, sobald der Computer zum ersten Mal gestartet wird.

In diesem Beispiel wird die folgende Konfiguration verwendet, durch die IIS auf dem neuen Computer installiert wird:

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>So fügen Sie ein MOF-Konfigurationsdokument zur VHD hinzu

1. Stellen Sie die VHD, zu der Sie die Konfiguration hinzufügen möchten, mit dem Cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) bereit. Beispiel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Auf einem Computer mit PowerShell 5.0 oder höher speichern Sie die oben stehende Konfiguration (**SampleIISInstall**) als PowerShell-Skriptdatei (.ps1).

3. Navigieren Sie in einer PowerShell-Konsole zu dem Ordner, in dem Sie die PS1-Datei gespeichert haben.

4. Führen Sie die folgenden PowerShell-Befehle zum Kompilieren des MOF-Dokuments aus (Informationen zum Kompilieren von DSC-Konfigurationen finden Sie unter [DSC-Konfigurationen](configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Dadurch wird eine `localhost.mof`-Datei in einen neuen Ordner namens `SampleIISInstall` erstellt.
   Benennen Sie die Datei in `Pending.mof`um, und verschieben Sie sie an den richtigen Speicherort auf der virtuellen Festplatte. Verwenden Sie dazu das Cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx). Beispiel:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Heben Sie die VHD-Bereitstellung durch Aufrufen des Cmdlets [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) auf. Beispiel:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Erstellen Sie einen virtuellen Computer mithilfe der VHD, auf der Sie das DSC MOF-Dokument installiert haben.

Nach dem ersten Hochfahren und der Installation des Betriebssystems wird IIS installiert.
Sie können dies überprüfen, indem Sie das Cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) aufrufen.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Hinzufügen einer Metakonfiguration zu einer VHD

Sie können einen Computer auch so konfigurieren, dass eine Konfiguration beim ersten Hochfahren abgerufen wird, indem Sie eine Metakonfiguration als `MetaConfig.mof`-Datei zur VHD hinzufügen (Informationen hierzu finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers (LCM)](metaConfig.md)).
Ist der Registrierungsschlüssel **DSCAutomationHostEnabled** auf 2 (Standardwert) festgelegt, wird die in `MetaConfig.mof` definierte Metakonfiguration von DSC auf den LCM angewendet, sobald der Computer zum ersten Mal gestartet wird.
Wenn in der Metakonfiguration festgelegt ist, dass Konfigurationen durch den LCM von einem Pullserver abgerufen werden sollen, versucht der Computer beim ersten Hochfahren, die Konfiguration von diesem Pullserver abzurufen.
Weitere Informationen zum Einrichten von DSC-Pullservern finden Sie unter [Einrichten eines DSC-Webpullservers](pullServer.md).

In diesem Beispiel wird sowohl die im vorherigen Abschnitt beschriebene Konfiguration (**SampleIISInstall**) als auch die folgenden Metakonfiguration verwendet:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>So fügen Sie ein MOF-Metakonfigurationsdokument zur VHD hinzu

1. Stellen Sie die VHD, zu der Sie die Metakonfiguration hinzufügen möchten, mit dem Cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) bereit. Beispiel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Richten Sie einen DSC-Webpullserver ein](pullServer.md), und speichern Sie die **SampleIISInistall**-Konfiguration im entsprechenden Ordner.

3. Auf einem Computer mit PowerShell 5.0 oder höher speichern Sie die oben stehende Metakonfiguration (**PullClientBootstrap**) als PowerShell-Skriptdatei (.ps1).

4. Navigieren Sie in einer PowerShell-Konsole zu dem Ordner, in dem Sie die PS1-Datei gespeichert haben.

5. Führen Sie die folgenden PowerShell-Befehle zum Kompilieren des MOF-Metakonfigurationsdokuments aus (Informationen zum Kompilieren von DSC-Konfigurationen finden Sie unter [DSC-Konfigurationen](configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Dadurch wird eine `localhost.meta.mof`-Datei in einen neuen Ordner namens `PullClientBootstrap` erstellt.
   Benennen Sie die Datei in `MetaConfig.mof`um, und verschieben Sie sie an den richtigen Speicherort auf der virtuellen Festplatte. Verwenden Sie dazu das Cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx).

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Heben Sie die VHD-Bereitstellung durch Aufrufen des Cmdlets [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) auf. Beispiel:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Erstellen Sie einen virtuellen Computer mithilfe der VHD, auf der Sie das DSC MOF-Dokument installiert haben.

Nach dem ersten Hochfahren und der Installation des Betriebssystems wird die Konfiguration durch DSC vom Pullserver abgerufen, und IIS wird installiert.
Sie können dies überprüfen, indem Sie das Cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) aufrufen.

## <a name="disable-dsc-at-boot-time"></a>Deaktivieren von DSC zur Startzeit

Standardmäßig wird der Wert des Schlüssels `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` auf „2“ festgelegt ist, wodurch eine DSC-Konfiguration ausgeführt werden kann, wenn der Computer einen ausstehenden oder aktuellen Zustand aufweist. Wenn beim ersten Hochfahren keine Konfiguration ausgeführt werden soll, müssen Sie den Wert dieses Schlüssels auf 0 festgelegt:

1. Stellen Sie die VHD bereit, indem Sie das Cmdlet [Mount-VHD](/powershell/module/hyper-v/mount-vhd) aufrufen. Beispiel:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Laden Sie den Registrierungsunterschlüssel `HKLM\Software` durch Aufrufen von `reg load` aus der VHD.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Navigieren Sie mithilfe des PowerShell-Registrierungsanbieters zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*`.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Ändern Sie den Wert von `DSCAutomationHostEnabled` in 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Entladen Sie die Registrierung, indem Sie die folgenden Befehle ausführen:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Weitere Informationen

[DSC-Konfigurationen](configurations.md)

[DSCAutomationHostEnabled (Registrierungsschlüssel)](DSCAutomationHostEnabled.md)

[Konfigurieren des lokalen Konfigurations-Managers (LCM)](metaConfig.md)

[Einrichten eines DSC-Webpullservers](pullServer.md)
