---
title: 'Anhang A: Hilfesyntax'
description: In diesem Artikel wird erläutert, wie Sie die Syntax eines Cmdlets lesen und verstehen, wenn es mit „Get-Help“ dargestellt wird.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437981"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="0e131-103">Anhang A: Hilfesyntax</span><span class="sxs-lookup"><span data-stu-id="0e131-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="0e131-104">Das folgende Beispiel zeigt den Abschnitt **SYNTAX** der Hilfe für das Cmdlet `Get-EventLog`.</span><span class="sxs-lookup"><span data-stu-id="0e131-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="0e131-105">In diesem Beispiel wird nur der relevante Teil der Hilfe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0e131-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="0e131-106">Die Syntax besteht hauptsächlich aus mehreren Sätzen von öffnenden und schließenden Klammern (`[]`).</span><span class="sxs-lookup"><span data-stu-id="0e131-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="0e131-107">Diese haben zwei unterschiedliche Bedeutungen, je nachdem, wie sie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0e131-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="0e131-108">Alles, was in eckigen Klammern enthalten ist, ist optional, es sei denn, es handelt sich um einen Satz leerer eckiger Klammern (`[]`).</span><span class="sxs-lookup"><span data-stu-id="0e131-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="0e131-109">Leere eckige Klammern kommen nur nach einem Datentyp vor, z. B. `<string[]>`.</span><span class="sxs-lookup"><span data-stu-id="0e131-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="0e131-110">Dies bedeutet, dass für einen bestimmten Parameter mehr als ein Wert dieses Typs akzeptiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0e131-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="0e131-111">Der erste Parameter im ersten Parametersatz von `Get-EventLog` ist **LogName**.</span><span class="sxs-lookup"><span data-stu-id="0e131-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="0e131-112">LogName steht in eckigen Klammern, was bedeutet, dass es sich um einen Positionsparameter handelt.</span><span class="sxs-lookup"><span data-stu-id="0e131-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="0e131-113">Anders ausgedrückt: Die Angabe des Namens des Parameters selbst ist optional, solange er an der richtigen Position angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="0e131-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="0e131-114">Die Informationen in den spitzen Klammern (`<>`) hinter dem Parameternamen zeigen an, dass er einen einzelnen **Zeichen folgen**wert benötigt.</span><span class="sxs-lookup"><span data-stu-id="0e131-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="0e131-115">Der gesamte Parametername und Datentyp stehen nicht in eckigen Klammern, sodass der Parameter **LogName** erforderlich ist, wenn dieser Parametersatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0e131-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="0e131-116">Der zweite Parameter ist **InstanceId**.</span><span class="sxs-lookup"><span data-stu-id="0e131-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="0e131-117">Beachten Sie, dass der Parametername und der Datentyp vollständig in eckigen Klammern stehen.</span><span class="sxs-lookup"><span data-stu-id="0e131-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="0e131-118">Dies bedeutet, dass der Parameter **InstanceId** optional, nicht obligatorisch ist.</span><span class="sxs-lookup"><span data-stu-id="0e131-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="0e131-119">Beachten Sie außerdem, dass **InstanceId** von einem eigenen Satz eckiger Klammern umgeben ist.</span><span class="sxs-lookup"><span data-stu-id="0e131-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="0e131-120">Wie bei dem Parameter **LogName** bedeutet dies, dass dies ein Positionsparameter ist.</span><span class="sxs-lookup"><span data-stu-id="0e131-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="0e131-121">Es gibt noch einen letzten Satz eckiger Klammern hinter dem Datentyp.</span><span class="sxs-lookup"><span data-stu-id="0e131-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="0e131-122">Dies bedeutet, dass er mehr als einen Wert in Form eines Arrays oder einer durch Trennzeichen getrennten Liste akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="0e131-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="0e131-123">Der zweite Parametersatz verfügt über einen Parameter **Liste**.</span><span class="sxs-lookup"><span data-stu-id="0e131-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="0e131-124">Dabei handelt es sich um einen Switch-Parameter, weil dem Parameternamen kein Datentyp folgt.</span><span class="sxs-lookup"><span data-stu-id="0e131-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="0e131-125">Wenn der Parameter **List** angegeben wird, ist der Wert **True**.</span><span class="sxs-lookup"><span data-stu-id="0e131-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="0e131-126">Wenn er nicht angegeben wird, lautet der Wert **False**.</span><span class="sxs-lookup"><span data-stu-id="0e131-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="0e131-127">Die Syntaxinformationen für einen Befehl können auch mithilfe von `Get-Command` unter Verwendung des Parameters **Syntax** abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="0e131-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="0e131-128">Dies ist eine praktische Abkürzung, die ich immer verwende.</span><span class="sxs-lookup"><span data-stu-id="0e131-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="0e131-129">Dies ermöglicht mir, schnell zu lernen, wie ein Befehl verwendet wird, ohne mehrere Seiten mit Hilfeinformationen durchlesen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="0e131-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="0e131-130">Wenn ich dann trotzdem noch weitere Informationen benötige, verwende ich doch den eigentlichen Hilfeinhalt.</span><span class="sxs-lookup"><span data-stu-id="0e131-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="0e131-131">Je mehr Sie das Hilfesystem in PowerShell verwenden, desto einfacher wird es, sich alle unterschiedlichen Nuancen zu merken.</span><span class="sxs-lookup"><span data-stu-id="0e131-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="0e131-132">Bevor Sie es bemerken, wird Ihnen seine Verwendung zur zweiten Natur.</span><span class="sxs-lookup"><span data-stu-id="0e131-132">Before you know it, using it becomes second nature.</span></span>
