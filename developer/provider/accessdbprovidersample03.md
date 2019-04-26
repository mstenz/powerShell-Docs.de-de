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
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081069"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="33c92-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="33c92-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="33c92-103">Dieses Beispiel zeigt, wie die [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) und [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methoden zum Aufrufen von unterstützen die `Get-Item` und `Set-Item` Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="33c92-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="33c92-104">Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="33c92-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="33c92-105">Zeigt</span><span class="sxs-lookup"><span data-stu-id="33c92-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33c92-106">Ihre Anbieterklasse wird wahrscheinlich von einem der folgenden Klassen abgeleitet werden und möglicherweise andere anbieterschnittstellen implementieren:</span><span class="sxs-lookup"><span data-stu-id="33c92-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="33c92-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="33c92-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="33c92-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="33c92-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="33c92-109">Finden Sie unter [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="33c92-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="33c92-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="33c92-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="33c92-111">Finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="33c92-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="33c92-112">Weitere Informationen zum auswählen die Anbieterklasse basierend auf Funktionen des Datenanbieters abgeleitet, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="33c92-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="33c92-113">Dieses Beispiel zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="33c92-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="33c92-114">Deklarieren der `CmdletProvider` Attribut.</span><span class="sxs-lookup"><span data-stu-id="33c92-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="33c92-115">Definieren eine abgeleitete Anbieterklasse die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="33c92-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="33c92-116">Überschreiben der [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode zum Ändern des Verhaltens von der `New-PSDrive` -Cmdlet, sodass des Benutzers neue Datenträger erstellen.</span><span class="sxs-lookup"><span data-stu-id="33c92-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="33c92-117">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `New-PSDrive` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="33c92-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="33c92-118">Überschreiben der [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode zum Entfernen der vorhandenen Laufwerke zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="33c92-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="33c92-119">Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Methode zum Ändern des Verhaltens von der `Get-Item` -Cmdlet, sodass der Benutzer Elemente aus dem Datenspeicher abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="33c92-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="33c92-120">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Get-Item` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="33c92-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="33c92-121">Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Methode zum Ändern des Verhaltens von der `Set-Item` -Cmdlet, sodass der Benutzer zum Aktualisieren der Elemente im Datenspeicher.</span><span class="sxs-lookup"><span data-stu-id="33c92-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="33c92-122">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Get-Item` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="33c92-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="33c92-123">Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) Methode zum Ändern des Verhaltens von der `Test-Path` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33c92-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="33c92-124">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Test-Path` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="33c92-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="33c92-125">Überschreiben der [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) Methode, um zu bestimmen, ob der angegebene Pfad gültig ist.</span><span class="sxs-lookup"><span data-stu-id="33c92-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="33c92-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="33c92-126">Example</span></span>

<span data-ttu-id="33c92-127">Dieses Beispiel zeigt, wie die Methoden zum Abrufen und Festlegen von Elementen in einer Microsoft Access-Basis erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33c92-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="33c92-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="33c92-128">See Also</span></span>

[<span data-ttu-id="33c92-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="33c92-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="33c92-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="33c92-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="33c92-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="33c92-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="33c92-132">Entwerfen Ihre Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="33c92-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)