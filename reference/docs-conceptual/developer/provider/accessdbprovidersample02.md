---
title: AccessDBProviderSample02 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: 219f8c2367939d16da928ede789843669b4451c6
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633412"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="f7d5c-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="f7d5c-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="f7d5c-103">In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) überschrieben werden, um Aufrufe der `New-PSDrive` -und- `Remove-PSDrive` Cmdlets zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="f7d5c-104">Die Anbieter Klasse in diesem Beispiel wird von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f7d5c-105">Zeigt</span><span class="sxs-lookup"><span data-stu-id="f7d5c-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7d5c-106">Ihre Anbieter Klasse wird wahrscheinlich von einer der folgenden Klassen abgeleitet und kann möglicherweise andere Anbieter Schnittstellen implementieren:</span><span class="sxs-lookup"><span data-stu-id="f7d5c-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="f7d5c-107">[System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="f7d5c-108">Siehe [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="f7d5c-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="f7d5c-109">[System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="f7d5c-110">Siehe [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="f7d5c-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="f7d5c-111">[System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="f7d5c-112">Siehe [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="f7d5c-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="f7d5c-113">Weitere Informationen zum Auswählen der Anbieter Klasse, von der basierend auf den Anbieter Features abgeleitet werden soll, finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7d5c-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="f7d5c-114">Dieses Beispiel zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f7d5c-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f7d5c-115">Deklarieren des `CmdletProvider` Attributs.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="f7d5c-116">Definieren einer Anbieter Klasse, die von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse Laufwerks gesteuert wird.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="f7d5c-117">Überschreiben der [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) -Methode, um das Erstellen neuer Laufwerke zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="f7d5c-118">(Dieses Beispiel zeigt nicht, wie dem Cmdlet dynamische Parameter hinzugefügt werden `New-PSDrive` .)</span><span class="sxs-lookup"><span data-stu-id="f7d5c-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="f7d5c-119">Überschreiben der [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) -Methode, um das Entfernen vorhandener Laufwerke zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="f7d5c-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f7d5c-120">Example</span></span>

<span data-ttu-id="f7d5c-121">In diesem Beispiel wird gezeigt, wie die Methoden [System. Management. Automation. Provider. drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) und [System. Management. Automation. Provider. drivecmdletprovider. removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="f7d5c-122">Bei diesem Beispiel Anbieter werden bei der Erstellung eines Laufwerks die Verbindungsinformationen in einem- `AccessDBPsDriveInfo` Objekt gespeichert.</span><span class="sxs-lookup"><span data-stu-id="f7d5c-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="f7d5c-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f7d5c-123">See Also</span></span>

[<span data-ttu-id="f7d5c-124">System. Management. Automation. Provider. itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f7d5c-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="f7d5c-125">System. Management. Automation. Provider. containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f7d5c-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="f7d5c-126">System. Management. Automation. Provider. navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f7d5c-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="f7d5c-127">Entwerfen eines Windows PowerShell-Anbieters</span><span class="sxs-lookup"><span data-stu-id="f7d5c-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
