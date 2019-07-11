---
title: Runspace01 (C#) Codebeispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735052"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="040b9-102">Runspace01-Codebeispiel (C#)</span><span class="sxs-lookup"><span data-stu-id="040b9-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="040b9-103">Hier sind die Codebeispiele, für der Runspace beschrieben [erstellen eine Konsole Einzelanwendung eines angegebenen Befehls](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="040b9-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="040b9-104">Zu diesem Zweck die Anwendung einen Runspace aufruft, und ruft dann einen Befehl auf.</span><span class="sxs-lookup"><span data-stu-id="040b9-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="040b9-105">(Beachten Sie, dass diese Anwendung gibt keinen Runspace-Konfigurationsinformationen oder wird explizit eine Pipeline erstellt.)</span><span class="sxs-lookup"><span data-stu-id="040b9-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="040b9-106">Der Befehl, der aufgerufen wird, wird die `Get-Process` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="040b9-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="040b9-107">Sie können die C# Quelldatei (runspace01.cs) für diesen Runspace, mit dem Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="040b9-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="040b9-108">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="040b9-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="040b9-109">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="040b9-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="040b9-110">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="040b9-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="040b9-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="040b9-111">See Also</span></span>

[<span data-ttu-id="040b9-112">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="040b9-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="040b9-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="040b9-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)