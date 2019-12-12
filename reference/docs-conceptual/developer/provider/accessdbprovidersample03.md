---
title: AccessDBProviderSample03 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359989"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="4e7c9-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="4e7c9-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="4e7c9-103">In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Provider. itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System. Management. Automation. Provider. itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) überschrieben werden, um Aufrufe an die `Get-Item`-und `Set-Item`-Cmdlets zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="4e7c9-104">Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4e7c9-105">Gegenstand</span><span class="sxs-lookup"><span data-stu-id="4e7c9-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e7c9-106">Ihre Anbieter Klasse wird wahrscheinlich von einer der folgenden Klassen abgeleitet und kann möglicherweise andere Anbieter Schnittstellen implementieren:</span><span class="sxs-lookup"><span data-stu-id="4e7c9-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="4e7c9-107">[System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="4e7c9-108">[System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="4e7c9-109">Siehe [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="4e7c9-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="4e7c9-110">[System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="4e7c9-111">Siehe [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="4e7c9-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="4e7c9-112">Weitere Informationen zum Auswählen der Anbieter Klasse, von der basierend auf den Anbieter Features abgeleitet werden soll, finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="4e7c9-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="4e7c9-113">Dieses Beispiel zeigt die folgenden Vorgänge:</span><span class="sxs-lookup"><span data-stu-id="4e7c9-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="4e7c9-114">Deklarieren des `CmdletProvider` Attributs.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="4e7c9-115">Definieren einer Anbieter Klasse, die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="4e7c9-116">Überschreiben der [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode, um das Verhalten des `New-PSDrive`-Cmdlets zu ändern, sodass der Benutzer neue Laufwerke erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="4e7c9-117">(In diesem Beispiel wird nicht gezeigt, wie dem `New-PSDrive`-Cmdlet dynamische Parameter hinzugefügt werden.)</span><span class="sxs-lookup"><span data-stu-id="4e7c9-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="4e7c9-118">Überschreiben der [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode, um das Entfernen vorhandener Laufwerke zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="4e7c9-119">Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -Methode, um das Verhalten des `Get-Item`-Cmdlets zu ändern, sodass der Benutzer Elemente aus dem Datenspeicher abrufen kann.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="4e7c9-120">(In diesem Beispiel wird nicht gezeigt, wie dem `Get-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)</span><span class="sxs-lookup"><span data-stu-id="4e7c9-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="4e7c9-121">Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) -Methode, um das Verhalten des `Set-Item`-Cmdlets zu ändern, sodass der Benutzer die Elemente im Datenspeicher aktualisieren kann.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="4e7c9-122">(In diesem Beispiel wird nicht gezeigt, wie dem `Get-Item`-Cmdlet dynamische Parameter hinzugefügt werden.)</span><span class="sxs-lookup"><span data-stu-id="4e7c9-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="4e7c9-123">Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -Methode, um das Verhalten des `Test-Path`-Cmdlets zu ändern.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="4e7c9-124">(In diesem Beispiel wird nicht gezeigt, wie dem `Test-Path`-Cmdlet dynamische Parameter hinzugefügt werden.)</span><span class="sxs-lookup"><span data-stu-id="4e7c9-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="4e7c9-125">Überschreiben der [System. Management. Automation. Provider. itemcmdletprovider. IsValidPath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) -Methode, um zu bestimmen, ob der angegebene Pfad gültig ist.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="4e7c9-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4e7c9-126">Example</span></span>

<span data-ttu-id="4e7c9-127">Dieses Beispiel zeigt, wie Sie die Methoden überschreiben, die zum Abrufen und Festlegen von Elementen in einer Microsoft Access-Datenbank erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="4e7c9-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="4e7c9-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4e7c9-128">See Also</span></span>

[<span data-ttu-id="4e7c9-129">System. Management. Automation. Provider. itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="4e7c9-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="4e7c9-130">System. Management. Automation. Provider. containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="4e7c9-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="4e7c9-131">System. Management. Automation. Provider. navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="4e7c9-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="4e7c9-132">Entwerfen Ihres Windows PowerShell-Anbieters</span><span class="sxs-lookup"><span data-stu-id="4e7c9-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
