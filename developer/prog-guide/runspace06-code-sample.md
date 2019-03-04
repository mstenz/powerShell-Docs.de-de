---
title: Codebeispiel RunSpace06 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: 2874f9df3f5166fbe14deb5b128674540c0d6701
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854036"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="1d7df-102">RunSpace06-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1d7df-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="1d7df-103">Hier ist der Quellcode, für das Beispiel Runspace06 in beschrieben [konfigurieren einen Runspace ein Windows PowerShell-Snap-in mit](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="1d7df-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="1d7df-104">Diese beispielanwendung erstellt einen Runspace basierend auf einer Windows PowerShell-Snap-in, die dann zum Ausführen einer Pipeline mit einem einzigen Befehl verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d7df-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="1d7df-105">Zu diesem Zweck die Anwendung die Konfigurationsinformationen des Runspace erstellt, einen Runspace erstellt, erstellt eine Pipeline mit einem einzigen Befehl und führt dann die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="1d7df-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="1d7df-106">Sie können die C# Quelldatei (runspace06.cs) mithilfe des Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="1d7df-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1d7df-107">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1d7df-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="1d7df-108">Sie können die C# Quelldatei (runspace06.cs) mithilfe des Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="1d7df-108">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1d7df-109">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1d7df-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1d7df-110">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="1d7df-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1d7df-111">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1d7df-111">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="1d7df-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1d7df-112">See Also</span></span>

[<span data-ttu-id="1d7df-113">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="1d7df-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1d7df-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1d7df-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)