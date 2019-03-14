---
title: Codebeispiel AccessDbProviderSample06 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795605"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="69b38-102">AccessDbProviderSample06-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="69b38-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="69b38-103">Der folgende Code zeigt die Implementierung des Windows PowerShell-Inhaltsanbieter, die in beschriebenen [erstellen eine Windows PowerShell-Inhaltsanbieter](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="69b38-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="69b38-104">Dieser Anbieter ermöglicht es den Benutzer den Inhalt der Elemente in einem Datenspeicher bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="69b38-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="69b38-105">Sie können die C# Quelldatei (AccessDBSampleProvider06.cs) für diesen Anbieter unter Verwendung des Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="69b38-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="69b38-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="69b38-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="69b38-107">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="69b38-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="69b38-108">Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="69b38-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="69b38-109">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="69b38-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="69b38-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="69b38-110">See Also</span></span>

[<span data-ttu-id="69b38-111">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="69b38-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="69b38-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="69b38-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)