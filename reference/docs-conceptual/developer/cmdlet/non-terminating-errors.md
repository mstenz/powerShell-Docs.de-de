---
title: Fehler ohne Abbruch | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369599"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="2711d-102">Fehler ohne Abbruch</span><span class="sxs-lookup"><span data-stu-id="2711d-102">Non-Terminating Errors</span></span>

<span data-ttu-id="2711d-103">In diesem Thema wird die Methode erläutert, die zum Melden von Fehlern ohne Abbruch verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2711d-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="2711d-104">Außerdem wird erläutert, wie die-Methode innerhalb des Cmdlets aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="2711d-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="2711d-105">Wenn ein Fehler ohne Abbruch auftritt, sollte das Cmdlet diesen Fehler durch Aufrufen der [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode melden.</span><span class="sxs-lookup"><span data-stu-id="2711d-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="2711d-106">Wenn das Cmdlet einen Fehler ohne Abbruch meldet, kann das Cmdlet weiterhin auf diesem Eingabe Objekt und auf weiteren eingehenden Pipeline Objekten arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2711d-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="2711d-107">Wenn das Cmdlet die [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode aufruft, kann das Cmdlet einen Fehler Daten Satz schreiben, der die Bedingung beschreibt, die den Fehler ohne Abbruch ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="2711d-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="2711d-108">Weitere Informationen zu Fehler Datensätzen finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="2711d-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="2711d-109">Cmdlets können [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nach Bedarf in ihren Eingabe Verarbeitungsmethoden aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2711d-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="2711d-110">Cmdlets können jedoch [System. Management. Automation. Cmdlet. Write error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nur aus dem Thread aufrufen, der " [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)", " [System. Management. Automation. Cmdlet. ProcessRecord" aufgerufen hat. ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oder [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Eingabe Verarbeitungsmethode.</span><span class="sxs-lookup"><span data-stu-id="2711d-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="2711d-111">" [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) " kann nicht von einem anderen Thread aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2711d-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="2711d-112">Stattdessen werden Fehler an den Haupt Thread übermittelt.</span><span class="sxs-lookup"><span data-stu-id="2711d-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="2711d-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2711d-113">See Also</span></span>

[<span data-ttu-id="2711d-114">System. Management. Automation. Cmdlet. Write error</span><span class="sxs-lookup"><span data-stu-id="2711d-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="2711d-115">System. Management. Automation. Cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="2711d-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="2711d-116">System. Management. Automation. Cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="2711d-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="2711d-117">System. Management. Automation. Cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="2711d-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="2711d-118">Windows PowerShell-Fehler Datensätze</span><span class="sxs-lookup"><span data-stu-id="2711d-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="2711d-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="2711d-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
