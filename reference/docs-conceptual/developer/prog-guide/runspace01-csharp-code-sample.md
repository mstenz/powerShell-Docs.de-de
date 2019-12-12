---
title: Runspace01 (C#)-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 607113ed566fc1e08e5b1d7092c83da2a22366ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74418023"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="7edca-102">Runspace01-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="7edca-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="7edca-103">Im folgenden finden Sie die Codebeispiele für den Runspace [, der unter Erstellen einer Konsolenanwendung beschrieben wird, die einen angegebenen Befehl ausführt](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="7edca-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="7edca-104">Hierzu ruft die Anwendung einen Runspace auf und ruft dann einen Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="7edca-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="7edca-105">(Beachten Sie, dass diese Anwendung keine Informationen zur Runspace-Konfiguration angibt und keine Pipeline explizit erstellt).</span><span class="sxs-lookup"><span data-stu-id="7edca-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="7edca-106">Der Befehl, der aufgerufen wird, ist das Cmdlet "`Get-Process`".</span><span class="sxs-lookup"><span data-stu-id="7edca-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="7edca-107">Sie können die C# Quelldatei (runspace01.cs) für diesen Runspace mithilfe der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen.</span><span class="sxs-lookup"><span data-stu-id="7edca-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7edca-108">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7edca-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7edca-109">Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="7edca-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7edca-110">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="7edca-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="7edca-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7edca-111">See Also</span></span>

[<span data-ttu-id="7edca-112">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="7edca-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7edca-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7edca-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
