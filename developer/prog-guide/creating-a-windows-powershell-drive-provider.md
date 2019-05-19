---
title: Erstellen eines Anbieters der Windows PowerShell-Laufwerk | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855207"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="b571a-102">Erstellen eines Windows PowerShell-Laufwerkanbieters</span><span class="sxs-lookup"><span data-stu-id="b571a-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b571a-103">Dieses Thema beschreibt, wie Sie einen Windows PowerShell-Laufwerk-Anbieter erstellen, der mit einen Datenspeicher über ein Windows PowerShell-Laufwerk zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="b571a-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="b571a-104">Dieser Typ des Anbieters ist auch als Windows PowerShell-Laufwerk-Anbieter bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b571a-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="b571a-105">Die Windows PowerShell-Laufwerke, die vom Anbieter verwendeten bieten die Möglichkeit, eine Verbindung mit dem Datenspeicher herstellen.</span><span class="sxs-lookup"><span data-stu-id="b571a-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="b571a-106">Die hier beschriebene Windows PowerShell-Laufwerk-Anbieter bietet Zugriff auf eine Microsoft Access-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="b571a-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="b571a-107">Für diesen Anbieter, stellt das Windows PowerShell-Laufwerk (es ist möglich, eine beliebige Anzahl von Laufwerken zu einem laufwerksanbieter hinzufügen) die Datenbank dar, mit der Container der obersten Ebene des Laufwerks darstellen, die Tabellen in der Datenbank und die Elemente der Container stehen für die Zeilen in die Tabellen.</span><span class="sxs-lookup"><span data-stu-id="b571a-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="b571a-108">Definieren der Windows PowerShell-Anbieter-Klasse</span><span class="sxs-lookup"><span data-stu-id="b571a-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="b571a-109">Die Laufwerk-Anbieter muss eine abgeleitete Klasse .NET definieren die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="b571a-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="b571a-110">So sieht die Klassendefinition für dieses Laufwerk-Anbieter aus:</span><span class="sxs-lookup"><span data-stu-id="b571a-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b571a-111">Beachten Sie, dass in diesem Beispiel die [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut gibt an, einen benutzerfreundlichen Namen für den Anbieter und den Windows PowerShell-spezifischen Funktionen, die der Anbieter macht die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b571a-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="b571a-112">Die möglichen Werte für die Funktionen des Anbieters werden definiert, durch die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration.</span><span class="sxs-lookup"><span data-stu-id="b571a-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="b571a-113">Dieses Laufwerk-Anbieter unterstützt keine dieser Funktionen.</span><span class="sxs-lookup"><span data-stu-id="b571a-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="b571a-114">Definiert die grundlegenden Funktionen</span><span class="sxs-lookup"><span data-stu-id="b571a-114">Defining Base Functionality</span></span>

<span data-ttu-id="b571a-115">Siehe [Entwurf der Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse leitet sich von der [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Basisklasse, die die Methoden, die erforderlich sind, für das Initialisieren und zum Aufheben der Initialisierung des Anbieters definiert.</span><span class="sxs-lookup"><span data-stu-id="b571a-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="b571a-116">Zum Implementieren der Funktionalität, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b571a-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="b571a-117">Allerdings können die meisten Anbieter (einschließlich des hier beschriebenen Anbieters) die standardmäßige Implementierung dieser Funktionalität, die von Windows PowerShell bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b571a-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="b571a-118">Erstellen von Laufwerkstatus-Informationen</span><span class="sxs-lookup"><span data-stu-id="b571a-118">Creating Drive State Information</span></span>

<span data-ttu-id="b571a-119">Alle Windows PowerShell-Anbieter werden statusfrei sein, berücksichtigt, was bedeutet, dass es sich bei Ihrem laufwerksanbieter muss alle Zustandsinformationen zu erstellen, die von der Windows PowerShell-Laufzeit benötigt wird, wenn Ihr Anbieter aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b571a-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="b571a-120">Für diesen laufwerksanbieter enthält Zustandsinformationen für die Verbindung mit der Datenbank, die als Teil der Informationen zum Laufwerk gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="b571a-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="b571a-121">Hier ist der Code, der zeigt, wie diese Informationen gespeichert werden, in der [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt, das Laufwerk beschreibt:</span><span class="sxs-lookup"><span data-stu-id="b571a-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="b571a-122">Erstellen ein Laufwerk</span><span class="sxs-lookup"><span data-stu-id="b571a-122">Creating a Drive</span></span>

<span data-ttu-id="b571a-123">Damit wird die Windows PowerShell-Laufzeit, um ein Laufwerk zu erstellen, muss die Laufwerk-Anbieter implementieren die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode.</span><span class="sxs-lookup"><span data-stu-id="b571a-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="b571a-124">Der folgende Code zeigt die Implementierung der [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode für diesen laufwerksanbieter:</span><span class="sxs-lookup"><span data-stu-id="b571a-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b571a-125">Ihre Überschreibung der diese Methode sollte folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="b571a-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="b571a-126">Überprüfen Sie, ob die [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) Element vorhanden ist und, die eine Verbindung mit dem Datenspeicher hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b571a-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="b571a-127">Erstellen Sie ein Laufwerk, und füllen Sie das Verbindung-Mitglied, Unterstützung des der `New-PSDrive` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b571a-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="b571a-128">Überprüfen Sie die [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt für das vorgeschlagene Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="b571a-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="b571a-129">Ändern der [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) Objekt, das Laufwerk mit allen erforderlichen Leistung oder Zuverlässigkeit Informationen beschreibt, oder geben Sie zusätzliche Daten, für das Laufwerk mit Aufrufer.</span><span class="sxs-lookup"><span data-stu-id="b571a-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="b571a-130">Behandeln von Fehlern, die mit der [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, und klicken Sie dann geben `null`.</span><span class="sxs-lookup"><span data-stu-id="b571a-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="b571a-131">Diese Methode gibt die Laufwerkinformationen, die übergeben wurde, auf die Methode oder eine anbieterspezifische-Version des Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="b571a-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="b571a-132">Dynamische Parameter anfügen NewDrive</span><span class="sxs-lookup"><span data-stu-id="b571a-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="b571a-133">Die `New-PSDrive` Cmdlets, die von Ihrem laufwerksanbieter unterstützt möglicherweise zusätzliche Parameter.</span><span class="sxs-lookup"><span data-stu-id="b571a-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="b571a-134">Um diese dynamischen Parameter an das Cmdlet anzufügen, die den Anbieter implementiert die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) Methode.</span><span class="sxs-lookup"><span data-stu-id="b571a-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="b571a-135">Diese Methode gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt.</span><span class="sxs-lookup"><span data-stu-id="b571a-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="b571a-136">Dieses Laufwerk-Anbieter überschreibt diese Methode nicht.</span><span class="sxs-lookup"><span data-stu-id="b571a-136">This drive provider does not override this method.</span></span> <span data-ttu-id="b571a-137">Der folgende Code zeigt jedoch die Standardimplementierung dieser Methode:</span><span class="sxs-lookup"><span data-stu-id="b571a-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="b571a-138">Entfernen ein Laufwerk</span><span class="sxs-lookup"><span data-stu-id="b571a-138">Removing a Drive</span></span>

<span data-ttu-id="b571a-139">Zum Schließen der Verbindung mit der der laufwerksanbieter implementieren muss die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode.</span><span class="sxs-lookup"><span data-stu-id="b571a-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="b571a-140">Diese Methode schließt die Verbindung auf das Laufwerk nach dem Bereinigen alle Anbieter-spezifischen Informationen.</span><span class="sxs-lookup"><span data-stu-id="b571a-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="b571a-141">Der folgende Code zeigt die Implementierung der [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode für diesen laufwerksanbieter:</span><span class="sxs-lookup"><span data-stu-id="b571a-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b571a-142">Wenn das Laufwerk entfernt werden kann, sollte die Methode über an die Methode übergebenen Informationen zurückgeben der `drive` Parameter.</span><span class="sxs-lookup"><span data-stu-id="b571a-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="b571a-143">Wenn das Laufwerk kann nicht entfernt werden, die Methode eine Ausnahme schreiben und dann zurückkehren soll `null`.</span><span class="sxs-lookup"><span data-stu-id="b571a-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="b571a-144">Wenn Ihr Anbieter diese Methode nicht überschreibt, gibt die Standardimplementierung dieser Methode nur die Laufwerkinformationen, die als Eingabe übergeben.</span><span class="sxs-lookup"><span data-stu-id="b571a-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="b571a-145">Initialisieren von Standard-Laufwerke</span><span class="sxs-lookup"><span data-stu-id="b571a-145">Initializing Default Drives</span></span>

<span data-ttu-id="b571a-146">Die Laufwerk-Anbieter implementiert die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode, um die Laufwerke bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b571a-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="b571a-147">Active Directory-Anbieter stellen z. B. kann ein Laufwerk für den Standardnamenskontext, wenn der Computer einer Domäne angehört.</span><span class="sxs-lookup"><span data-stu-id="b571a-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="b571a-148">Diese Methode gibt eine Auflistung von Laufwerkinformationen zu den initialisierten Laufwerken oder eine leere Auflistung zurück.</span><span class="sxs-lookup"><span data-stu-id="b571a-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="b571a-149">Der Aufruf dieser Methode erfolgt nach dem Aufrufen der Windows PowerShell-Laufzeit die [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, um den Anbieter zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="b571a-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="b571a-150">Dieses Laufwerk-Anbieter überschreibt nicht die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode.</span><span class="sxs-lookup"><span data-stu-id="b571a-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="b571a-151">Der folgende Code zeigt jedoch die Standardimplementierung, die eine leeres Laufwerk Auflistung zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="b571a-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="b571a-152">Punkte zu beachten, die zum Implementieren von InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="b571a-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="b571a-153">Alle Laufwerk-Anbieter sollte ein Stammlaufwerk, die der Benutzer mit Erkennbarkeit helfen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b571a-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="b571a-154">Das Stammlaufwerk möglicherweise Standorte aufzulisten, die als Stämme für andere bereitgestellten Laufwerken dienen.</span><span class="sxs-lookup"><span data-stu-id="b571a-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="b571a-155">Active Directory-Anbieter kann beispielsweise ein Laufwerk, das listet Namenskontexte finden Sie im Erstellen der `namingContext` Attribute für den Stamm verteilte Umgebung (DSE).</span><span class="sxs-lookup"><span data-stu-id="b571a-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="b571a-156">Dadurch können Benutzer, die Bereitstellungspunkte für andere Laufwerke zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b571a-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b571a-157">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="b571a-157">Code Sample</span></span>

<span data-ttu-id="b571a-158">Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample02 Codebeispiel](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b571a-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="b571a-159">Testen des Anbieters der Windows PowerShell-Laufwerk</span><span class="sxs-lookup"><span data-stu-id="b571a-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b571a-160">Wenn Ihre Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, durch Ausführen der unterstützten Cmdlets in der Befehlszeile, einschließlich alle Cmdlets, die durch Ableitung zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="b571a-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="b571a-161">Testen Sie nun den laufwerksanbieter Beispiel.</span><span class="sxs-lookup"><span data-stu-id="b571a-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="b571a-162">Führen Sie die `Get-PSProvider` -Cmdlet zum Abrufen der Liste der Anbieter, um sicherzustellen, dass es sich bei der laufwerksanbieter AccessDB vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="b571a-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="b571a-163">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="b571a-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="b571a-164">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b571a-164">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="b571a-165">Stellen Sie sicher, dass für die Datenbank ein Datenbank-Servernamen (DSN) vorhanden ist, durch den Zugriff auf die **Datenquellen** Teil der **Verwaltung** für das Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="b571a-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="b571a-166">In der **Benutzer-DSN** table, doppelklicken Sie auf **MS Access-Datenbank** und den Pfad zum Laufwerk C:\ps\northwind.mdb hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b571a-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="b571a-167">Erstellen Sie ein neues Laufwerk, das mit dem Beispiel Laufwerk-Anbieter:</span><span class="sxs-lookup"><span data-stu-id="b571a-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="b571a-168">**PS > Neues Psdrive-Namen Mydb-root-c:\ps\northwind.mdb - Psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="b571a-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="b571a-169">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b571a-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="b571a-170">Überprüfen der Verbindung an.</span><span class="sxs-lookup"><span data-stu-id="b571a-170">Validate the connection.</span></span> <span data-ttu-id="b571a-171">Da die Verbindung als Mitglied des Laufwerks definiert ist, können Sie es mit dem Cmdlet Get-PDDrive überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b571a-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b571a-172">Der Benutzer kann nicht mit dem Anbieter als Laufwerk noch interagieren, wie der Anbieter Containerfunktionalität für diese Interaktion benötigt.</span><span class="sxs-lookup"><span data-stu-id="b571a-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="b571a-173">Weitere Informationen finden Sie unter [erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b571a-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="b571a-174">**PS > (Get-Psdrive Mydb) .connection**</span><span class="sxs-lookup"><span data-stu-id="b571a-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="b571a-175">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b571a-175">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="b571a-176">Entfernen Sie das Laufwerk, und beenden Sie die Shell aus:</span><span class="sxs-lookup"><span data-stu-id="b571a-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="b571a-177">**PS > Remove-Psdrive Mydb**</span><span class="sxs-lookup"><span data-stu-id="b571a-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="b571a-178">**PS > Beenden**</span><span class="sxs-lookup"><span data-stu-id="b571a-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="b571a-179">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b571a-179">See Also</span></span>

[<span data-ttu-id="b571a-180">Erstellen von Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="b571a-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="b571a-181">Entwerfen Sie Ihre Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="b571a-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="b571a-182">Erstellen einen einfachen Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="b571a-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)