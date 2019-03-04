---
title: GetProc04-Codebeispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855446"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="500f4-102">GetProc04-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="500f4-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="500f4-103">Hier sind die Codebeispiele für die GetProc04-Beispiel-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="500f4-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="500f4-104">Dies ist die `Get-Process` Cmdlet-Beispiel in beschriebenen [hinzufügen ohne Abbruch Fehlerberichterstattung an Ihr Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="500f4-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="500f4-105">Dies `Get-Process` Cmdlet Ruft die [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode auf, wenn eine ungültige Operation-Ausnahme, beim Abrufen der Prozessinformationen ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="500f4-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="500f4-106">Sie können die C# Quelldatei (getprov04.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="500f4-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="500f4-107">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="500f4-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="500f4-108">Sie können die C# Quelldatei (getprov04.cs) für dieses Get-Proc-Cmdlet mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten.</span><span class="sxs-lookup"><span data-stu-id="500f4-108">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="500f4-109">Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="500f4-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="500f4-110">Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="500f4-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="500f4-111">Vollständigen Beispielcode finden Sie unter den folgenden Themen.</span><span class="sxs-lookup"><span data-stu-id="500f4-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="500f4-112">Sprache</span><span class="sxs-lookup"><span data-stu-id="500f4-112">Language</span></span>|<span data-ttu-id="500f4-113">Thema</span><span class="sxs-lookup"><span data-stu-id="500f4-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="500f4-114">C#</span><span class="sxs-lookup"><span data-stu-id="500f4-114">C#</span></span>|[<span data-ttu-id="500f4-115">GetProc04 (C#)-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="500f4-115">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="500f4-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="500f4-116">VB.NET</span></span>|[<span data-ttu-id="500f4-117">GetProc04 Beispielcode (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="500f4-117">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="500f4-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="500f4-118">See Also</span></span>

[<span data-ttu-id="500f4-119">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="500f4-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="500f4-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="500f4-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)