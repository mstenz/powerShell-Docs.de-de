---
title: Codebeispiel AccessDbProviderSample02 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795486"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="947b9-102">AccessDbProviderSample02-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="947b9-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="947b9-103">Der folgende Code zeigt die Implementierung der Windows PowerShell-Anbieter, die in beschriebenen [erstellen ein Windows PowerShell-Laufwerk-Anbieter](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="947b9-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="947b9-104">Diese Implementierung erstellt einen Pfad, stellt eine Verbindung mit einer Access-Datenbank und entfernt dann das Laufwerk.</span><span class="sxs-lookup"><span data-stu-id="947b9-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="947b9-105">Sie können die C# Quelldatei (AccessDBSampleProvider02.cs) für diesen Anbieter, die mit dem Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="947b9-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="947b9-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="947b9-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="947b9-107">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="947b9-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="947b9-108">Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="947b9-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="947b9-109">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="947b9-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="947b9-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="947b9-110">See Also</span></span>

[<span data-ttu-id="947b9-111">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="947b9-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="947b9-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="947b9-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)