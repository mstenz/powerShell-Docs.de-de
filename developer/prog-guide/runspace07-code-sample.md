---
title: Codebeispiel RunSpace07 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857926"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="9fd5e-102">RunSpace07-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="9fd5e-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="9fd5e-103">Hier ist der Quellcode, für das Beispiel Runspace07 in beschrieben [erstellen eine Anwendung, fügt Konsolenbefehle zu einer Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="9fd5e-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="9fd5e-104">Diese beispielanwendung einen Runspace erstellt, wird eine Pipeline erstellt, fügt zwei Befehle an die Pipeline und führt dann die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="9fd5e-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="9fd5e-105">Die Befehle zur Pipeline hinzugefügte sind die `Get-Process` und `Measure-Object` Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9fd5e-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="9fd5e-106">Sie können die C# Quelldatei (runspace07.cs) mit dem Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="9fd5e-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9fd5e-107">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9fd5e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9fd5e-108">Sie können die C# Quelldatei (runspace07.cs) mit dem Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="9fd5e-108">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9fd5e-109">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="9fd5e-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9fd5e-110">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="9fd5e-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9fd5e-111">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="9fd5e-111">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="9fd5e-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9fd5e-112">See Also</span></span>

[<span data-ttu-id="9fd5e-113">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="9fd5e-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9fd5e-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9fd5e-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)