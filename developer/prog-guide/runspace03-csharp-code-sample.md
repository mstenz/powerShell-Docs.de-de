---
title: RunSpace03 (C#) Codebeispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081375"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="31cbc-102">Runspace03-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="31cbc-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="31cbc-103">Hier ist die C# Quellcode für die Konsolenanwendung, die in beschriebenen [erstellen eine Konsole-Anwendungsausführung an, dass ein Skript angegeben](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="31cbc-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="31cbc-104">Dieses Beispiel verwendet die [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) Klasse, um ein Skript ausführen, die Ruft Informationen verarbeiten, indem Sie die Liste der Prozessnamen in das Skript übergeben.</span><span class="sxs-lookup"><span data-stu-id="31cbc-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="31cbc-105">Es zeigt, wie Eingabeobjekte an ein Skript zu übergeben und Error-Objekte als auch für Ausgabeobjekte abrufen.</span><span class="sxs-lookup"><span data-stu-id="31cbc-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="31cbc-106">Sie können die C# Quelldatei (runspace03.cs) für dieses Beispiel unter Verwendung des Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="31cbc-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="31cbc-107">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="31cbc-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="31cbc-108">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="31cbc-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="31cbc-109">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="31cbc-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="31cbc-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="31cbc-110">See Also</span></span>

[<span data-ttu-id="31cbc-111">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="31cbc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="31cbc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="31cbc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)