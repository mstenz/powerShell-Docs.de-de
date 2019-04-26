---
title: GetProc04 (C#)-Codebeispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 936fb355be40b98136719ea929cf50b06705b687
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081630"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="90bce-102">GetProc04-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="90bce-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="90bce-103">Der folgende Code zeigt die Implementierung einer `Get-Process` Cmdlet, das meldet Fehler ohne Abbruch.</span><span class="sxs-lookup"><span data-stu-id="90bce-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="90bce-104">Diese Implementierung ruft die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode, um Bericht-Fehler ohne Abbruch.</span><span class="sxs-lookup"><span data-stu-id="90bce-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="90bce-105">Sie können die C# Quelldatei (getprov04.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="90bce-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="90bce-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="90bce-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="90bce-107">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="90bce-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="90bce-108">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="90bce-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="90bce-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="90bce-109">See Also</span></span>

[<span data-ttu-id="90bce-110">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="90bce-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="90bce-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="90bce-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)