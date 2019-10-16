---
title: Konzepte für die Fehlerberichterstattung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364619"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="06e7a-102">Konzepte der Fehlerberichterstattung</span><span class="sxs-lookup"><span data-stu-id="06e7a-102">Error Reporting Concepts</span></span>

<span data-ttu-id="06e7a-103">Windows PowerShell bietet zwei Mechanismen zum Melden von Fehlern: einen Mechanismus zum *Beenden von Fehlern* und einen anderen Mechanismus für *Fehler ohne*Abbruch.</span><span class="sxs-lookup"><span data-stu-id="06e7a-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="06e7a-104">Es ist wichtig, dass das Cmdlet Fehler ordnungsgemäß meldet, damit die Host Anwendung, die die Cmdlets ausführen, auf angemessene Weise reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="06e7a-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="06e7a-105">Ihr Cmdlet sollte bei Auftreten eines Fehlers die [System. Management. Automation. Cmdlet. ThrowTerminatingError \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) -Methode aufgerufen werden, bei der das Cmdlet die Verarbeitung seiner Eingabe Objekte nicht zulässt.</span><span class="sxs-lookup"><span data-stu-id="06e7a-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="06e7a-106">Ihr Cmdlet muss die [System. Management. Automation. Cmdlet. Write-error](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) -Methode zum Melden von Fehlern ohne Abbruch verwenden, wenn das Cmdlet die Verarbeitung der Eingabe Objekte fortsetzen kann.</span><span class="sxs-lookup"><span data-stu-id="06e7a-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="06e7a-107">Beide Methoden stellen einen Fehler Daten Satz bereit, der von der Host Anwendung verwendet werden kann, um die Ursache des Fehlers zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="06e7a-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="06e7a-108">Verwenden Sie die folgenden Richtlinien, um zu bestimmen, ob ein Fehler ein Abbruch Fehler oder ein Fehler ohne Abbruch ist.</span><span class="sxs-lookup"><span data-stu-id="06e7a-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="06e7a-109">Ein Fehler ist ein Abbruch Fehler, wenn das Cmdlet verhindert, dass das aktuelle Objekt weiterhin verarbeitet wird oder wenn andere Eingabe Objekte unabhängig von Ihrem Inhalt erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="06e7a-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="06e7a-110">Ein Fehler ist ein Beendigungs Fehler, wenn Sie nicht möchten, dass das Cmdlet die Verarbeitung des aktuellen Objekts oder weiterer Eingabe Objekte, unabhängig von deren Inhalten, fortsetzt.</span><span class="sxs-lookup"><span data-stu-id="06e7a-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="06e7a-111">Ein Fehler ist ein Abbruch Fehler, wenn er in einem Cmdlet auftritt, das ein Objekt nicht akzeptiert oder zurückgibt, oder wenn es in einem Cmdlet vorkommt, das nur ein Objekt akzeptiert oder zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="06e7a-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="06e7a-112">Ein Fehler ist ein Fehler ohne Abbruch, wenn Sie möchten, dass das Cmdlet die Verarbeitung des aktuellen Objekts und aller weiteren Eingabe Objekte fortsetzt.</span><span class="sxs-lookup"><span data-stu-id="06e7a-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="06e7a-113">Ein Fehler ist ein Fehler ohne Abbruch, wenn er mit einem bestimmten Eingabe Objekt oder einer Teilmenge von Eingabe Objekten verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="06e7a-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="06e7a-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="06e7a-114">See Also</span></span>

[<span data-ttu-id="06e7a-115">System. Management. Automation. Cmdlet. ThrowTerminatingError \*</span><span class="sxs-lookup"><span data-stu-id="06e7a-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="06e7a-116">System. Management. Automation. Cmdlet. Write error</span><span class="sxs-lookup"><span data-stu-id="06e7a-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="06e7a-117">Windows PowerShell-Fehler Datensätze</span><span class="sxs-lookup"><span data-stu-id="06e7a-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="06e7a-118">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="06e7a-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
