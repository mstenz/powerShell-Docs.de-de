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
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853776"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="e6be7-102">Fehler ohne Abbruch</span><span class="sxs-lookup"><span data-stu-id="e6be7-102">Non-Terminating Errors</span></span>

<span data-ttu-id="e6be7-103">In diesem Thema wird erläutert, die Methode verwendet, um Fehler ohne Abbruch zu melden.</span><span class="sxs-lookup"><span data-stu-id="e6be7-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="e6be7-104">Es wird erläutert, wie die Methode aus, in dem-Cmdlet aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e6be7-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="e6be7-105">Tritt ein Fehler ohne Abbruch, das Cmdlet sollte melden Sie diesen Fehler durch Aufrufen der [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode.</span><span class="sxs-lookup"><span data-stu-id="e6be7-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="e6be7-106">Wenn das Cmdlet einen Fehler ohne Abbruch meldet, kann das Cmdlet funktioniert auf diesem Eingabeobjekt und weiteren eingehenden weiterhin pipeline Objekte.</span><span class="sxs-lookup"><span data-stu-id="e6be7-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="e6be7-107">Wenn Sie das Cmdlet Ruft die [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode, schreibt das Cmdlet kann ein Error-Datensatzes, der die Bedingung beschreibt, die den Fehler ohne Abbruch verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="e6be7-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="e6be7-108">Weitere Informationen zu Datensätzen, finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="e6be7-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="e6be7-109">Cmdlets aufrufen können [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aus innerhalb ihrer eingabeverarbeitungsmethoden nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="e6be7-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="e6be7-110">Allerdings Cmdlets aufrufen können [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) nur aus dem Thread, der Namen der [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oder [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Geben Sie die Verarbeitungsmethode aus.</span><span class="sxs-lookup"><span data-stu-id="e6be7-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="e6be7-111">Rufen Sie keine [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aus einem anderen Thread.</span><span class="sxs-lookup"><span data-stu-id="e6be7-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="e6be7-112">Kommunizieren Sie stattdessen Fehlern zurück an den primären Thread.</span><span class="sxs-lookup"><span data-stu-id="e6be7-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6be7-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e6be7-113">See Also</span></span>

[<span data-ttu-id="e6be7-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="e6be7-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="e6be7-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="e6be7-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="e6be7-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="e6be7-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="e6be7-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="e6be7-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="e6be7-118">Windows PowerShell-Error-Datensätze</span><span class="sxs-lookup"><span data-stu-id="e6be7-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="e6be7-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e6be7-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
