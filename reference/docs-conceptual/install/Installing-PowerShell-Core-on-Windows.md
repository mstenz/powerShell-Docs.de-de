---
title: Installieren von PowerShell Core unter Windows
description: Informationen zur Installation von PowerShell Core unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: 00a1d8064a3c1ec6608a46415bbabb8d98d880f0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416795"
---
# <a name="installing-powershell-core-on-windows"></a>Installieren von PowerShell Core unter Windows

Es gibt mehrere Möglichkeiten zum Installieren von PowerShell Core unter Windows.

> [!TIP]
> Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a>Voraussetzungen

Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:

- [Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss auf Windows-Versionen vor Windows 10 installiert werden. Sie ist über einen direkten Download oder durch ein Windows-Update verfügbar. Auf vollständig gepatchten (inklusive optionaler Pakete), unterstützten Systeme ist sie bereits installiert.
- Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2. Weitere Informationen zu WMF erhalten Sie in der [WMF-Übersicht](/powershell/scripting/wmf/overview).

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Installieren des MSI-Pakets

Installieren Sie PowerShell auf einem Windows-Client oder Windows Server (funktioniert auf Windows 7 SP1, Windows Server 2008 R2 und höher), indem Sie das MSI-Paket von unserer GitHub [Freigaben][releases]-Seite herunterladen. Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten. Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.

Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.

Das Installationsprogramm erstellt eine Verknüpfung im Windows-Startmenü.

- Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert
- Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten

### <a name="administrative-install-from-the-command-line"></a>Administrative Installation über die Befehlszeile

MSI-Pakete können über die Befehlszeile installiert werden. Dies ermöglicht es Administratoren, Pakete ohne Benutzerinteraktion bereitzustellen. Das MSI-Paket für PowerShell enthält die folgenden Eigenschaften zum Steuern der Installationsoptionen:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – Diese Eigenschaft steuert die Option zum Hinzufügen des Elements **PowerShell öffnen** zum Kontextmenü im Windows-Explorer.
- **ENABLE_PSREMOTING** – Diese Eigenschaft steuert die Option zum Aktivieren von PowerShell-Remoting während der Installation.
- **REGISTER_MANIFEST** – Diese Eigenschaft steuert die Option zum Registrieren des Manifests für Windows-Ereignisprotokollierung.

Die folgenden Beispiele zeigen, wie PowerShell Core im Hintergrund installiert wird, wobei alle Installationsoptionen aktiviert sind.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Eine vollständige Liste der Befehlszeilenoptionen für „Msiexec.exe“ finden Sie unter [Befehlszeilenoptionen](/windows/desktop/Msi/command-line-options).

## <a name="a-idmsix-installing-the-msix-package"></a><a id="msix" />Installieren des MSIX-Pakets

Um das MSIX-Paket manuell auf einem Windows 10-Client zu installieren, laden Sie das MSIX-Paket von der GitHub-Seite mit [Releases][releases] herunter. Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten. Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.

Die MSI-Datei sieht wie folgt aus: `PowerShell-<version>-win-<os-arch>.msix`

Nach dem Download können Sie nicht einfach auf das Installationsprogramm doppelklicken, weil dieses Paket die Verwendung nicht virtualisierter Ressourcen erfordert.  Zum Installieren müssen Sie das Cmdlet `Add-AppxPackage` verwenden:

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Installieren des ZIP-Pakets

Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen. Beachten Sie, dass die Prüfung der Voraussetzungen bei der Benutzung des ZIP-Archivs nicht wie bei dem MSI-Paket durchgeführt wird. Damit Remoting über WSMan einwandfrei funktioniert, müssen Sie die [Voraussetzungen](#prerequisites) erfüllt haben.

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
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Stellen Sie eine Verbindung mit dem Gerät her, und erweitern Sie das Archiv.

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Richten Sie Remoting für PowerShell Core 6 ein.

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Stellen Sie eine Verbindung mit dem PowerShell Core 6-Endpunkt auf dem Gerät her.

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
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
4. Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.

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

- Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.

## <a name="how-to-create-a-remoting-endpoint"></a>Vorgehensweise zum Erstellen eines Remoting-Endpunkts

PowerShell Core unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH. Weitere Informationen finden Sie unter:

- [SSH-Remoting in PowerShell Core][ssh-remoting]
- [WSMan-Remoting in PowerShell Core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
