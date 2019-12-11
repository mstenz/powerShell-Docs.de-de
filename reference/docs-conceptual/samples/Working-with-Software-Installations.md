---
ms.date: 06/03/2019
keywords: powershell,cmdlet
title: Arbeiten mit Softwareinstallationen
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "66830289"
---
# <a name="working-with-software-installations"></a>Arbeiten mit Softwareinstallationen

Auf Anwendungen, die für die Verwendung von Windows Installer entwickelt wurden, kann über die WMI-Klasse **Win32_Product** zugegriffen werden, aber nicht alle heute verfügbaren Anwendungen verwenden den Windows Installer.
Anwendungen, die alternative Setuproutinen verwenden, werden normalerweise nicht von Windows Installer verwaltet.
Spezifische Verfahren für die Arbeit mit diesen Anwendungen hängen von der Installationssoftware und von den Entscheidungen des Anwendungsentwicklers ab. Beispielsweise können Anwendungen, die durch Kopieren der Dateien in einen Ordner auf den Computer installiert werden, in der Regel nicht mit den hier beschriebenen Verfahren verwaltet werden. Sie können diese Anwendungen als Dateien und Ordner mit den Verfahren verwalten, die unter [Arbeiten mit Dateien und Ordnern](Working-with-Files-and-Folders.md) erläutert werden.

> [!CAUTION]
> Die Klasse **Win32_Product** ist nicht für Abfragen optimiert. Abfragen mit Platzhalterfiltern führen dazu, dass WMI alle installierten Produkte über den MSI-Anbieter auflistet und anschließend die vollständige Liste sequenziell analysiert, um den Filter zu verarbeiten. Außerdem wird eine Konsistenzprüfung der installierten Pakete gestartet, um die Installation zu überprüfen und zu reparieren. Die Validierung ist ein langwieriger Prozess und kann zu Fehlern in den Ereignisprotokollen führen. Weitere Informationen finden Sie im [KB-Artikel 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Auflisten von Windows Installer-Anwendungen

Verwenden Sie die folgende einfache WMI-Abfrage zum Auflisten von Anwendungen, die mithilfe von Windows Installer auf einem lokalen System oder Remotesystem installiert wurden:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Um alle Eigenschaften des Objekts **Win32_Product** auf dem Bildschirm anzuzeigen, verwenden Sie den Parameter **Property** der Formatierungs-Cmdlets (z.B. Cmdlet `Format-List`) mit dem Wert `*` (alle).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Verwenden Sie alternativ den **Filter**-Parameter `Get-CimInstance`, um nur Microsoft .NET Framework 2.0 auszuwählen. Der Wert des **Filter**-Parameters verwendet die Syntax der WMI-Abfragesprache (WMI Query Language, WQL) und nicht die Windows PowerShell-Syntax. Beispiel:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

Um nur die relevanten Eigenschaften aufzulisten, verwenden Sie den Parameter **Property** der Formatierungs-Cmdlets zum Auflisten der gewünschten Eigenschaften.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Auflisten aller deinstallierbaren Anwendungen

Da die meisten Standardanwendungen ein Deinstallationsprogramm bei Windows registrieren, können Sie mit diesen lokal arbeiten, indem Sie sie in der Windows-Registrierung suchen. Es gibt keine garantierte Möglichkeit, jede Anwendung auf einem System zu finden. Allerdings ist es möglich, alle Programme mit Auflistungen zu finden, die unter **Software** angezeigt werden. **Software** sucht diese Anwendungen im folgenden Registrierungsschlüssel:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Dieser Schlüssel kann untersucht werden, um Anwendungen zu finden. Um die Anzeige des Deinstallationsschlüssels zu vereinfachen, kann diesem Registrierungsspeicherort ein PowerShell-Laufwerk zugeordnet werden:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
Wir haben nun ein Laufwerk mit dem Namen „Uninstall:“, das für die schnelle und bequeme Suche nach Anwendungsinstallationen verwendet werden kann. Wir können die Anzahl der installierten Anwendungen durch Zählen der Anzahl der Registrierungsschlüssel im PowerShell-Laufwerk „Uninstall:“ finden:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

Diese Liste mit Anwendungen kann nun anhand einer Vielzahl von Verfahren weiter durchsucht werden, beginnend mit **Get-ChildItem**. Um eine Liste der Anwendungen abzurufen und in der Variablen **$UninstallableApplications** zu speichern, verwenden Sie folgenden Befehl:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Um die Werte der Registrierungseinträge in den Registrierungsschlüsseln unter „Deinstallieren“ anzuzeigen, verwenden Sie die Methode „GetValue“ der Registrierungsschlüssel. Der Wert der Methode ist der Name des Registrierungseintrags.

Um die Anzeigenamen der Anwendungen beispielsweise im Deinstallationsschlüssel zu suchen, verwenden Sie den folgenden Befehl:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Es gibt keine Garantie dafür, dass diese Werte eindeutig sind. Im folgenden Beispiel werden zwei installierte Elemente als „Windows Media Encoder 9-Reihe“ angezeigt:

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Installieren von Anwendungen

Sie können die Klasse **Win32_Product** verwenden, um Windows Installer-Pakete remote oder lokal zu installieren.

> [!NOTE]
> Um eine Anwendung zu installieren, müssen Sie PowerShell mit der Option „Als Administrator ausführen“ starten.

Verwenden Sie bei der Remoteinstallation einen UNC-Netzwerkpfad (Universal Naming Convention), um den Pfad zum MSI-Paket anzugeben, weil das WMI-Subsystem PowerShell-Pfade nicht interpretieren kann. Geben Sie beispielsweise zum Installieren des Pakets „NewPackage.msi“ in der Netzwerkfreigabe `\\AppServ\dsp` auf dem Remotecomputer PC01 den folgenden Befehl in der PowerShell-Eingabeaufforderung ein:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Anwendungen, die keine Windows Installer-Technologie verwenden, verfügen möglicherweise über anwendungsspezifische Methoden für die automatisierte Bereitstellung. Lesen Sie die Dokumentation zur Anwendung, oder wenden Sie sich an den Support des Anwendungsherstellers.

## <a name="removing-applications"></a>Entfernen von Anwendungen

Das Entfernen eines Windows Installer-Pakets über PowerShell funktioniert ungefähr so wie die Installation eines Pakets. Im Folgenden ist ein Beispiel aufgeführt, in dem das zu deinstallierende Paket basierend auf seinem Namen ausgewählt wird. In einigen Fällen ist es möglicherweise einfacher, mit **IdentifyingNumber** zu filtern:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Das Entfernen von anderen Anwendungen ist nicht ganz so einfach, auch wenn es lokal durchgeführt wird. Nach den Befehlszeilen-Deinstallationszeichenfolgen für diese Anwendungen wird durch Extrahieren der Eigenschaft **UninstallString** gesucht.
Diese Methode funktioniert für Windows Installer-Anwendungen und ältere Programme, die unter dem Deinstallationsschlüssel angezeigt werden:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Sie können die Ausgabe bei Bedarf nach dem Anzeigenamen filtern:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Möglicherweise sind diese Zeichenfolgen jedoch nur mit einigen Änderungen direkt über die PowerShell-Eingabeaufforderung verwendbar.

## <a name="upgrading-windows-installer-applications"></a>Aktualisieren von Windows Installer-Anwendungen

Um eine Anwendung zu aktualisieren, müssen Sie den Namen der Anwendung und den Pfad zum Aktualisierungspaket der Anwendung kennen. Mit diesen Informationen können Sie eine Anwendung mit einem einzigen PowerShell-Befehl aktualisieren:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
