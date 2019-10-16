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
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360299"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="ac854-102">GetProc04-Codebeispiel (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="ac854-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="ac854-103">Der folgende Code zeigt die Implementierung eines `Get-Process`-Cmdlets, das nicht abschließende Fehler meldet.</span><span class="sxs-lookup"><span data-stu-id="ac854-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="ac854-104">Diese Implementierung ruft die [System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode auf, um nicht abschließende Fehler zu melden.</span><span class="sxs-lookup"><span data-stu-id="ac854-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="ac854-105">Sie können die C# Quelldatei (getprov04.cs) für dieses Get-proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten herunterladen.</span><span class="sxs-lookup"><span data-stu-id="ac854-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ac854-106">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="ac854-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ac854-107">Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ac854-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ac854-108">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="ac854-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="ac854-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ac854-109">See Also</span></span>

[<span data-ttu-id="ac854-110">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="ac854-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ac854-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ac854-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)