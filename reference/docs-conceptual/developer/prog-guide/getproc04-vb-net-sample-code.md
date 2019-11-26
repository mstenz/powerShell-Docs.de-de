---
title: GetProc04 (VB.net)-Beispiel Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416092"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="dc314-102">GetProc04-Codebeispiel (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="dc314-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="dc314-103">Der folgende Code zeigt die Implementierung eines `Get-Process` Cmdlets, das nicht abschließende Fehler meldet.</span><span class="sxs-lookup"><span data-stu-id="dc314-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="dc314-104">Diese Implementierung ruft die [System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode auf, um nicht abschließende Fehler zu melden.</span><span class="sxs-lookup"><span data-stu-id="dc314-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="dc314-105">Sie können die C# Quelldatei (getprov04.cs) für dieses Get-proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten herunterladen.</span><span class="sxs-lookup"><span data-stu-id="dc314-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dc314-106">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="dc314-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="dc314-107">Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="dc314-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dc314-108">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="dc314-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="dc314-109">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dc314-109">See Also</span></span>

[<span data-ttu-id="dc314-110">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="dc314-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dc314-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dc314-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
