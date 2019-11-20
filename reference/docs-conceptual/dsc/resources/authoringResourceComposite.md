---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 'Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource'
ms.openlocfilehash: 7fa6ee56d4706b96fb47123c7aa00c4df6256492
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933824"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Zusammengesetzte Ressourcen Verwenden einer DSC-Konfiguration als Ressource

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

In realen Situationen können Konfigurationen lang und komplex sein, viele verschiedene Ressourcen aufrufen und eine große Anzahl von Eigenschaften festlegen. Um mit dieser Komplexität zurecht zu kommen, können Sie eine Windows PowerShell DSC-Konfiguration als Ressource für andere Konfigurationen verwenden. Dies wird als zusammengesetzte Ressource bezeichnet. Eine zusammengesetzte Ressource ist eine DSC-Konfiguration, die Parameter verwendet. Die Parameter der Konfiguration fungieren als Eigenschaften der Ressource. Die Konfiguration wird als Datei mit der Erweiterung **.schema.psm1** gespeichert und tritt in einer normalen DSC-Ressource an die Stelle von MOF-Schema und Ressourcenskript (weitere Informationen zu DSC-Ressourcen finden Sie unter [Windows PowerShell DSC-Ressourcen](resources.md).

## <a name="creating-the-composite-resource"></a>Erstellen der zusammengesetzten Ressource

Im folgenden Beispiel wird eine Konfiguration erstellt, die eine Reihe von vorhandenen Ressourcen zum Konfigurieren virtueller Computer aufruft. Anstatt die festzulegenden Werte in Konfigurationsblöcken anzugeben, verwendet die Konfiguration eine Reihe von Parametern, die dann in den Konfigurationsblöcken verwendet werden.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a>Speichern die Konfiguration als eine zusammengesetzte Ressource

Damit die parametrisierte Konfiguration als DSC-Ressource verwendet werden kann, speichern Sie sie in einer Verzeichnisstruktur, die den Verzeichnisstrukturen MOF-basierter Ressourcen entspricht, und geben Sie ihr einen Namen mit der Erweiterung **.schema.psm1**. In diesem Beispiel erhält die Datei den Namen **xVirtualMachine.schema.psm1**. Sie müssen auch ein Manifest mit dem Namen **xVirtualMachine.psd1** erstellen, das die folgende Zeile enthält. Beachten Sie, dass dies zusätzlich zur Datei **MyDscResources.psd1** erforderlich ist, dem Modulmanifest für alle Ressourcen im Ordner **MyDscResources**.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Wenn Sie fertig sind, sollte die Ordnerstruktur wie folgt aussehen:

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Die Ressource kann nun mit dem Cmdlet „Get-DscResource“ gefunden werden, und ihre Eigenschaften können entweder mit diesem Cmdlet oder über die Tastenkombination **STRG+LEERTASTE** (AutoVervollständigen) in Windows PowerShell ISE sichtbar gemacht werden.

## <a name="using-the-composite-resource"></a>Verwenden der zusammengesetzten Ressource

Als Nächstes wird eine Konfiguration erstellt, die die zusammengesetzte Ressource aufruft. Diese Konfiguration ruft die zusammengesetzte Ressource „xVirtualMachine“ auf, um einen virtuellen Computer zu erstellen, und ruft anschließend die Ressource **xComputer** auf, um sie umzubenennen.

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

Sie können diese Ressource auch zum Erstellen mehrerer VMs verwenden, indem Sie ein Array von VM-Namen an die Ressource „xVirtualMachine“ übergeben.

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>Unterstützung von PsDscRunAsCredential

> [!NOTE]
> **PsDscRunAsCredential** wird in PowerShell 5.0 und höher unterstützt.

Mithilfe der Eigenschaft **PsDscRunAsCredential** kann im Ressourcenblock [DSC configurations](../configurations/configurations.md) angegeben werden, dass die Ressource mit einem festgelegten Satz an Anmeldeinformationen ausgeführt werden soll.
Weitere Informationen finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](../configurations/runAsUser.md).

Um aus einer benutzerdefinierten Ressource auf den Benutzerkontext zuzugreifen, können Sie die automatische Variable `$PsDscContext` verwenden.

Beispielsweise wird mit dem folgenden Code der Benutzerkontext für die Ressourcenausführung in den ausführlichen Ausgabestream geschrieben:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Weitere Informationen
### <a name="concepts"></a>Konzepte
* [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md)
* [Erste Schritte mit Windows PowerShell Desired State Configuration (DSC)](../overview/overview.md)
