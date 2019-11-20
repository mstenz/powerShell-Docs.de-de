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
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="00f59-103">Zusammengesetzte Ressourcen Verwenden einer DSC-Konfiguration als Ressource</span><span class="sxs-lookup"><span data-stu-id="00f59-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="00f59-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="00f59-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="00f59-105">In realen Situationen können Konfigurationen lang und komplex sein, viele verschiedene Ressourcen aufrufen und eine große Anzahl von Eigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="00f59-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="00f59-106">Um mit dieser Komplexität zurecht zu kommen, können Sie eine Windows PowerShell DSC-Konfiguration als Ressource für andere Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="00f59-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="00f59-107">Dies wird als zusammengesetzte Ressource bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="00f59-107">We call this a composite resource.</span></span> <span data-ttu-id="00f59-108">Eine zusammengesetzte Ressource ist eine DSC-Konfiguration, die Parameter verwendet.</span><span class="sxs-lookup"><span data-stu-id="00f59-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="00f59-109">Die Parameter der Konfiguration fungieren als Eigenschaften der Ressource.</span><span class="sxs-lookup"><span data-stu-id="00f59-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="00f59-110">Die Konfiguration wird als Datei mit der Erweiterung **.schema.psm1** gespeichert und tritt in einer normalen DSC-Ressource an die Stelle von MOF-Schema und Ressourcenskript (weitere Informationen zu DSC-Ressourcen finden Sie unter [Windows PowerShell DSC-Ressourcen](resources.md).</span><span class="sxs-lookup"><span data-stu-id="00f59-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="00f59-111">Erstellen der zusammengesetzten Ressource</span><span class="sxs-lookup"><span data-stu-id="00f59-111">Creating the composite resource</span></span>

<span data-ttu-id="00f59-112">Im folgenden Beispiel wird eine Konfiguration erstellt, die eine Reihe von vorhandenen Ressourcen zum Konfigurieren virtueller Computer aufruft.</span><span class="sxs-lookup"><span data-stu-id="00f59-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="00f59-113">Anstatt die festzulegenden Werte in Konfigurationsblöcken anzugeben, verwendet die Konfiguration eine Reihe von Parametern, die dann in den Konfigurationsblöcken verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="00f59-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="00f59-114">Speichern die Konfiguration als eine zusammengesetzte Ressource</span><span class="sxs-lookup"><span data-stu-id="00f59-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="00f59-115">Damit die parametrisierte Konfiguration als DSC-Ressource verwendet werden kann, speichern Sie sie in einer Verzeichnisstruktur, die den Verzeichnisstrukturen MOF-basierter Ressourcen entspricht, und geben Sie ihr einen Namen mit der Erweiterung **.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="00f59-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="00f59-116">In diesem Beispiel erhält die Datei den Namen **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="00f59-116">For this example, we'll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="00f59-117">Sie müssen auch ein Manifest mit dem Namen **xVirtualMachine.psd1** erstellen, das die folgende Zeile enthält.</span><span class="sxs-lookup"><span data-stu-id="00f59-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="00f59-118">Beachten Sie, dass dies zusätzlich zur Datei **MyDscResources.psd1** erforderlich ist, dem Modulmanifest für alle Ressourcen im Ordner **MyDscResources**.</span><span class="sxs-lookup"><span data-stu-id="00f59-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="00f59-119">Wenn Sie fertig sind, sollte die Ordnerstruktur wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="00f59-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="00f59-120">Die Ressource kann nun mit dem Cmdlet „Get-DscResource“ gefunden werden, und ihre Eigenschaften können entweder mit diesem Cmdlet oder über die Tastenkombination **STRG+LEERTASTE** (AutoVervollständigen) in Windows PowerShell ISE sichtbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="00f59-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="00f59-121">Verwenden der zusammengesetzten Ressource</span><span class="sxs-lookup"><span data-stu-id="00f59-121">Using the composite resource</span></span>

<span data-ttu-id="00f59-122">Als Nächstes wird eine Konfiguration erstellt, die die zusammengesetzte Ressource aufruft.</span><span class="sxs-lookup"><span data-stu-id="00f59-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="00f59-123">Diese Konfiguration ruft die zusammengesetzte Ressource „xVirtualMachine“ auf, um einen virtuellen Computer zu erstellen, und ruft anschließend die Ressource **xComputer** auf, um sie umzubenennen.</span><span class="sxs-lookup"><span data-stu-id="00f59-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

<span data-ttu-id="00f59-124">Sie können diese Ressource auch zum Erstellen mehrerer VMs verwenden, indem Sie ein Array von VM-Namen an die Ressource „xVirtualMachine“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="00f59-124">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="00f59-125">Unterstützung von PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="00f59-125">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="00f59-126">**PsDscRunAsCredential** wird in PowerShell 5.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="00f59-126">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="00f59-127">Mithilfe der Eigenschaft **PsDscRunAsCredential** kann im Ressourcenblock [DSC configurations](../configurations/configurations.md) angegeben werden, dass die Ressource mit einem festgelegten Satz an Anmeldeinformationen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="00f59-127">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="00f59-128">Weitere Informationen finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="00f59-128">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="00f59-129">Um aus einer benutzerdefinierten Ressource auf den Benutzerkontext zuzugreifen, können Sie die automatische Variable `$PsDscContext` verwenden.</span><span class="sxs-lookup"><span data-stu-id="00f59-129">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="00f59-130">Beispielsweise wird mit dem folgenden Code der Benutzerkontext für die Ressourcenausführung in den ausführlichen Ausgabestream geschrieben:</span><span class="sxs-lookup"><span data-stu-id="00f59-130">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="00f59-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="00f59-131">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="00f59-132">Konzepte</span><span class="sxs-lookup"><span data-stu-id="00f59-132">Concepts</span></span>
* [<span data-ttu-id="00f59-133">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="00f59-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="00f59-134">Erste Schritte mit Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="00f59-134">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
