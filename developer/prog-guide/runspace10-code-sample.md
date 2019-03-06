---
title: Codebeispiel RunSpace10 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429583"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="3850a-102">RunSpace10-Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3850a-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="3850a-103">Hier ist der Quellcode für das Beispiel Runspace10.</span><span class="sxs-lookup"><span data-stu-id="3850a-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="3850a-104">Diese beispielanwendung Fügt ein Cmdlet zum [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) und verwendet dann die geänderte Konfigurationsinformationen zum Erstellen des Runspaces.</span><span class="sxs-lookup"><span data-stu-id="3850a-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="3850a-105">Sie können die C# Quelldatei (runspace10.cs) mithilfe des Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="3850a-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3850a-106">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="3850a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3850a-107">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="3850a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3850a-108">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3850a-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="3850a-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3850a-109">See Also</span></span>

[<span data-ttu-id="3850a-110">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="3850a-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3850a-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3850a-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)