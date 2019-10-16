---
title: AccessDbProviderSample04-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366969"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="51cb0-102">AccessDbProviderSample04-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="51cb0-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="51cb0-103">Der folgende Code zeigt die Implementierung des Windows PowerShell-Anbieters, der unter [Erstellen eines Windows PowerShell-Container Anbieters](./creating-a-windows-powershell-container-provider.md)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="51cb0-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="51cb0-104">Dieser Anbieter funktioniert in Daten speichern mit mehreren Ebenen.</span><span class="sxs-lookup"><span data-stu-id="51cb0-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="51cb0-105">Bei dieser Art von Datenspeicher enthält die oberste Ebene des Stores die Stamm Elemente, und jede nachfolgende Ebene wird als Knoten untergeordneter Elemente bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="51cb0-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="51cb0-106">Da der Benutzer an diesen untergeordneten Knoten arbeiten kann, kann er hierarchisch über den Datenspeicher interagieren.</span><span class="sxs-lookup"><span data-stu-id="51cb0-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="51cb0-107">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="51cb0-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="51cb0-108">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="51cb0-108">See Also</span></span>

[<span data-ttu-id="51cb0-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="51cb0-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
