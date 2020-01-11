---
title: RunSpace07-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: f40b24951c44c228d85524845045aea58f680f2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870607"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="54954-102">RunSpace07-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="54954-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="54954-103">Im folgenden finden Sie den Quellcode für das Runspace07-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, mit der einer Pipeline Befehle hinzugefügt](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)werden.</span><span class="sxs-lookup"><span data-stu-id="54954-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="54954-104">Diese Beispielanwendung erstellt einen Runspace, erstellt eine Pipeline, fügt der Pipeline zwei Befehle hinzu und führt dann die Pipeline aus.</span><span class="sxs-lookup"><span data-stu-id="54954-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="54954-105">Die Befehle, die der Pipeline hinzugefügt werden, sind die `Get-Process`-und `Measure-Object`-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="54954-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="54954-106">Sie können die C# Quelldatei (runspace07.cs) unter Verwendung der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen.</span><span class="sxs-lookup"><span data-stu-id="54954-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="54954-107">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="54954-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="54954-108">Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="54954-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="54954-109">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="54954-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="54954-110">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="54954-110">See Also</span></span>

[<span data-ttu-id="54954-111">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="54954-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="54954-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="54954-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
