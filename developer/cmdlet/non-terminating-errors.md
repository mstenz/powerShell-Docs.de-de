---
title: Nicht endenden Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054356"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="fcb61-102">Fehler ohne Abbruch</span><span class="sxs-lookup"><span data-stu-id="fcb61-102">Non-Terminating Errors</span></span>

<span data-ttu-id="fcb61-103">In diesem Thema wird erläutert, die Methode verwendet, um Fehler ohne Abbruch zu melden.</span><span class="sxs-lookup"><span data-stu-id="fcb61-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="fcb61-104">Es wird erläutert, wie die Methode aus, in dem-Cmdlet aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fcb61-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="fcb61-105">Tritt ein Fehler ohne Abbruch, das Cmdlet sollte melden Sie diesen Fehler durch Aufrufen der [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode.</span><span class="sxs-lookup"><span data-stu-id="fcb61-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="fcb61-106">Wenn das Cmdlet einen Fehler ohne Abbruch meldet, kann das Cmdlet funktioniert auf diesem Eingabeobjekt und weiteren eingehenden weiterhin pipeline Objekte.</span><span class="sxs-lookup"><span data-stu-id="fcb61-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="fcb61-107">Wenn Sie das Cmdlet Ruft die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode, schreibt das Cmdlet kann ein Error-Datensatzes, der die Bedingung beschreibt, die den Fehler ohne Abbruch verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="fcb61-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="fcb61-108">Weitere Informationen zu Datensätzen, finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="fcb61-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="fcb61-109">Cmdlets aufrufen können [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aus innerhalb ihrer eingabeverarbeitungsmethoden nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="fcb61-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="fcb61-110">Allerdings Cmdlets aufrufen können [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nur aus dem Thread, der Namen der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oder [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Geben Sie die Verarbeitungsmethode aus.</span><span class="sxs-lookup"><span data-stu-id="fcb61-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="fcb61-111">Rufen Sie keine [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aus einem anderen Thread.</span><span class="sxs-lookup"><span data-stu-id="fcb61-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="fcb61-112">Kommunizieren Sie stattdessen Fehlern zurück an den primären Thread.</span><span class="sxs-lookup"><span data-stu-id="fcb61-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb61-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fcb61-113">See Also</span></span>

[<span data-ttu-id="fcb61-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="fcb61-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="fcb61-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="fcb61-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="fcb61-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="fcb61-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="fcb61-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="fcb61-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="fcb61-118">Windows PowerShell-Error-Datensätze</span><span class="sxs-lookup"><span data-stu-id="fcb61-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="fcb61-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fcb61-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
