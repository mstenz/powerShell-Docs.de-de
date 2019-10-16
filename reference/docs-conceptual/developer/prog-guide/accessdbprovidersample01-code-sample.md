---
title: AccessDbProviderSample01-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 429339a86b44bfa53302329fe1e21f6f91c52b42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360549"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="0ece6-102">AccessDbProviderSample01-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="0ece6-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="0ece6-103">Der folgende Code zeigt die Implementierung des Windows PowerShell-Anbieters, der unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="0ece6-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="0ece6-104">Diese Implementierung stellt Methoden zum Starten und Beenden des Anbieters bereit und stellt zwar keine Mittel für den Zugriff auf einen Datenspeicher oder zum Abrufen oder Festlegen der Daten im Datenspeicher bereit, bietet jedoch die Grundfunktionen, die von allen Anbietern benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="0ece6-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="0ece6-105">Sie können die C# Quelldatei (AccessDBSampleProvider01.cs) für diesen Anbieter herunterladen, indem Sie das Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0-Laufzeitkomponenten verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ece6-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0ece6-106">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0ece6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0ece6-107">Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0ece6-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="0ece6-108">Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0ece6-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="0ece6-109">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="0ece6-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="0ece6-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0ece6-110">See Also</span></span>

[<span data-ttu-id="0ece6-111">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="0ece6-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0ece6-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0ece6-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
