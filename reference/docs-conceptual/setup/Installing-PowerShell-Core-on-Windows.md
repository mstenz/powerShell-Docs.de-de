---
title: Installieren von PowerShell Core unter Windows
description: Informationen zur Installation von PowerShell Core unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: 595f12efd060406264a1a4efb9d54035da06ffe3
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557177"
---
# <a name="installing-powershell-core-on-windows"></a>Installieren von PowerShell Core unter Windows

## <a name="msi"></a>MSI

Installieren Sie PowerShell auf einem Windows-Client oder Windows Server (funktioniert auf Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub [Releases][]-Seite herunterladen.

Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.

Bei der Installation wird im Startmenü eine Verknüpfung erstellt.

- Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert
- Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten

### <a name="prerequisites"></a>Voraussetzungen

Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:

- [Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden.
  Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar.
  Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.
- Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen.
Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird.
Damit das Remoting über WSMan auf Windows-Versionen vor Windows 10 richtig funktioniert, müssen Sie sicherstellen, dass die [Voraussetzungen](#prerequisites) erfüllt sind.

## <a name="deploying-on-windows-iot"></a>Bereitstellen auf Windows IoT

Windows IoT ist bereits in Windows PowerShell enthalten, das Sie zum Bereitstellen von PowerShell Core 6 verwenden werden.

1. Erstellen Sie `PSSession` auf dem Zielgerät.

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Kopieren Sie das ZIP-Paket auf das Gerät.

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. Richten Sie Remoting für PowerShell Core 6 ein.

   ```powershell
   cd .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Stellen Sie eine Verbindung mit dem PowerShell Core 6-Endpunkt auf dem Gerät her.

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>Bereitstellen auf Nano Server

Diese Anweisungen gehen von einer Version von PowerShell aus, die bereits auf dem Nano Server-Image ausgeführt wird und von dem [Nano Server-Image-Builder](/windows-server/get-started/deploy-nano-server) erstellt wurde.
Nano Server ist ein „monitorloses“ Betriebssystem. Core-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.

1. Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.
2. Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.

In beiden Fällen benötigen Sie das Windows 10 x64 ZIP-Releasepaket, und Sie müssen die Befehle in einer „Administrator“-PowerShell-Instanz ausführen.

### <a name="offline-deployment-of-powershell-core"></a>Offline-Bereitstellung von PowerShell Core

1. Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.
2. Heben Sie die Bereitstellung des Images auf, und starten Sie es.
3. Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.
4. Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.

### <a name="online-deployment-of-powershell-core"></a>Onlinebereitstellung von PowerShell Core

Die folgenden Schritte führen Sie durch die Bereitstellung von PowerShell Core für eine ausgeführte Instanz von Nano Server und die Konfiguration des dazugehörigen Remoteendpunkts.

- Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Kopieren Sie die Datei in die Nano Server-Instanz.

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Geben Sie die Sitzung ein.

  ```powershell
  Enter-PSSession $session
  ```

- Extrahieren Sie die ZIP-Datei.

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.

## <a name="instructions-to-create-a-remoting-endpoint"></a>Anweisungen zum Erstellen eines Remoting-Endpunkts

PowerShell Core unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH.
Weitere Informationen finden Sie unter:

- [SSH-Remoting in PowerShell Core][ssh-remoting]
- [WSMan-Remoting in PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Installationsanweisungen für Artefakte

Ein Archiv mit CoreCLR-Bestandteilen wird auf jedem CI-Build über [AppVeyor][] veröffentlicht.

So Installieren Sie PowerShell Core über das CoreCLR-Artefakt:

1. Laden Sie das ZIP-Paket über die Registerkarte **Artefakte** eines bestimmten Builds herunter.
2. Entsperren der ZIP-Datei: Rechtsklick auf Explorer > Eigenschaften. Setzen Sie dann ein Häkchen bei „Zulassen“ und klicken Sie auf „Anwenden“.
3. Extrahieren Sie die ZIP-Datei in das Verzeichnis `bin`.
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[Releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
