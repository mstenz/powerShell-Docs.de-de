---
title: AccessDBProviderSample04 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057619"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="fbe70-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="fbe70-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="fbe70-103">Dieses Beispiel zeigt, wie containermethoden um Aufrufe unterstützen die `Copy-Item`, `Get-ChildItem`, `New-Item`, und `Remove-Item` Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fbe70-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="fbe70-104">Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind.</span><span class="sxs-lookup"><span data-stu-id="fbe70-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="fbe70-105">Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element.</span><span class="sxs-lookup"><span data-stu-id="fbe70-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="fbe70-106">Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="fbe70-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fbe70-107">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="fbe70-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbe70-108">Die Anbieterklasse in den meisten Fällen von abgeleitet der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="fbe70-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="fbe70-109">Dieses Beispiel zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="fbe70-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="fbe70-110">Deklarieren der `CmdletProvider` Attribut.</span><span class="sxs-lookup"><span data-stu-id="fbe70-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="fbe70-111">Definieren eine abgeleitete Anbieterklasse die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="fbe70-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="fbe70-112">Überschreiben der [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) Methode zum Ändern des Verhaltens von der `Copy-Item` Cmdlet, das dem Benutzer ermöglicht, Elemente aus einem Speicherort in einen anderen zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="fbe70-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="fbe70-113">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Copy-Item` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="fbe70-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="fbe70-114">Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) Methode, um das Verhalten des Cmdlets Get-ChildItems ändern, in denen dem Benutzer ermöglicht, die die untergeordneten Elemente des übergeordneten Elements abrufen. .</span><span class="sxs-lookup"><span data-stu-id="fbe70-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="fbe70-115">(Dieses Beispiel zeigt keine dynamischen Parameter an das Cmdlet Get-ChildItems hinzufügen.)</span><span class="sxs-lookup"><span data-stu-id="fbe70-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="fbe70-116">Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) Methode, um das Verhalten des Cmdlets Get-ChildItems ändern bei der `Name` -Parameter des Cmdlets angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="fbe70-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="fbe70-117">Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Methode zum Ändern des Verhaltens von der `New-Item` -Cmdlet, das dem Benutzer ermöglicht, Elemente mit dem Datenspeicher hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="fbe70-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="fbe70-118">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `New-Item` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="fbe70-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="fbe70-119">Überschreiben der [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) Methode zum Ändern des Verhaltens von der `Remove-Item` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbe70-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="fbe70-120">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Remove-Item` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="fbe70-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="fbe70-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fbe70-121">Example</span></span>

<span data-ttu-id="fbe70-122">Dieses Beispiel zeigt, wie die Methoden zum Kopieren, erstellen und Entfernen von Elementen sowie Methoden zum Abrufen der untergeordneten Elemente eines übergeordneten Elements benötigt.</span><span class="sxs-lookup"><span data-stu-id="fbe70-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="fbe70-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fbe70-123">See Also</span></span>

[<span data-ttu-id="fbe70-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fbe70-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="fbe70-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fbe70-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="fbe70-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="fbe70-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="fbe70-127">Entwerfen Ihre Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="fbe70-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)