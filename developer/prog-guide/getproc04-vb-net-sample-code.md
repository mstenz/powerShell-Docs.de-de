---
title: GetProc04 Beispielcode (VB.NET) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 0d0d1a3f82bc2cee025139d69fee02eb601fa563
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055460"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="6b074-102">GetProc04-Codebeispiel (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6b074-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="6b074-103">Der folgende Code zeigt die Implementierung einer `Get-Process` Cmdlet, das meldet Fehler ohne Abbruch.</span><span class="sxs-lookup"><span data-stu-id="6b074-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="6b074-104">Diese Implementierung ruft die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode, um Bericht-Fehler ohne Abbruch.</span><span class="sxs-lookup"><span data-stu-id="6b074-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="6b074-105">Sie können die C# Quelldatei (getprov04.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="6b074-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6b074-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6b074-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6b074-107">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="6b074-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6b074-108">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="6b074-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="6b074-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6b074-109">See Also</span></span>

[<span data-ttu-id="6b074-110">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="6b074-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6b074-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6b074-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)