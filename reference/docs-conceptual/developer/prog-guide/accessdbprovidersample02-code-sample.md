---
title: AccessDbProviderSample02-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 122fc8ec4fc4388cca01f1a7e5014fa875506bb7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360529"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="70ca4-102">AccessDbProviderSample02-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="70ca4-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="70ca4-103">Der folgende Code zeigt die Implementierung des Windows PowerShell-Anbieters, der unter [Erstellen eines Windows PowerShell-Laufwerks Anbieters](./creating-a-windows-powershell-drive-provider.md)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="70ca4-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="70ca4-104">Diese Implementierung erstellt einen Pfad, stellt eine Verbindung mit einer Access-Datenbank her und entfernt dann das Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="70ca4-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="70ca4-105">Sie können die C# Quelldatei (AccessDBSampleProvider02.cs) für diesen Anbieter mithilfe der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen.</span><span class="sxs-lookup"><span data-stu-id="70ca4-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="70ca4-106">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="70ca4-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="70ca4-107">Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.</span><span class="sxs-lookup"><span data-stu-id="70ca4-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="70ca4-108">Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="70ca4-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="70ca4-109">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="70ca4-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="70ca4-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="70ca4-110">See Also</span></span>

[<span data-ttu-id="70ca4-111">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="70ca4-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="70ca4-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="70ca4-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
