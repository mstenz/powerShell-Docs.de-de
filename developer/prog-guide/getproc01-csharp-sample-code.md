---
title: GetProc01 (C#)-Codebeispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 56ce7080e24cc12de6d43ac607ffd5d3f0a3b17c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856886"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="889d1-102">GetProc01-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="889d1-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="889d1-103">Der folgende Code zeigt die Implementierung des GetProc01-Beispiel-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="889d1-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="889d1-104">Beachten Sie, dass das Cmdlet vereinfacht ist, indem Sie die eigentliche Arbeit des Abrufens der Prozess zum Verlassen der [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) Methode.</span><span class="sxs-lookup"><span data-stu-id="889d1-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="889d1-105">Sie können die C# Quelldatei (getproc01.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="889d1-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="889d1-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="889d1-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="889d1-107">Sie können die C# Quelldatei (getproc01.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="889d1-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="889d1-108">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="889d1-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="889d1-109">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="889d1-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="889d1-110">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="889d1-110">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="889d1-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="889d1-111">See Also</span></span>

[<span data-ttu-id="889d1-112">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="889d1-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="889d1-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="889d1-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)