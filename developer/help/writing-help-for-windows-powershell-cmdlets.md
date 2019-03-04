---
title: Schreiben von Hilfe für PowerShell-Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857856"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="1dd75-102">Schreiben von Hilfe für PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1dd75-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="1dd75-103">PowerShell-Cmdlets kann nützlich sein, aber es sei denn, Ihre Hilfethemen eindeutig erläutern, was das Cmdlet durchführt und wie es verwendet, mit dem-Cmdlet kann nicht verwendet oder, schlimmer noch, kann er Benutzer frustrierend sein.</span><span class="sxs-lookup"><span data-stu-id="1dd75-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="1dd75-104">Das XML-basierten Cmdlet-Hilfe-Dateiformat verbessert die Konsistenz, aber große Hilfe erfordert viel mehr.</span><span class="sxs-lookup"><span data-stu-id="1dd75-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="1dd75-105">Wenn Sie Hilfe zu Cmdlets nie geschrieben haben, überprüfen Sie die folgenden Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="1dd75-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="1dd75-106">Das XML-Schema erforderlich, um die Cmdlet-Hilfethemas zu erstellen, wird im folgenden Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1dd75-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="1dd75-107">Beginnen Sie mit [erstellen die Cmdlet-Hilfedatei](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="1dd75-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="1dd75-108">Dieses Thema enthält eine Beschreibung der XML-Knoten der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="1dd75-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="1dd75-109">Schreiben von Richtlinien für die Cmdlet-Hilfe</span><span class="sxs-lookup"><span data-stu-id="1dd75-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="1dd75-110">Schreiben Sie auch</span><span class="sxs-lookup"><span data-stu-id="1dd75-110">Write well</span></span>
<span data-ttu-id="1dd75-111">"Nothing" wird eine gut geschriebene Thema ersetzt.</span><span class="sxs-lookup"><span data-stu-id="1dd75-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="1dd75-112">Wenn Sie nicht über ein professional Writer sind, finden Sie ein Writer oder den Editor, die Ihnen helfen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="1dd75-113">Eine Alternative besteht darin, den Hilfetext in Microsoft Word kopieren und verwenden Sie die Grammatik und Rechtschreibung überprüft werden, um Ihre Arbeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="1dd75-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="1dd75-114">Einfach zu schreiben</span><span class="sxs-lookup"><span data-stu-id="1dd75-114">Write simply</span></span>
<span data-ttu-id="1dd75-115">Verwenden Sie einfache Wörter und Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="1dd75-115">Use simple words and phrases.</span></span>
<span data-ttu-id="1dd75-116">Vermeiden Sie Jargon.</span><span class="sxs-lookup"><span data-stu-id="1dd75-116">Avoid jargon.</span></span>
<span data-ttu-id="1dd75-117">Beachten Sie, dass viele Leser nur mit einem fremdsprachige Wörterbuch und Ihre Hilfethema ausgestattet sind.</span><span class="sxs-lookup"><span data-stu-id="1dd75-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="1dd75-118">Schreiben Sie konsistent</span><span class="sxs-lookup"><span data-stu-id="1dd75-118">Write consistently</span></span>
<span data-ttu-id="1dd75-119">Hilfe zu verwandte Cmdlets (z. B. "," Get-X "und" Set-X ") ähneln sollte.</span><span class="sxs-lookup"><span data-stu-id="1dd75-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="1dd75-120">Verwenden Sie die standard-Beschreibungen für standard-Parameter, wie z. B. **Force** und **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="1dd75-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="1dd75-121">(Kopieren sie aus der Hilfe für die Kern-Cmdlets.) Verwenden Sie die standard-Begriffe.</span><span class="sxs-lookup"><span data-stu-id="1dd75-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="1dd75-122">Z. B. "mit dem Parameter", nicht "Argument", und verwenden "Cmdlet" nicht "Befehl" oder "Command-Let".</span><span class="sxs-lookup"><span data-stu-id="1dd75-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="1dd75-123">Starten Sie die Übersicht mit einem verb</span><span class="sxs-lookup"><span data-stu-id="1dd75-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="1dd75-124">Das Feld "Zusammenfassung" wird der Benutzer informiert, welche das Cmdlet durchführt, nicht was, wie es funktioniert.</span><span class="sxs-lookup"><span data-stu-id="1dd75-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="1dd75-125">Verben erstellen Sie eine aufgabenbasierte-Anweisung, die Benutzer darüber informiert, wenn Sie dieses Cmdlet aus, um ihre Anforderungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="1dd75-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="1dd75-126">Verwenden Sie einfache Verben wie "get", "erstellen" und "ändern".</span><span class="sxs-lookup"><span data-stu-id="1dd75-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="1dd75-127">Vermeiden Sie "Set", und sein kann, und mit Effekten Wörter wie "ändern".</span><span class="sxs-lookup"><span data-stu-id="1dd75-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="1dd75-128">Konzentrieren Sie sich für Objekte</span><span class="sxs-lookup"><span data-stu-id="1dd75-128">Focus on objects</span></span>
<span data-ttu-id="1dd75-129">Die meisten "get" Anzeigen der Cmdlets etwas, aber die primäre Funktion zum Abrufen eines Objekts ist.</span><span class="sxs-lookup"><span data-stu-id="1dd75-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="1dd75-130">In der Ihre Hilfe konzentrieren Sie sich für das Objekt, damit Benutzer verstehen, dass die Standardanzeige eines von vielen ist und sie verwenden können, die Methoden und Eigenschaften des Objekts, das Sie für diese auf unterschiedliche Weise abgerufen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="1dd75-131">Schreiben Sie eine detaillierte Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1dd75-131">Write detailed descriptions</span></span>
<span data-ttu-id="1dd75-132">Kurze Listen Sie alle Elemente, die mit dem-Cmdlet in der ausführlichen Beschreibung ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="1dd75-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="1dd75-133">Wenn die main-Funktion ist eine Eigenschaft zu ändern, aber das-Cmdlet kann alle Eigenschaften ändern, listet diese in der detaillierten Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="1dd75-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="1dd75-134">Verwenden Sie herkömmliche Syntax.</span><span class="sxs-lookup"><span data-stu-id="1dd75-134">Use conventional syntax</span></span>
<span data-ttu-id="1dd75-135">Verwenden Sie das standardmäßige Backus-Naur-Format handelt es sich häufig für Windows und UNIX-Befehlszeilenhilfe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1dd75-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="1dd75-136">Verwenden Sie Microsoft .NET Framework-Typen für Parameterwerte</span><span class="sxs-lookup"><span data-stu-id="1dd75-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="1dd75-137">Die Platzhalter für Parameterwerte (in der Syntax- und parameterbeschreibungen) anzeigen, die .NET Framework-Typen der Objekte, die der Parameter akzeptiert wird.</span><span class="sxs-lookup"><span data-stu-id="1dd75-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="1dd75-138">Das PowerShell-Team entwickelt diese Konvention können Benutzer über die .NET Framework zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="1dd75-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="1dd75-139">Schreiben Sie die vollständige parameterbeschreibungen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="1dd75-140">Beschreibungen der Parameter müssen ein Benutzer zwei Möglichkeiten informieren: Welche Parameters (dessen Auswirkung) ist und was sie für die Parameterwerte eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="1dd75-141">Praktische Beispiele zu schreiben</span><span class="sxs-lookup"><span data-stu-id="1dd75-141">Write practical examples</span></span>
<span data-ttu-id="1dd75-142">In den Beispielen sollte mit allen Parametern, aber das wichtigste ist veranschaulichen, wie Sie das Cmdlet in wirklichkeitsgetreue Aufgaben verwenden.</span><span class="sxs-lookup"><span data-stu-id="1dd75-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="1dd75-143">Beginnen Sie mit der ein einfaches Beispiel, und Schreiben Sie immer komplexere Beispiele.</span><span class="sxs-lookup"><span data-stu-id="1dd75-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="1dd75-144">Zeigen Sie im abschließenden Beispiel, wie Sie das Cmdlet in einer Pipeline verwenden.</span><span class="sxs-lookup"><span data-stu-id="1dd75-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="1dd75-145">Verwenden Sie das Feld "Notizen"</span><span class="sxs-lookup"><span data-stu-id="1dd75-145">Use the Notes field</span></span>
<span data-ttu-id="1dd75-146">Verwenden Sie das Feld "Notizen", um die Konzepte zu erläutern, die Benutzer das-Cmdlet zu verstehen müssen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="1dd75-147">Sie können auch Anmerkungen zu dieser Version verwenden, können Benutzer, die häufige Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="1dd75-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="1dd75-148">Vermeiden Sie URLs, wie sie ändern.</span><span class="sxs-lookup"><span data-stu-id="1dd75-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="1dd75-149">Geben Sie stattdessen Benutzer Suchbegriffe für.</span><span class="sxs-lookup"><span data-stu-id="1dd75-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="1dd75-150">Testen Sie Ihre Hilfe</span><span class="sxs-lookup"><span data-stu-id="1dd75-150">Test your Help</span></span>
<span data-ttu-id="1dd75-151">Testen Sie die Hilfe so, wie Sie den Code zu testen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="1dd75-152">Freunden und Kollegen lesen Sie den Hilfeinhalt und Feedback geben.</span><span class="sxs-lookup"><span data-stu-id="1dd75-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="1dd75-153">Sie können auch Feedback aus die Newsgroups einzuholen.</span><span class="sxs-lookup"><span data-stu-id="1dd75-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dd75-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1dd75-154">See Also</span></span>

 [<span data-ttu-id="1dd75-155">Vorgehensweise: Erstellen Sie die Cmdlet-Hilfedatei</span><span class="sxs-lookup"><span data-stu-id="1dd75-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="1dd75-156">Die Cmdlet-Namen und eine Zusammenfassung zu einem Cmdlet-Hilfethema hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1dd75-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-157">So fügen Sie die ausführliche Beschreibung zu einem Cmdlet-Hilfethema hinzu</span><span class="sxs-lookup"><span data-stu-id="1dd75-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="1dd75-158">So fügen Sie die Syntax für ein Cmdlet-Hilfethema hinzu</span><span class="sxs-lookup"><span data-stu-id="1dd75-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-159">Gewusst wie: Hinzufügen von Parametern zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="1dd75-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="1dd75-160">So fügen Sie die zu einem Cmdlet-Hilfethemas Eingabetypen hinzu</span><span class="sxs-lookup"><span data-stu-id="1dd75-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-161">Rückgabe von Werten für ein Cmdlet-Hilfethema hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1dd75-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-162">Gewusst wie: Hinzufügen von Notizen an ein Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="1dd75-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-163">Beispiele für ein Cmdlet-Hilfethema hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1dd75-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-164">Gewusst wie: Hinzufügen von Links zu verwandten Themen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="1dd75-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="1dd75-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1dd75-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)