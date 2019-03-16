---
title: Fehler, die Konzepte der Berichterstellung | Microsoft-Dokumentation
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054406"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="31b76-102">Konzepte der Fehlerberichterstattung</span><span class="sxs-lookup"><span data-stu-id="31b76-102">Error Reporting Concepts</span></span>

<span data-ttu-id="31b76-103">Windows PowerShell bietet zwei Mechanismen zum Melden von Fehlern: ein Mechanismus zum *Fehler beenden* und einen anderen Mechanismus für die *Fehler ohne Abbruch*.</span><span class="sxs-lookup"><span data-stu-id="31b76-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="31b76-104">Es ist richtig, damit die hostanwendung, die Ihre Cmdlets ausgeführt wird, in geeigneter Weise reagieren kann wichtig für Ihre Cmdlets aus, um Fehler zu melden.</span><span class="sxs-lookup"><span data-stu-id="31b76-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="31b76-105">Sollte Ihr Cmdlet rufen Sie die [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) Methode, wenn ein Fehler auftritt, nicht, oder das-Cmdlet verarbeitet Eingabeobjekte weiterhin sollten nicht zulassen.</span><span class="sxs-lookup"><span data-stu-id="31b76-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="31b76-106">Ihr Cmdlet aufrufen, sollte die [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) Methode zum Melden Fehler ohne Abbruch, wenn das Cmdlet die Eingabeobjekte Verarbeitung fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="31b76-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="31b76-107">Beide Methoden bieten einen Fehlerdatensatz, den die hostanwendung verwenden können, um die Ursache des Fehlers untersuchen.</span><span class="sxs-lookup"><span data-stu-id="31b76-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="31b76-108">Verwenden Sie die folgenden Richtlinien, um zu bestimmen, ob ein Fehler ist ein Abbruch oder Fehler ohne Abbruch.</span><span class="sxs-lookup"><span data-stu-id="31b76-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="31b76-109">Ein Fehler ist ein Fehler mit Abbruch an, wenn sie Ihr Cmdlet nicht fortgesetzt werden kann, um das aktuelle Objekt zu verarbeiten oder erfolgreich verarbeitet alle weiteren Eingabeobjekte, unabhängig von deren Inhalt verhindert.</span><span class="sxs-lookup"><span data-stu-id="31b76-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="31b76-110">Ein Fehler ist ein Fehler mit Abbruch, wenn Sie nicht Ihr Cmdlet und weiter verarbeitet werden, das aktuelle Objekt oder weitere Eingabeobjekten, unabhängig von deren Inhalt möchten.</span><span class="sxs-lookup"><span data-stu-id="31b76-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="31b76-111">Ein Fehler ist ein Fehler mit Abbruch an, oder wenn sie ein Cmdlet generiert wird, die nicht akzeptieren, oder Sie geben ein Objekt zurück, wenn es sich in einem Cmdlet auftritt, das akzeptiert oder gibt nur ein Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="31b76-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="31b76-112">Ein Fehler ist ein Fehler ohne Abbruch, sollten Sie dem Cmdlet das aktuelle Objekt und alle weiteren Eingabeobjekte die Verarbeitung fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="31b76-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="31b76-113">Ein Fehler ist ein Fehler ohne Abbruch, wenn er eine bestimmte input-Objekt oder eine Teilmenge der Eingabeobjekte verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="31b76-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="31b76-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="31b76-114">See Also</span></span>

[<span data-ttu-id="31b76-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="31b76-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="31b76-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="31b76-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="31b76-117">Windows PowerShell-Error-Datensätze</span><span class="sxs-lookup"><span data-stu-id="31b76-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="31b76-118">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="31b76-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
