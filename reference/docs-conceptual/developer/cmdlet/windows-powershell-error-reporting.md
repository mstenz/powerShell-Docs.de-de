---
title: Windows PowerShell-Fehlerberichterstattung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364269"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="12121-102">Windows PowerShell-Fehlerberichterstattung</span><span class="sxs-lookup"><span data-stu-id="12121-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="12121-103">In den Themen in diesem Abschnitt wird erläutert, wie-Cmdlets Fehler melden.</span><span class="sxs-lookup"><span data-stu-id="12121-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="12121-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="12121-104">In This Section</span></span>

<span data-ttu-id="12121-105">[Konzepte für die Fehlerberichterstattung](./error-reporting-concepts.md) Beschreibt die beiden Mechanismen, die Cmdlets zum Melden von Fehlern verwenden können.</span><span class="sxs-lookup"><span data-stu-id="12121-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="12121-106">[Fehler beim Beenden](./terminating-errors.md) Beschreibt die Methode, die zum Melden von Beendigungs Fehlern verwendet wird, wobei diese Methode innerhalb des Cmdlets aufgerufen werden kann, und Ausnahmen, die von der Windows PowerShell-Laufzeit zurückgegeben werden können, wenn die-Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="12121-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="12121-107">[Fehler ohne](./non-terminating-errors.md) Abbruch Beschreibt die Methode, die verwendet wird, um Fehler ohne Abbruch zu melden, und wo diese Methode innerhalb des Cmdlets aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="12121-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="12121-108">[Anzeigen von Fehlerinformationen nach Kategorie](./displaying-error-information.md) Erläutert die Möglichkeiten, wie Benutzerfehler anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="12121-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="12121-109">[Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md) Beschreibt die Komponenten eines Fehler Datensatzes.</span><span class="sxs-lookup"><span data-stu-id="12121-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="12121-110">[Interpretieren von ErrorRecord-Objekten](./interpreting-errorrecord-objects.md) Erläutert, wie ErrorRecord-Objekte interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="12121-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="12121-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="12121-111">See Also</span></span>

[<span data-ttu-id="12121-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="12121-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
