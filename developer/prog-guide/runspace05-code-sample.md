---
title: Codebeispiel RunSpace05 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 2b5ac097e8a52832b0f8cfb93b84eef56fc64858
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854596"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="e5b66-102">RunSpace05-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="e5b66-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="e5b66-103">Hier ist der Quellcode für das Runspace05-Beispiel, das beschrieben ist [konfigurieren einen Runspace mithilfe RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="e5b66-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="e5b66-104">Dieses Beispiel zeigt, wie Sie die Konfigurationsinformationen des Runspace erstellen, einen Runspace erstellen, erstellen Sie eine Pipeline mit einem einzigen Befehl und führen Sie dann auf die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="e5b66-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="e5b66-105">Der Befehl, der ausgeführt wird, wird die `Get-Process` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e5b66-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e5b66-106">Sie können die C# Quelldatei (runspace05.cs) mithilfe des Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="e5b66-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e5b66-107">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e5b66-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e5b66-108">Sie können die C# Quelldatei (runspace05.cs) mithilfe des Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="e5b66-108">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e5b66-109">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="e5b66-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e5b66-110">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="e5b66-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e5b66-111">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="e5b66-111">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="e5b66-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5b66-112">See Also</span></span>

[<span data-ttu-id="e5b66-113">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="e5b66-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e5b66-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e5b66-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)