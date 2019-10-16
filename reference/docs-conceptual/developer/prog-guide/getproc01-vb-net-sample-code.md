---
title: GetProc01 (VB.net)-Beispiel Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360439"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="184ef-102">GetProc01-Codebeispiel (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="184ef-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="184ef-103">Der folgende Code zeigt die Implementierung des GetProc01-Beispiel-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="184ef-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="184ef-104">Beachten Sie, dass das Cmdlet vereinfacht wird, indem Sie die tatsächliche Prozess Abruf Funktion an die [System. Diagnostics. Process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) -Methode überlassen.</span><span class="sxs-lookup"><span data-stu-id="184ef-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="184ef-105">Sie können die C# Quelldatei (getproc01.cs) für dieses Get-proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten herunterladen.</span><span class="sxs-lookup"><span data-stu-id="184ef-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="184ef-106">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="184ef-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="184ef-107">Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.</span><span class="sxs-lookup"><span data-stu-id="184ef-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="184ef-108">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="184ef-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="184ef-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="184ef-109">See Also</span></span>

[<span data-ttu-id="184ef-110">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="184ef-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="184ef-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="184ef-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)