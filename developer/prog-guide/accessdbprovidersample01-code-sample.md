---
title: Codebeispiel AccessDbProviderSample01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859666"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="687f2-102">AccessDbProviderSample01-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="687f2-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="687f2-103">Der folgende Code zeigt die Implementierung der Windows PowerShell-Anbieter, die in beschriebenen [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="687f2-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="687f2-104">Diese Implementierung bietet Methoden zum Starten und beenden den Anbieter aus, und obwohl es eine Möglichkeit, auf einen Datenspeicher oder zum Abrufen oder Festlegen von Daten im Datenspeicher nicht bietet, bietet es die grundlegende Funktionalität, die von allen Anbietern erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="687f2-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="687f2-105">Sie können die C# Quelldatei (AccessDBSampleProvider01.cs) für diesen Anbieter unter Verwendung des Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="687f2-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="687f2-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="687f2-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="687f2-107">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="687f2-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="687f2-108">Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="687f2-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="687f2-109">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="687f2-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="687f2-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="687f2-110">See Also</span></span>

[<span data-ttu-id="687f2-111">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="687f2-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="687f2-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="687f2-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)