---
title: AccessDBProviderSample06 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055545"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="755af-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="755af-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="755af-103">Dieses Beispiel zeigt, wie inhaltsmethoden um Aufrufe unterstützen die `Clear-Content`, `Get-Content`, und `Set-Content` Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="755af-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="755af-104">Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss.</span><span class="sxs-lookup"><span data-stu-id="755af-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="755af-105">Die Anbieterklasse in diesem Beispiel ist abgeleitet von der [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse und implementiert die [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="755af-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="755af-106">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="755af-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="755af-107">Ihre Anbieterklasse wird wahrscheinlich von einem der folgenden Klassen abgeleitet werden und möglicherweise andere anbieterschnittstellen implementieren:</span><span class="sxs-lookup"><span data-stu-id="755af-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="755af-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="755af-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="755af-109">Finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="755af-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="755af-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="755af-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="755af-111">Finden Sie unter [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="755af-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="755af-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="755af-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="755af-113">Weitere Informationen zum auswählen die Anbieterklasse basierend auf Funktionen des Datenanbieters abgeleitet, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="755af-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="755af-114">Dieses Beispiel zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="755af-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="755af-115">Deklarieren der `CmdletProvider` Attribut.</span><span class="sxs-lookup"><span data-stu-id="755af-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="755af-116">Definieren eine abgeleitete Anbieterklasse die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) darstellt und deklariert die [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="755af-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="755af-117">Überschreiben der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methode zum Ändern des Verhaltens von der `Clear-Content` -Cmdlet, damit der Benutzer den Inhalt von einem Element zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="755af-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="755af-118">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Clear-Content` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="755af-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="755af-119">Überschreiben der [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) Methode zum Ändern des Verhaltens von der `Get-Content` -Cmdlet, sodass der Benutzer zum Abrufen des Inhalts eines Elements.</span><span class="sxs-lookup"><span data-stu-id="755af-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="755af-120">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Get-Content` Cmdlet.).</span><span class="sxs-lookup"><span data-stu-id="755af-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="755af-121">Überschreiben der [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) Methode zum Ändern des Verhaltens von der `Set-Content` -Cmdlet, damit der Benutzer den Inhalt eines Elements aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="755af-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="755af-122">(Dieses Beispiel zeigt keine dynamischen Parameter zum Hinzufügen der `Set-Content` Cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="755af-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="755af-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="755af-123">Example</span></span>

<span data-ttu-id="755af-124">Dieses Beispiel zeigt, wie die Methoden zum deaktivieren, erhalten, und legen Sie den Inhalt von Elementen in einer Microsoft Access Basis erforderlich.</span><span class="sxs-lookup"><span data-stu-id="755af-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="755af-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="755af-125">See Also</span></span>

[<span data-ttu-id="755af-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="755af-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="755af-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="755af-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="755af-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="755af-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="755af-129">Entwerfen Ihre Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="755af-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)