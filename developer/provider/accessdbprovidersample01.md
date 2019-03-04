---
title: AccessDBProviderSample01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854156"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="940f9-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="940f9-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="940f9-103">Dieses Beispiel zeigt, wie eine Anbieterklasse deklarieren, die direkt von abgeleitet ist die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="940f9-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="940f9-104">Wird hier nur aus Gründen der Vollständigkeit aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="940f9-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="940f9-105">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="940f9-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="940f9-106">Ihre Anbieterklasse wird wahrscheinlich von einem der folgenden Klassen abgeleitet werden und möglicherweise andere anbieterschnittstellen implementieren:</span><span class="sxs-lookup"><span data-stu-id="940f9-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="940f9-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="940f9-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="940f9-108">Finden Sie unter [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="940f9-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="940f9-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="940f9-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="940f9-110">Finden Sie unter [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="940f9-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="940f9-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="940f9-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="940f9-112">Finden Sie unter [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="940f9-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="940f9-113">Weitere Informationen zum auswählen die Anbieterklasse basierend auf Funktionen des Datenanbieters abgeleitet, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="940f9-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="940f9-114">Dieses Beispiel zeigt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="940f9-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="940f9-115">Deklarieren der `CmdletProvider` Attribut.</span><span class="sxs-lookup"><span data-stu-id="940f9-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="940f9-116">Definieren einer Klasse, die direkt von abgeleitet ist die [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Klasse.</span><span class="sxs-lookup"><span data-stu-id="940f9-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="940f9-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="940f9-117">Example</span></span>

<span data-ttu-id="940f9-118">Dieses Beispiel zeigt, wie eine Anbieterklasse definiert und deklariert die `CmdletProvider` Attribut.</span><span class="sxs-lookup"><span data-stu-id="940f9-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="940f9-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="940f9-119">See Also</span></span>

[<span data-ttu-id="940f9-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="940f9-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="940f9-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="940f9-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="940f9-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="940f9-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="940f9-123">Entwerfen Ihre Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="940f9-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)