---
title: Erstellen eines Windows PowerShell-Laufwerk Anbieters | Microsoft-Dokumentation
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
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366829"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="1db4d-102">Erstellen eines Windows PowerShell-Laufwerkanbieters</span><span class="sxs-lookup"><span data-stu-id="1db4d-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="1db4d-103">In diesem Thema wird beschrieben, wie Sie einen Windows PowerShell-Laufwerks Anbieter erstellen, der die Möglichkeit bietet, über ein Windows PowerShell-Laufwerk auf einen Datenspeicher zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="1db4d-104">Diese Art von Anbieter wird auch als Windows PowerShell-Laufwerks Anbieter bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="1db4d-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="1db4d-105">Die vom Anbieter verwendeten Windows PowerShell-Laufwerke bieten die Möglichkeit, eine Verbindung mit dem Datenspeicher herzustellen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="1db4d-106">Der hier beschriebene Windows PowerShell-Laufwerks Anbieter ermöglicht den Zugriff auf eine Microsoft Access-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="1db4d-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="1db4d-107">Für diesen Anbieter stellt das Windows PowerShell-Laufwerk die Datenbank dar (es ist möglich, einem Laufwerks Anbieter eine beliebige Anzahl von Laufwerken hinzuzufügen), die Container der obersten Ebene des Laufwerks repräsentieren die Tabellen in der Datenbank, und die Elemente der Container repräsentieren die Zeilen in die Tabellen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="1db4d-108">Definieren der Windows PowerShell-Anbieter Klasse</span><span class="sxs-lookup"><span data-stu-id="1db4d-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="1db4d-109">Der Laufwerk Anbieter muss eine .NET-Klasse definieren, die von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Basisklasse abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="1db4d-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="1db4d-110">Hier ist die Klassendefinition für diesen Laufwerks Anbieter:</span><span class="sxs-lookup"><span data-stu-id="1db4d-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="1db4d-111">Beachten Sie, dass das [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attribut in diesem Beispiel einen benutzerfreundlichen Namen für den Anbieter und die Windows PowerShell-spezifischen Funktionen angibt, die der Anbieter für Windows verfügbar macht. PowerShell-Laufzeit während der Befehls Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="1db4d-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="1db4d-112">Die möglichen Werte für die Anbieter Funktionen werden von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration definiert.</span><span class="sxs-lookup"><span data-stu-id="1db4d-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="1db4d-113">Dieser Laufwerk Anbieter unterstützt diese Funktionen nicht.</span><span class="sxs-lookup"><span data-stu-id="1db4d-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="1db4d-114">Definieren der Basisfunktionalität</span><span class="sxs-lookup"><span data-stu-id="1db4d-114">Defining Base Functionality</span></span>

<span data-ttu-id="1db4d-115">Wie unter [Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)beschrieben, wird die [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse von der [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Basisklasse abgeleitet, die definiert die Methoden, die zum Initialisieren und Aufheben der Initialisierung des Anbieters erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="1db4d-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="1db4d-116">Informationen zum Implementieren von Funktionen zum Hinzufügen von Sitzungs spezifischen Initialisierungs Informationen und zum Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1db4d-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="1db4d-117">Die meisten Anbieter (einschließlich des hier beschriebenen Anbieters) können jedoch die Standard Implementierung dieser Funktionalität verwenden, die von Windows PowerShell bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1db4d-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="1db4d-118">Erstellen von Laufwerks Zustandsinformationen</span><span class="sxs-lookup"><span data-stu-id="1db4d-118">Creating Drive State Information</span></span>

<span data-ttu-id="1db4d-119">Alle Windows PowerShell-Anbieter gelten als zustandslos. Dies bedeutet, dass Ihr Laufwerks Anbieter alle Zustandsinformationen erstellen muss, die von der Windows PowerShell-Laufzeit benötigt werden, wenn der Anbieter aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1db4d-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="1db4d-120">Bei diesem Laufwerk Anbieter enthalten Zustandsinformationen die Verbindung mit der Datenbank, die als Teil der Laufwerk Informationen beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="1db4d-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="1db4d-121">Der folgende Code zeigt, wie diese Informationen im [System. Management. Automation. psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt gespeichert werden, das das Laufwerk beschreibt:</span><span class="sxs-lookup"><span data-stu-id="1db4d-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="1db4d-122">Erstellen eines Laufwerks</span><span class="sxs-lookup"><span data-stu-id="1db4d-122">Creating a Drive</span></span>

<span data-ttu-id="1db4d-123">Damit die Windows PowerShell-Laufzeit ein Laufwerk erstellen kann, muss der Laufwerk Anbieter die [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode implementieren.</span><span class="sxs-lookup"><span data-stu-id="1db4d-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="1db4d-124">Der folgende Code zeigt die Implementierung der [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode für diesen Laufwerk Anbieter:</span><span class="sxs-lookup"><span data-stu-id="1db4d-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="1db4d-125">Die außer Kraft setzung dieser Methode sollte folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="1db4d-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="1db4d-126">Überprüfen Sie, ob der Member " [System. Management. Automation. psdriveinfo. root \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) " vorhanden ist und eine Verbindung mit dem Datenspeicher hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1db4d-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="1db4d-127">Erstellen Sie ein Laufwerk, und füllen Sie das Verbindungs Mitglied auf, um das Cmdlet "`New-PSDrive`" zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="1db4d-128">Überprüfen Sie das [System. Management. Automation. psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt für das vorgeschlagene Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="1db4d-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="1db4d-129">Ändern Sie das [System. Management. Automation. psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt, das das Laufwerk mit den erforderlichen Leistungs-oder Zuverlässigkeits Informationen beschreibt, oder stellen Sie zusätzliche Daten für Aufrufer mit dem Laufwerk bereit.</span><span class="sxs-lookup"><span data-stu-id="1db4d-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="1db4d-130">Behandeln Sie Fehler mithilfe der [System. Management. Automation. Provider. cmdletprovider. Write-error](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) -Methode, und geben Sie dann `null` zurück.</span><span class="sxs-lookup"><span data-stu-id="1db4d-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="1db4d-131">Diese Methode gibt entweder die Laufwerk Informationen zurück, die an die-Methode oder eine anbieterspezifische Version der Methode übermittelt wurden.</span><span class="sxs-lookup"><span data-stu-id="1db4d-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="1db4d-132">Dynamische Parameter werden an newdrive angefügt.</span><span class="sxs-lookup"><span data-stu-id="1db4d-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="1db4d-133">Das Cmdlet "`New-PSDrive`", das von Ihrem Laufwerk Anbieter unterstützt wird, erfordert möglicherweise zusätzliche Parameter</span><span class="sxs-lookup"><span data-stu-id="1db4d-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="1db4d-134">Um diese dynamischen Parameter an das Cmdlet anzufügen, implementiert der Anbieter die [System. Management. Automation. Provider. drivecmdletprovider. newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) -Methode.</span><span class="sxs-lookup"><span data-stu-id="1db4d-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="1db4d-135">Diese Methode gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln.</span><span class="sxs-lookup"><span data-stu-id="1db4d-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="1db4d-136">Dieser Laufwerk Anbieter setzt diese Methode nicht außer Kraft.</span><span class="sxs-lookup"><span data-stu-id="1db4d-136">This drive provider does not override this method.</span></span> <span data-ttu-id="1db4d-137">Der folgende Code zeigt jedoch die Standard Implementierung dieser Methode:</span><span class="sxs-lookup"><span data-stu-id="1db4d-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="1db4d-138">Entfernen eines Laufwerks</span><span class="sxs-lookup"><span data-stu-id="1db4d-138">Removing a Drive</span></span>

<span data-ttu-id="1db4d-139">Der Laufwerks Anbieter muss die [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode implementieren, um die Datenbankverbindung zu schließen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="1db4d-140">Diese Methode schließt die Verbindung mit dem Laufwerk, nachdem alle anbieterspezifischen Informationen bereinigt wurden.</span><span class="sxs-lookup"><span data-stu-id="1db4d-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="1db4d-141">Der folgende Code zeigt die Implementierung der [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode für diesen Laufwerk Anbieter:</span><span class="sxs-lookup"><span data-stu-id="1db4d-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="1db4d-142">Wenn das Laufwerk entfernt werden kann, sollte die-Methode die an die Methode übergebenen Informationen über den `drive`-Parameter zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="1db4d-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="1db4d-143">Wenn das Laufwerk nicht entfernt werden kann, sollte die Methode eine Ausnahme schreiben und dann `null` zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="1db4d-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="1db4d-144">Wenn der Anbieter diese Methode nicht außer Kraft setzt, gibt die Standard Implementierung dieser Methode nur die als Eingabe übergebenen Laufwerks Informationen zurück.</span><span class="sxs-lookup"><span data-stu-id="1db4d-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="1db4d-145">Standard Laufwerke werden initialisiert.</span><span class="sxs-lookup"><span data-stu-id="1db4d-145">Initializing Default Drives</span></span>

<span data-ttu-id="1db4d-146">Der Laufwerks Anbieter implementiert die [System. Management. Automation. Provider. drivecmdletprovider. initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -Methode zum Einbinden von Laufwerken.</span><span class="sxs-lookup"><span data-stu-id="1db4d-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="1db4d-147">Beispielsweise kann der Active Directory Anbieter ein Laufwerk für den Standard namens Kontext einbinden, wenn der Computer einer Domäne hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1db4d-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="1db4d-148">Diese Methode gibt eine Auflistung von Laufwerk Informationen zu den initialisierten Laufwerken oder eine leere Auflistung zurück.</span><span class="sxs-lookup"><span data-stu-id="1db4d-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="1db4d-149">Der Aufruf dieser Methode erfolgt, nachdem die Windows PowerShell-Runtime die [System. Management. Automation. Provider. cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -Methode aufgerufen hat, um den Anbieter zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="1db4d-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="1db4d-150">Dieser Laufwerk Anbieter setzt die [System. Management. Automation. Provider. drivecmdletprovider. initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) -Methode nicht außer Kraft.</span><span class="sxs-lookup"><span data-stu-id="1db4d-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="1db4d-151">Der folgende Code zeigt jedoch die Standard Implementierung, die eine leere Laufwerks Auflistung zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="1db4d-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="1db4d-152">Dinge, die Sie beim Implementieren von initializedefaultdrives beachten sollten</span><span class="sxs-lookup"><span data-stu-id="1db4d-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="1db4d-153">Alle Laufwerks Anbieter sollten ein Stamm Laufwerk einbinden, um dem Benutzer die Auffindbarkeit zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="1db4d-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="1db4d-154">Das Stamm Laufwerk kann Speicherorte auflisten, die als Stämme für andere eingebundene Laufwerke fungieren.</span><span class="sxs-lookup"><span data-stu-id="1db4d-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="1db4d-155">Beispielsweise kann der Active Directory Anbieter ein Laufwerk erstellen, das die Namenskontexte auflistet, die in den `namingContext`-Attributen der DSE-Stamm Umgebung (DSE) enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="1db4d-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="1db4d-156">Dadurch können Benutzer Einstellungspunkte für andere Laufwerke ermitteln.</span><span class="sxs-lookup"><span data-stu-id="1db4d-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1db4d-157">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="1db4d-157">Code Sample</span></span>

<span data-ttu-id="1db4d-158">Einen umfassenden Beispielcode finden Sie unter [AccessDbProviderSample02-Codebeispiel](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1db4d-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="1db4d-159">Testen des Windows PowerShell-Laufwerks Anbieters</span><span class="sxs-lookup"><span data-stu-id="1db4d-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="1db4d-160">Wenn Ihr Windows PowerShell-Anbieter bei Windows PowerShell registriert wurde, können Sie ihn testen, indem Sie die unterstützten Cmdlets in der Befehlszeile ausführen, einschließlich aller Cmdlets, die durch Ableitung verfügbar gemacht wurden.</span><span class="sxs-lookup"><span data-stu-id="1db4d-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="1db4d-161">Testen Sie den Beispiel Laufwerk Anbieter.</span><span class="sxs-lookup"><span data-stu-id="1db4d-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="1db4d-162">Führen Sie das `Get-PSProvider`-Cmdlet aus, um die Liste der Anbieter abzurufen, um sicherzustellen, dass der accessdb-Laufwerks Anbieter vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="1db4d-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="1db4d-163">**PS > `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="1db4d-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="1db4d-164">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1db4d-164">The following output appears:</span></span>

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

2. <span data-ttu-id="1db4d-165">Stellen Sie sicher, dass ein Datenbankserver Name (DSN) für die Datenbank vorhanden ist, indem Sie auf den **Datenquellen** Teil der **Verwaltungs Tools** für das Betriebssystem zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="1db4d-166">Doppelklicken Sie in der Tabelle **Benutzer-DSN** auf **MS Access Database** , und fügen Sie den Laufwerks Pfad c:\ps\northwind.mdb hinzu.</span><span class="sxs-lookup"><span data-stu-id="1db4d-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="1db4d-167">Erstellen Sie ein neues Laufwerk mithilfe des Beispiel-Laufwerk Anbieters:</span><span class="sxs-lookup"><span data-stu-id="1db4d-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="1db4d-168">**PS > New-PSDrive-Name mydb-root c:\ps\northwind.mdb-psprovider accessdb**</span><span class="sxs-lookup"><span data-stu-id="1db4d-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="1db4d-169">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1db4d-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="1db4d-170">Überprüfen Sie die Verbindung.</span><span class="sxs-lookup"><span data-stu-id="1db4d-170">Validate the connection.</span></span> <span data-ttu-id="1db4d-171">Da die Verbindung als Mitglied des Laufwerks definiert ist, können Sie Sie mithilfe des Cmdlets Get-pddrive überprüfen.</span><span class="sxs-lookup"><span data-stu-id="1db4d-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1db4d-172">Der Benutzer kann noch nicht als Laufwerk mit dem Anbieter interagieren, da der Anbieter für diese Interaktion Container Funktionen benötigt.</span><span class="sxs-lookup"><span data-stu-id="1db4d-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="1db4d-173">Weitere Informationen finden Sie unter [Erstellen eines Windows PowerShell-Container Anbieters](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1db4d-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="1db4d-174">**PS-> (Get-PSDrive mydb). Connection**</span><span class="sxs-lookup"><span data-stu-id="1db4d-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="1db4d-175">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1db4d-175">The following output appears:</span></span>

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

5. <span data-ttu-id="1db4d-176">Entfernen Sie das Laufwerk, und beenden Sie die Shell:</span><span class="sxs-lookup"><span data-stu-id="1db4d-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="1db4d-177">**PS > Remove-PSDrive mydb**</span><span class="sxs-lookup"><span data-stu-id="1db4d-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="1db4d-178">**PS > beenden**</span><span class="sxs-lookup"><span data-stu-id="1db4d-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="1db4d-179">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1db4d-179">See Also</span></span>

[<span data-ttu-id="1db4d-180">Erstellen von Windows PowerShell-Anbietern</span><span class="sxs-lookup"><span data-stu-id="1db4d-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="1db4d-181">Entwerfen Ihres Windows PowerShell-Anbieters</span><span class="sxs-lookup"><span data-stu-id="1db4d-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="1db4d-182">Erstellen eines einfachen Windows PowerShell-Anbieters</span><span class="sxs-lookup"><span data-stu-id="1db4d-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
