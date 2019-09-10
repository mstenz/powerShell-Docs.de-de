---
title: RunSpace03 (C#)-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848027"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="2e427-102">Runspace03-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="2e427-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="2e427-103">Im folgenden finden C# Sie den Quellcode für die Konsolenanwendung, die unter "Erstellen einer Konsolenanwendung, die ein bestimmtes Skript ausführt" beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="2e427-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="2e427-104">In diesem Beispiel wird die [System. Management. Automation. runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) -Klasse verwendet, um ein Skript auszuführen, das Prozessinformationen mithilfe der Liste der Prozessnamen abruft, die an das Skript übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="2e427-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="2e427-105">Es zeigt, wie Eingabe Objekte an ein Skript übergeben werden und wie Fehler Objekte sowie die Ausgabe Objekte abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2e427-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="2e427-106">Sie können die C# Quelldatei (runspace03.cs) für dieses Beispiel mithilfe der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen.</span><span class="sxs-lookup"><span data-stu-id="2e427-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2e427-107">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2e427-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2e427-108">Die heruntergeladenen Quelldateien sind im > Verzeichnis für  **\<PowerShell-Beispiele** verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2e427-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2e427-109">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="2e427-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="2e427-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2e427-110">See Also</span></span>

[<span data-ttu-id="2e427-111">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="2e427-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2e427-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2e427-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)