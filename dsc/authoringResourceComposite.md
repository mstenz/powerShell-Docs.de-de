---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: 'Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource'
ms.openlocfilehash: 1d5fb89eb9845820de8543f388ddb6aaeaaa3e44
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="bbd7c-103">Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource</span><span class="sxs-lookup"><span data-stu-id="bbd7c-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="bbd7c-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bbd7c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bbd7c-105">In realen Situationen können Konfigurationen lang und komplex sein, viele verschiedene Ressourcen aufrufen und eine große Anzahl von Eigenschaften festlegen.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="bbd7c-106">Um mit dieser Komplexität zurecht zu kommen, können Sie eine Windows PowerShell DSC-Konfiguration als Ressource für andere Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="bbd7c-107">Dies wird als zusammengesetzte Ressource bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-107">We call this a composite resource.</span></span> <span data-ttu-id="bbd7c-108">Eine zusammengesetzte Ressource ist eine DSC-Konfiguration, die Parameter verwendet.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="bbd7c-109">Die Parameter der Konfiguration fungieren als Eigenschaften der Ressource.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="bbd7c-110">Die Konfiguration wird als Datei mit der Erweiterung **.schema.psm1** gespeichert und tritt in einer normalen DSC-Ressource an die Stelle von MOF-Schema und Ressourcenskript (weitere Informationen zu DSC-Ressourcen finden Sie unter [Windows PowerShell DSC-Ressourcen](resources.md).</span><span class="sxs-lookup"><span data-stu-id="bbd7c-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="bbd7c-111">Erstellen der zusammengesetzten Ressource</span><span class="sxs-lookup"><span data-stu-id="bbd7c-111">Creating the composite resource</span></span>

<span data-ttu-id="bbd7c-112">Im folgenden Beispiel wird eine Konfiguration erstellt, die eine Reihe von vorhandenen Ressourcen zum Konfigurieren virtueller Computer aufruft.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="bbd7c-113">Anstatt die festzulegenden Werte in Konfigurationsblöcken anzugeben, verwendet die Konfiguration eine Reihe von Parametern, die dann in den Konfigurationsblöcken verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="bbd7c-114">Speichern die Konfiguration als eine zusammengesetzte Ressource</span><span class="sxs-lookup"><span data-stu-id="bbd7c-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="bbd7c-115">Damit die parametrisierte Konfiguration als DSC-Ressource verwendet werden kann, speichern Sie sie in einer Verzeichnisstruktur, die den Verzeichnisstrukturen MOF-basierter Ressourcen entspricht, und geben Sie ihr einen Namen mit der Erweiterung **.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="bbd7c-116">In diesem Beispiel erhält die Datei den Namen **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="bbd7c-117">Sie müssen auch ein Manifest mit dem Namen **xVirtualMachine.psd1** erstellen, das die folgende Zeile enthält.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="bbd7c-118">Beachten Sie, dass dies zusätzlich zur Datei **MyDscResources.psd1** erforderlich ist, dem Modulmanifest für alle Ressourcen im Ordner **MyDscResources**.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="bbd7c-119">Wenn Sie fertig sind, sollte die Ordnerstruktur wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="bbd7c-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="bbd7c-120">Die Ressource kann nun mit dem Cmdlet „Get-DscResource“ gefunden werden, und ihre Eigenschaften können entweder mit diesem Cmdlet oder über die Tastenkombination **STRG+LEERTASTE** (AutoVervollständigen) in Windows PowerShell ISE sichtbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="bbd7c-121">Verwenden der zusammengesetzten Ressource</span><span class="sxs-lookup"><span data-stu-id="bbd7c-121">Using the composite resource</span></span>

<span data-ttu-id="bbd7c-122">Als Nächstes wird eine Konfiguration erstellt, die die zusammengesetzte Ressource aufruft.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="bbd7c-123">Diese Konfiguration ruft die zusammengesetzte Ressource „xVirtualMachine“ auf, um einen virtuellen Computer zu erstellen, und ruft anschließend die Ressource **xComputer** auf, um sie umzubenennen.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="bbd7c-124">Unterstützung von PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bbd7c-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="bbd7c-125">**Hinweis:** **PsDscRunAsCredential** wird in PowerShell 5.0 und höheren Versionen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="bbd7c-126">Mithilfe der Eigenschaft **PsDscRunAsCredential** kann im Ressourcenblock [DSC configurations](configurations.md) angegeben werden, dass die Ressource mit einem festgelegten Satz an Anmeldeinformationen ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="bbd7c-127">Weitere Informationen finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="bbd7c-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="bbd7c-128">Um aus einer benutzerdefinierten Ressource auf den Benutzerkontext zuzugreifen, können Sie die automatische Variable `$PsDscContext` verwenden.</span><span class="sxs-lookup"><span data-stu-id="bbd7c-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="bbd7c-129">Beispielsweise wird mit dem folgenden Code der Benutzerkontext für die Ressourcenausführung in den ausführlichen Ausgabestream geschrieben:</span><span class="sxs-lookup"><span data-stu-id="bbd7c-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="bbd7c-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bbd7c-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="bbd7c-131">Konzepte</span><span class="sxs-lookup"><span data-stu-id="bbd7c-131">Concepts</span></span>
* [<span data-ttu-id="bbd7c-132">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="bbd7c-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="bbd7c-133">Erste Schritte mit Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="bbd7c-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)

