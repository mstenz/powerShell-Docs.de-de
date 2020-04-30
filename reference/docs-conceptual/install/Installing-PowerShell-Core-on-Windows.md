---
title: Installieren von PowerShell unter Windows
description: Informationen zur Installation von PowerShell unter Windows
ms.date: 08/06/2018
ms.openlocfilehash: a8543a91ad503364c5346a11c9c9d9f910547278
ms.sourcegitcommit: b80ce0396550d0896189d0205d6c4b4372ac2015
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141381"
---
# <a name="installing-powershell-on-windows"></a>Installieren von PowerShell unter Windows

Es gibt mehrere Möglichkeiten zum Installieren von PowerShell unter Windows.

## <a name="prerequisites"></a>Voraussetzungen

Die neueste Version von PowerShell wird unter Windows 7 SP1, Windows Server 2008 R2 und höheren Versionen unterstützt.

Zum Aktivieren des PowerShell-Remoting über WSMan müssen die folgenden Voraussetzungen erfüllt sein:

- [Universal C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) muss unter Windows-Versionen vor Windows 10 installiert sein. Die Runtime ist über einen direkten Download oder Windows-Update verfügbar. Auf vollständig gepatchten Systemen ist dieses Paket bereits installiert.
- Installieren Sie Windows Management Framework (WMF) 4.0 oder höher auf Windows 7 und Windows Server 2008 R2. Weitere Informationen zu WMF erhalten Sie in der [WMF-Übersicht](/powershell/scripting/wmf/overview).

## <a name="download-the-installer-package"></a>Herunterladen des Installationspakets

Um PowerShell unter Windows zu installieren, laden Sie das Installationspaket von unserer GitHub-Seite [Releases][releases] herunter. Scrollen Sie auf der Seite „Release“ nach unten zum Abschnitt **Assets**. Der Abschnitt **Assets** ist möglicherweise zugeklappt, sodass Sie darauf klicken müssen, um ihn aufzuklappen.

## <a name="installing-the-msi-package"></a><a id="msi" />Installieren des MSI-Pakets

Die MSI-Datei sieht so aus: `PowerShell-<version>-win-<os-arch>.msi`. Beispiel:

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

Sobald sie heruntergeladen wurde, führen Sie den Installer mit einem Doppelklick aus und befolgen die Anweisungen.

Das Installationsprogramm erstellt eine Verknüpfung im Windows-Startmenü.

- Das Paket wird standardmäßig unter `$env:ProgramFiles\PowerShell\<version>` installiert
- Sie können PowerShell über das Startmenü oder über `$env:ProgramFiles\PowerShell\<version>\pwsh.exe` starten

> [!NOTE]
> PowerShell 7 wird in ein neues Verzeichnis installiert und parallel mit Windows PowerShell 5.1 ausgeführt. Für PowerShell Core 6.x ist PowerShell 7 ein direktes Upgrade, durch das PowerShell Core 6.x entfernt wird.
>
> - PowerShell 7 wird in `$env:ProgramFiles\PowerShell\7` installiert.
> - Der Ordner `$env:ProgramFiles\PowerShell\7` wird `$env:PATH` hinzugefügt.
> - Der Ordner `$env:ProgramFiles\PowerShell\6` wird gelöscht.
>
> Wenn Sie PowerShell 6 und PowerShell 7 parallel ausführen müssen, installieren Sie PowerShell 6 mithilfe der [ZIP-Installationsmethode](#zip) neu.

### <a name="administrative-install-from-the-command-line"></a>Administrative Installation über die Befehlszeile

MSI-Pakete können über die Befehlszeile installiert werden, sodass Administratoren Pakete ohne Benutzerinteraktion bereitstellen können. Das MSI-Paket enthält die folgenden Eigenschaften zum Steuern der Installationsoptionen:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** – Diese Eigenschaft steuert die Option zum Hinzufügen des Elements **PowerShell öffnen** zum Kontextmenü im Windows-Explorer.
- **ENABLE_PSREMOTING** – Diese Eigenschaft steuert die Option zum Aktivieren von PowerShell-Remoting während der Installation.
- **REGISTER_MANIFEST** – Diese Eigenschaft steuert die Option zum Registrieren des Manifests für Windows-Ereignisprotokollierung.

Das folgenden Beispiel zeigt, wie PowerShell mit allen aktivierten Installationsoptionen im Hintergrund installiert wird.

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Eine vollständige Liste der Befehlszeilenoptionen für `Msiexec.exe` finden Sie unter [Befehlszeilenoptionen](/windows/desktop/Msi/command-line-options).

## <a name="installing-the-msix-package"></a><a id="msix" />Installieren des MSIX-Pakets

Um das MSIX-Paket manuell auf einem Windows 10-Client zu installieren, laden Sie das MSIX-Paket von der GitHub-Seite mit [Releases][releases] herunter. Scrollen Sie nach unten zum Abschnitt **Assets** des Release, das Sie installieren möchten. Der Abschnitt „Assets“ ist möglicherweise reduziert, sodass Sie klicken müssen, um ihn zu erweitern.

Die MSIX-Datei sieht so aus: `PowerShell-<version>-win-<os-arch>.msix`

Zum Installieren des Pakets müssen Sie das Cmdlet `Add-AppxPackage` verwenden:

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> Das MSIX-Paket wurde noch nicht veröffentlicht. Nach seiner Veröffentlichung ist es im Microsoft Store und auf der GitHub-Seite [Releases][releases] verfügbar.

## <a name="installing-the-zip-package"></a><a id="zip" />Installieren des ZIP-Pakets

Binäre PowerShell ZIP-Archive werden zur Verfügung gestellt, um erweiterte Bereitstellungsszenarios zu ermöglichen. Bei der Installation des ZIP-Archivs werden die Voraussetzungen nicht wie bei den MSI-Paketen überprüft. Laden Sie das ZIP-Archiv von der Seite [Releases][releases] herunter. Je nachdem, wie Sie die Datei herunterladen, müssen Sie die Blockierung der Datei mit dem Cmdlet `Unblock-File` aufheben. Entpacken Sie den Inhalt an den Speicherort Ihrer Wahl, und führen Sie `pwsh.exe` von dort aus. Damit Remoting über WSMan einwandfrei funktioniert, müssen die [Voraussetzungen](#prerequisites) unbedingt erfüllt sein.

## <a name="deploying-on-windows-10-iot-enterprise"></a>Bereitstellung unter Windows 10 IoT Enterprise

Bei Windows 10 IoT Enterprise ist Windows PowerShell bereits im Funktionsumfang enthalten, sodass PowerShell 7 bereitgestellt werden kann.

1. Erstellen Sie `PSSession` auf dem Zielgerät.

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
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

4. Richten Sie Remoting für PowerShell 7 ein.

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Stellen Sie eine Verbindung mit dem PowerShell 7-Endpunkt auf dem Gerät her.

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```
## <a name="deploying-on-windows-10-iot-core"></a>Bereitstellung unter Windows 10 IoT Core

Bei Windows 10 IoT Core wird Windows PowerShell hinzugefügt, wenn Sie das Feature *IOT_POWERSHELL* aufnehmen. Über dieses Feature kann PowerShell 7 bereitgestellt werden.
Die oben beschriebenen Schritte für Windows 10 IoT Enterprise können auch für IoT Core ausgeführt werden.

Verwenden Sie zum Hinzufügen der aktuellen PowerShell-Version im Image den Befehl [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease). Mit diesem Befehl wird das Paket im Arbeitsbereich eingefügt und das Feature *OPENSRC_POWERSHELL* zu Ihrem Image hinzugefügt.

> [!NOTE]
> Bei der ARM64-Architektur wird Windows PowerShell nicht hinzugefügt, wenn Sie *IOT_POWERSHELL* einfügen. Daher funktioniert die ZIP-basierte Installation nicht.
> Sie müssen den Befehl „Import-PSCoreRelease“ verwenden, um PowerShell im Image hinzuzufügen.

## <a name="deploying-on-nano-server"></a>Bereitstellen auf Nano Server

Diese Anweisungen gehen davon aus, dass der Nano Server ein „monitorloses“ Betriebssystem ist, unter dem bereits eine Version von PowerShell ausgeführt wird. Weitere Informationen finden Sie in der [Dokumentation zu Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).

PowerShell-Binärdateien können auf zwei verschiedene Arten bereitgestellt werden.

1. Offline: Binden Sie die Nano Server-VHD ein, und entpacken Sie den Inhalt der ZIP-Datei an dem von Ihnen gewünschten Speicherort in dem eingebundenen Image.
2. Online: Übertragen Sie die ZIP-Datei über eine PowerShell-Sitzung, und entpacken Sie sie an dem von Ihnen gewünschten Speicherort.

In beiden Fällen benötigen Sie das ZIP-Releasepaket für Windows 10 x64. Führen Sie die Befehle in einer „Administrator“-Instanz von PowerShell aus.

### <a name="offline-deployment-of-powershell"></a>Offlinebereitstellung von PowerShell

1. Verwenden Sie Ihr bevorzugtes ZIP-Hilfsprogramm, um das Paket in ein Verzeichnis im eingebundenen Nano Server-Image zu entpacken.
2. Heben Sie die Bereitstellung des Images auf, und starten Sie es.
3. Stellen Sie eine Verbindung zur Posteingangsinstanz von Windows PowerShell her.
4. Befolgen Sie die Anweisungen, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.

### <a name="online-deployment-of-powershell"></a>Onlinebereitstellung von PowerShell

Stellen Sie PowerShell mithilfe der folgenden Schritte für Nano Server bereit.

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
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- Befolgen Sie die Anweisungen, wenn Sie auf WSMan basierendes Remoting verwenden möchten, um einen Remoting-Endpunkt mithilfe der [„Andere Instanz-Methode“](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register) zu erstellen.

## <a name="install-as-a-net-global-tool"></a>Installieren als globales .NET-Tool

Wenn Sie das [.NET Core SDK](/dotnet/core/sdk) bereits installiert haben, können Sie PowerShell einfach als [globales .NET-Tool](/dotnet/core/tools/global-tools) installieren.

```
dotnet tool install --global PowerShell
```

Der .NET-Toolinstaller fügt `$env:USERPROFILE\dotnet\tools` Ihrer `$env:PATH`-Umgebungsvariablen hinzu. Die aktuell ausgeführte Shell verfügt jedoch nicht über die aktualisierte Umgebungsvariable `$env:PATH`. Sie können PowerShell über eine neue Shell starten, indem Sie `pwsh` eingeben.

## <a name="how-to-create-a-remoting-endpoint"></a>Vorgehensweise zum Erstellen eines Remoting-Endpunkts

PowerShell unterstützt das PowerShell-Remotingprotokoll (PSRP) über WSMan und SSH. Weitere Informationen finden Sie unter

- [SSH-Remoting in PowerShell Core][ssh-remoting]
- [WSMan-Remoting in PowerShell Core][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
