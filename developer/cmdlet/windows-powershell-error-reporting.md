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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067092"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="bee7a-102">Windows PowerShell-Fehlerberichterstattung</span><span class="sxs-lookup"><span data-stu-id="bee7a-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="bee7a-103">Die Themen in diesem Abschnitt wird erläutert, wie Cmdlets Fehler gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="bee7a-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bee7a-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="bee7a-104">In This Section</span></span>

<span data-ttu-id="bee7a-105">[Konzepte von Reporting Fehler](./error-reporting-concepts.md) wird beschrieben, die zwei Mechanismen, die-Cmdlets, um Fehler zu melden verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bee7a-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="bee7a-106">[Beenden Sie die Fehler](./terminating-errors.md) beschreibt die Methode verwendet, um melden beendet, in dem diese Methode aufgerufen werden kann aus in das-Cmdlet, Fehlern und Ausnahmen, die von der Windows PowerShell-Laufzeit zurückgegeben werden können, wenn die Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="bee7a-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="bee7a-107">[Fehler ohne Abbruch](./non-terminating-errors.md) beschreibt die Methode verwendet einen Fehler ohne Abbruch und, in dem diese Methode aus dem-Cmdlet aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="bee7a-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="bee7a-108">[Anzeigen von Fehlerinformationen nach Kategorie](./displaying-error-information.md) beschreibt die Möglichkeiten zur, dass Benutzer Fehler angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="bee7a-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="bee7a-109">[Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md) beschreibt die Komponenten eines fehlerdatensatzes.</span><span class="sxs-lookup"><span data-stu-id="bee7a-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="bee7a-110">[Interpretieren von ErrorRecord Objekte](./interpreting-errorrecord-objects.md) wird erläutert, wie ErrorRecord Objekte interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="bee7a-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="bee7a-111">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bee7a-111">See Also</span></span>

[<span data-ttu-id="bee7a-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bee7a-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
