---
title: RunSpace05-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: a99d0cc0dd35ae4c1a52e3624a9dd5af2a26c97a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360139"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="1740e-102">RunSpace05-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1740e-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="1740e-103">Im folgenden finden Sie den Quellcode für das Runspace05-Beispiel, das unter [Konfigurieren eines Runspace mithilfe von runspaceconfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="1740e-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="1740e-104">Dieses Beispiel zeigt, wie Sie die Runspace-Konfigurationsinformationen erstellen, einen Runspace erstellen, eine Pipeline mit einem einzelnen Befehl erstellen und dann die Pipeline ausführen.</span><span class="sxs-lookup"><span data-stu-id="1740e-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="1740e-105">Der Befehl, der ausgeführt wird, ist das Cmdlet "`Get-Process`".</span><span class="sxs-lookup"><span data-stu-id="1740e-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="1740e-106">Sie können die C# Quelldatei (runspace05.cs) unter Verwendung der Laufzeitkomponenten Microsoft Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0 herunterladen.</span><span class="sxs-lookup"><span data-stu-id="1740e-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1740e-107">Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1740e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1740e-108">Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1740e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1740e-109">Code Beispiel</span><span class="sxs-lookup"><span data-stu-id="1740e-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="1740e-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1740e-110">See Also</span></span>

[<span data-ttu-id="1740e-111">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="1740e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1740e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1740e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
