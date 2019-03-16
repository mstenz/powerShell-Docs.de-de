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
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055648"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="be19e-102">Erstellen eines Windows PowerShell-Laufwerkanbieters</span><span class="sxs-lookup"><span data-stu-id="be19e-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="be19e-103">Dieses Thema beschreibt, wie Sie einen Windows PowerShell-Laufwerk-Anbieter erstellen, der mit einen Datenspeicher über ein Windows PowerShell-Laufwerk zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="be19e-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="be19e-104">Dieser Typ des Anbieters ist auch als Windows PowerShell-Laufwerk-Anbieter bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="be19e-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="be19e-105">Die Windows PowerShell-Laufwerke, die vom Anbieter verwendeten bieten die Möglichkeit, eine Verbindung mit dem Datenspeicher herstellen.</span><span class="sxs-lookup"><span data-stu-id="be19e-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="be19e-106">Die hier beschriebene Windows PowerShell-Laufwerk-Anbieter bietet Zugriff auf eine Microsoft Access-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="be19e-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="be19e-107">Für diesen Anbieter, stellt das Windows PowerShell-Laufwerk (es ist möglich, eine beliebige Anzahl von Laufwerken zu einem laufwerksanbieter hinzufügen) die Datenbank dar, mit der Container der obersten Ebene des Laufwerks darstellen, die Tabellen in der Datenbank und die Elemente der Container stehen für die Zeilen in die Tabellen.</span><span class="sxs-lookup"><span data-stu-id="be19e-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="be19e-108">Hier ist eine Liste der Abschnitte in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="be19e-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="be19e-109">Wenn Sie mit dem Schreiben von Windows PowerShell-Laufwerk-Anbieter nicht vertraut sind, lesen Sie diese Abschnitte in der angezeigten Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="be19e-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="be19e-110">Aber wenn Sie mit dem Schreiben von einem laufwerksanbieter vertraut sind, wechseln Sie direkt auf die Informationen, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="be19e-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="be19e-111">Definieren der Windows PowerShell-Anbieter-Klasse</span><span class="sxs-lookup"><span data-stu-id="be19e-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="be19e-112">Definiert die grundlegenden Funktionen</span><span class="sxs-lookup"><span data-stu-id="be19e-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="be19e-113">Erstellen von Laufwerkstatus-Informationen</span><span class="sxs-lookup"><span data-stu-id="be19e-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="be19e-114">Erstellen ein Laufwerk</span><span class="sxs-lookup"><span data-stu-id="be19e-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="be19e-115">Dynamische Parameter anfügen NewDrive</span><span class="sxs-lookup"><span data-stu-id="be19e-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="be19e-116">Entfernen ein Laufwerk</span><span class="sxs-lookup"><span data-stu-id="be19e-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="be19e-117">Initialisieren von Standard-Laufwerke</span><span class="sxs-lookup"><span data-stu-id="be19e-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="be19e-118">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="be19e-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="be19e-119">Testen des Anbieters der Windows PowerShell-Laufwerk</span><span class="sxs-lookup"><span data-stu-id="be19e-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="be19e-120">Definieren der Windows PowerShell-Anbieter-Klasse</span><span class="sxs-lookup"><span data-stu-id="be19e-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="be19e-121">Die Laufwerk-Anbieter muss eine abgeleitete Klasse .NET definieren die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="be19e-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="be19e-122">So sieht die Klassendefinition für dieses Laufwerk-Anbieter aus:</span><span class="sxs-lookup"><span data-stu-id="be19e-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="be19e-123">Beachten Sie, dass in diesem Beispiel die [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut gibt an, einen benutzerfreundlichen Namen für den Anbieter und den Windows PowerShell-spezifischen Funktionen, die der Anbieter macht die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="be19e-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="be19e-124">Die möglichen Werte für die Funktionen des Anbieters werden definiert, durch die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration.</span><span class="sxs-lookup"><span data-stu-id="be19e-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="be19e-125">Dieses Laufwerk-Anbieter unterstützt keine dieser Funktionen.</span><span class="sxs-lookup"><span data-stu-id="be19e-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="be19e-126">Definiert die grundlegenden Funktionen</span><span class="sxs-lookup"><span data-stu-id="be19e-126">Defining Base Functionality</span></span>

<span data-ttu-id="be19e-127">Siehe [Entwurf der Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse leitet sich von der [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Basisklasse, die die Methoden, die erforderlich sind, für das Initialisieren und zum Aufheben der Initialisierung des Anbieters definiert.</span><span class="sxs-lookup"><span data-stu-id="be19e-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="be19e-128">Zum Implementieren der Funktionalität, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="be19e-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="be19e-129">Allerdings können die meisten Anbieter (einschließlich des hier beschriebenen Anbieters) die standardmäßige Implementierung dieser Funktionalität, die von Windows PowerShell bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="be19e-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="be19e-130">Erstellen von Laufwerkstatus-Informationen</span><span class="sxs-lookup"><span data-stu-id="be19e-130">Creating Drive State Information</span></span>

<span data-ttu-id="be19e-131">Alle Windows PowerShell-Anbieter werden statusfrei sein, berücksichtigt, was bedeutet, dass es sich bei Ihrem laufwerksanbieter muss alle Zustandsinformationen zu erstellen, die von der Windows PowerShell-Laufzeit benötigt wird, wenn Ihr Anbieter aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="be19e-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="be19e-132">Für diesen laufwerksanbieter enthält Zustandsinformationen für die Verbindung mit der Datenbank, die als Teil der Informationen zum Laufwerk gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="be19e-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="be19e-133">Hier ist der Code, der zeigt, wie diese Informationen gespeichert werden, in der [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt, das Laufwerk beschreibt:</span><span class="sxs-lookup"><span data-stu-id="be19e-133">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="be19e-134">Erstellen ein Laufwerk</span><span class="sxs-lookup"><span data-stu-id="be19e-134">Creating a Drive</span></span>

<span data-ttu-id="be19e-135">Damit wird die Windows PowerShell-Laufzeit, um ein Laufwerk zu erstellen, muss die Laufwerk-Anbieter implementieren die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode.</span><span class="sxs-lookup"><span data-stu-id="be19e-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="be19e-136">Der folgende Code zeigt die Implementierung der [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode für diesen laufwerksanbieter:</span><span class="sxs-lookup"><span data-stu-id="be19e-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="be19e-137">Ihre Überschreibung der diese Methode sollte folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="be19e-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="be19e-138">Überprüfen Sie, ob die [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) Element vorhanden ist und, die eine Verbindung mit dem Datenspeicher hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="be19e-138">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="be19e-139">Erstellen Sie ein Laufwerk, und füllen Sie das Verbindung-Mitglied, Unterstützung des der `New-PSDrive` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be19e-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="be19e-140">Überprüfen Sie die [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt für das vorgeschlagene Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="be19e-140">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="be19e-141">Ändern der [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) Objekt, das Laufwerk mit allen erforderlichen Leistung oder Zuverlässigkeit Informationen beschreibt, oder geben Sie zusätzliche Daten, für das Laufwerk mit Aufrufer.</span><span class="sxs-lookup"><span data-stu-id="be19e-141">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="be19e-142">Behandeln von Fehlern, die mit der [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, und klicken Sie dann geben `null`.</span><span class="sxs-lookup"><span data-stu-id="be19e-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="be19e-143">Diese Methode gibt die Laufwerkinformationen, die übergeben wurde, auf die Methode oder eine anbieterspezifische-Version des Zertifikats.</span><span class="sxs-lookup"><span data-stu-id="be19e-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="be19e-144">Dynamische Parameter anfügen NewDrive</span><span class="sxs-lookup"><span data-stu-id="be19e-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="be19e-145">Die `New-PSDrive` Cmdlets, die von Ihrem laufwerksanbieter unterstützt möglicherweise zusätzliche Parameter.</span><span class="sxs-lookup"><span data-stu-id="be19e-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="be19e-146">Um diese dynamischen Parameter an das Cmdlet anzufügen, die den Anbieter implementiert die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) Methode.</span><span class="sxs-lookup"><span data-stu-id="be19e-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="be19e-147">Diese Methode gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt.</span><span class="sxs-lookup"><span data-stu-id="be19e-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="be19e-148">Dieses Laufwerk-Anbieter überschreibt diese Methode nicht.</span><span class="sxs-lookup"><span data-stu-id="be19e-148">This drive provider does not override this method.</span></span> <span data-ttu-id="be19e-149">Der folgende Code zeigt jedoch die Standardimplementierung dieser Methode:</span><span class="sxs-lookup"><span data-stu-id="be19e-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="be19e-150">Entfernen ein Laufwerk</span><span class="sxs-lookup"><span data-stu-id="be19e-150">Removing a Drive</span></span>

<span data-ttu-id="be19e-151">Zum Schließen der Verbindung mit der der laufwerksanbieter implementieren muss die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode.</span><span class="sxs-lookup"><span data-stu-id="be19e-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="be19e-152">Diese Methode schließt die Verbindung auf das Laufwerk nach dem Bereinigen alle Anbieter-spezifischen Informationen.</span><span class="sxs-lookup"><span data-stu-id="be19e-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="be19e-153">Der folgende Code zeigt die Implementierung der [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode für diesen laufwerksanbieter:</span><span class="sxs-lookup"><span data-stu-id="be19e-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="be19e-154">Wenn das Laufwerk entfernt werden kann, sollte die Methode über an die Methode übergebenen Informationen zurückgeben der `drive` Parameter.</span><span class="sxs-lookup"><span data-stu-id="be19e-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="be19e-155">Wenn das Laufwerk kann nicht entfernt werden, die Methode eine Ausnahme schreiben und dann zurückkehren soll `null`.</span><span class="sxs-lookup"><span data-stu-id="be19e-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="be19e-156">Wenn Ihr Anbieter diese Methode nicht überschreibt, gibt die Standardimplementierung dieser Methode nur die Laufwerkinformationen, die als Eingabe übergeben.</span><span class="sxs-lookup"><span data-stu-id="be19e-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="be19e-157">Initialisieren von Standard-Laufwerke</span><span class="sxs-lookup"><span data-stu-id="be19e-157">Initializing Default Drives</span></span>

<span data-ttu-id="be19e-158">Die Laufwerk-Anbieter implementiert die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode, um die Laufwerke bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="be19e-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="be19e-159">Active Directory-Anbieter stellen z. B. kann ein Laufwerk für den Standardnamenskontext, wenn der Computer einer Domäne angehört.</span><span class="sxs-lookup"><span data-stu-id="be19e-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="be19e-160">Diese Methode gibt eine Auflistung von Laufwerkinformationen zu den initialisierten Laufwerken oder eine leere Auflistung zurück.</span><span class="sxs-lookup"><span data-stu-id="be19e-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="be19e-161">Der Aufruf dieser Methode erfolgt nach dem Aufrufen der Windows PowerShell-Laufzeit die [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, um den Anbieter zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="be19e-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="be19e-162">Dieses Laufwerk-Anbieter überschreibt nicht die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode.</span><span class="sxs-lookup"><span data-stu-id="be19e-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="be19e-163">Der folgende Code zeigt jedoch die Standardimplementierung, die eine leeres Laufwerk Auflistung zurückgibt:</span><span class="sxs-lookup"><span data-stu-id="be19e-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="be19e-164">Punkte zu beachten, die zum Implementieren von InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="be19e-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="be19e-165">Alle Laufwerk-Anbieter sollte ein Stammlaufwerk, die der Benutzer mit Erkennbarkeit helfen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="be19e-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="be19e-166">Das Stammlaufwerk möglicherweise Standorte aufzulisten, die als Stämme für andere bereitgestellten Laufwerken dienen.</span><span class="sxs-lookup"><span data-stu-id="be19e-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="be19e-167">Active Directory-Anbieter kann beispielsweise ein Laufwerk, das listet Namenskontexte finden Sie im Erstellen der `namingContext` Attribute für den Stamm verteilte Umgebung (DSE).</span><span class="sxs-lookup"><span data-stu-id="be19e-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="be19e-168">Dadurch können Benutzer, die Bereitstellungspunkte für andere Laufwerke zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="be19e-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="be19e-169">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="be19e-169">Code Sample</span></span>

<span data-ttu-id="be19e-170">Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample02 Codebeispiel](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="be19e-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="be19e-171">Testen des Anbieters der Windows PowerShell-Laufwerk</span><span class="sxs-lookup"><span data-stu-id="be19e-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="be19e-172">Wenn Ihre Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, durch Ausführen der unterstützten Cmdlets in der Befehlszeile, einschließlich alle Cmdlets, die durch Ableitung zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="be19e-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="be19e-173">Testen Sie nun den laufwerksanbieter Beispiel.</span><span class="sxs-lookup"><span data-stu-id="be19e-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="be19e-174">Führen Sie die `Get-PSProvider` -Cmdlet zum Abrufen der Liste der Anbieter, um sicherzustellen, dass es sich bei der laufwerksanbieter AccessDB vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="be19e-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="be19e-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="be19e-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="be19e-176">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="be19e-176">The following output appears:</span></span>

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

2. <span data-ttu-id="be19e-177">Stellen Sie sicher, dass für die Datenbank ein Datenbank-Servernamen (DSN) vorhanden ist, durch den Zugriff auf die **Datenquellen** Teil der **Verwaltung** für das Betriebssystem.</span><span class="sxs-lookup"><span data-stu-id="be19e-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="be19e-178">In der **Benutzer-DSN** table, doppelklicken Sie auf **MS Access-Datenbank** und den Pfad zum Laufwerk C:\ps\northwind.mdb hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="be19e-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="be19e-179">Erstellen Sie ein neues Laufwerk, das mit dem Beispiel Laufwerk-Anbieter:</span><span class="sxs-lookup"><span data-stu-id="be19e-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="be19e-180">**PS > Neues Psdrive-Namen Mydb-root-c:\ps\northwind.mdb - Psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="be19e-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="be19e-181">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="be19e-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="be19e-182">Überprüfen der Verbindung an.</span><span class="sxs-lookup"><span data-stu-id="be19e-182">Validate the connection.</span></span> <span data-ttu-id="be19e-183">Da die Verbindung als Mitglied des Laufwerks definiert ist, können Sie es mit dem Cmdlet Get-PDDrive überprüfen.</span><span class="sxs-lookup"><span data-stu-id="be19e-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="be19e-184">Der Benutzer kann nicht mit dem Anbieter als Laufwerk noch interagieren, wie der Anbieter Containerfunktionalität für diese Interaktion benötigt.</span><span class="sxs-lookup"><span data-stu-id="be19e-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="be19e-185">Weitere Informationen finden Sie unter [erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="be19e-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="be19e-186">**PS > (Get-Psdrive Mydb) .connection**</span><span class="sxs-lookup"><span data-stu-id="be19e-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="be19e-187">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="be19e-187">The following output appears:</span></span>

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

5. <span data-ttu-id="be19e-188">Entfernen Sie das Laufwerk, und beenden Sie die Shell aus:</span><span class="sxs-lookup"><span data-stu-id="be19e-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="be19e-189">**PS > Remove-Psdrive Mydb**</span><span class="sxs-lookup"><span data-stu-id="be19e-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="be19e-190">**PS > Beenden**</span><span class="sxs-lookup"><span data-stu-id="be19e-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="be19e-191">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="be19e-191">See Also</span></span>

[<span data-ttu-id="be19e-192">Erstellen von Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="be19e-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="be19e-193">Entwerfen Sie Ihre Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="be19e-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="be19e-194">Erstellen einen einfachen Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="be19e-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)