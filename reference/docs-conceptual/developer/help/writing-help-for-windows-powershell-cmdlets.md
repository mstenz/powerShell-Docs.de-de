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
ms.openlocfilehash: fd565e8bf8429d91d785664c8cc69d1843439219
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560592"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="b2a0b-102">Schreiben von Hilfe für PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b2a0b-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="b2a0b-103">PowerShell-Cmdlets können nützlich sein, aber wenn in den Hilfe Themen nicht klar erklärt wird, was das Cmdlet tut und wie es verwendet werden kann, wird das Cmdlet möglicherweise nicht verwendet, oder es ist noch schlimmer, dass es die Benutzer beeinträchtigen könnte.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="b2a0b-104">Das XML-basierte Cmdlet-Hilfedatei Format erhöht die Konsistenz, aber die großartige Hilfe erfordert viel mehr.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="b2a0b-105">Wenn Sie die Cmdlet-Hilfe noch nie geschrieben haben, überprüfen Sie die folgenden Richtlinien.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="b2a0b-106">Das XML-Schema, das zum Erstellen des Cmdlet-Hilfe Themas erforderlich ist, wird im folgenden Abschnitt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="b2a0b-107">Beginnen Sie mit [dem Erstellen der Cmdlet-Hilfedatei](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="b2a0b-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="b2a0b-108">Dieses Thema enthält eine Beschreibung der XML-Knoten der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="b2a0b-109">Schreiben von Richtlinien für die Cmdlet-Hilfe</span><span class="sxs-lookup"><span data-stu-id="b2a0b-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="b2a0b-110">Gut schreiben</span><span class="sxs-lookup"><span data-stu-id="b2a0b-110">Write well</span></span>
<span data-ttu-id="b2a0b-111">Nothing ersetzt ein gut geschriebenes Thema.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="b2a0b-112">Wenn Sie kein professioneller Writer sind, finden Sie einen Writer oder Editor, der Ihnen hilft.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="b2a0b-113">Eine weitere Alternative besteht darin, den Hilfetext in Microsoft Word zu kopieren und die Grammatik-und Rechtschreibprüfungen zu verwenden, um Ihre Arbeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="b2a0b-114">Einfaches schreiben</span><span class="sxs-lookup"><span data-stu-id="b2a0b-114">Write simply</span></span>
<span data-ttu-id="b2a0b-115">Verwenden Sie einfache Wörter und Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-115">Use simple words and phrases.</span></span>
<span data-ttu-id="b2a0b-116">Fachsprache vermeiden.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-116">Avoid jargon.</span></span>
<span data-ttu-id="b2a0b-117">Beachten Sie, dass viele Leser nur mit einem fremdsprachigen Wörterbuch und Ihrem Hilfethema ausgestattet sind.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="b2a0b-118">Konsistentes schreiben</span><span class="sxs-lookup"><span data-stu-id="b2a0b-118">Write consistently</span></span>
<span data-ttu-id="b2a0b-119">Die Hilfe zu verwandten Cmdlets sollte ähnlich sein (z. b. Get-x und Set-x).</span><span class="sxs-lookup"><span data-stu-id="b2a0b-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="b2a0b-120">Verwenden Sie die Standard Beschreibungen für Standardparameter wie " **Force** " und " **Inputobject**".</span><span class="sxs-lookup"><span data-stu-id="b2a0b-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="b2a0b-121">(Kopieren Sie Sie aus der Hilfe für die Core-Cmdlets.) Verwenden Sie die Standardbegriffe.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="b2a0b-122">Verwenden Sie z. b. "Parameter", nicht "Argument", und verwenden Sie "Cmdlet" nicht "Command" oder "Command-Let".</span><span class="sxs-lookup"><span data-stu-id="b2a0b-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="b2a0b-123">Starten der Synchronisierungs mit einem Verb</span><span class="sxs-lookup"><span data-stu-id="b2a0b-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="b2a0b-124">Das Feld Zusammenfassung informiert den Benutzer über das, was das Cmdlet tut, nicht über dessen Funktionsweise.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="b2a0b-125">Verben erstellen eine Task basierte-Anweisung, mit der Benutzer informiert werden, wenn dieses Cmdlet Ihre Anforderungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="b2a0b-126">Verwenden Sie einfache Verben wie "Get", "Create" und "Change".</span><span class="sxs-lookup"><span data-stu-id="b2a0b-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="b2a0b-127">Vermeiden Sie "Set", was vage und ausgefallene Wörter wie "Modify" sein kann.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="b2a0b-128">Fokus auf Objekte</span><span class="sxs-lookup"><span data-stu-id="b2a0b-128">Focus on objects</span></span>
<span data-ttu-id="b2a0b-129">Die meisten Cmdlets "Get" zeigen etwas an, aber Ihre primäre Funktion ist das Abfangen eines Objekts.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="b2a0b-130">Konzentrieren Sie sich in der Hilfe auf das-Objekt, damit die Benutzer verstehen, dass die Standard Anzeige eine von vielen ist, und dass Sie die Methoden und Eigenschaften des Objekts, das Sie für Sie abgerufen haben, auf unterschiedliche Weise verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="b2a0b-131">Ausführliche Beschreibungen schreiben</span><span class="sxs-lookup"><span data-stu-id="b2a0b-131">Write detailed descriptions</span></span>
<span data-ttu-id="b2a0b-132">Listen Sie kurz alle Elemente auf, die das Cmdlet in der ausführlichen Beschreibung ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="b2a0b-133">Wenn die Main-Funktion eine Eigenschaft ändern soll, das Cmdlet jedoch alle Eigenschaften ändern kann, Listen Sie diese in der ausführlichen Beschreibung auf.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="b2a0b-134">Konventionelle Syntax verwenden</span><span class="sxs-lookup"><span data-stu-id="b2a0b-134">Use conventional syntax</span></span>
<span data-ttu-id="b2a0b-135">Verwenden Sie das standardmäßige Backus-Naur-Format, das bei der Windows-und UNIX-Befehlszeilen Hilfe üblich ist.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="b2a0b-136">Verwenden von Microsoft .NET Framework-Typen für Parameterwerte</span><span class="sxs-lookup"><span data-stu-id="b2a0b-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="b2a0b-137">Die Platzhalter für Parameterwerte (in den Syntax-und Parameter Beschreibungen) zeigen die .NET Framework Typen der Objekte an, die der-Parameter akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="b2a0b-138">Das PowerShell-Team hat diese Konvention entwickelt, um Benutzern die .NET Framework zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="b2a0b-139">Schreiben von kompletten Parameter Beschreibungen</span><span class="sxs-lookup"><span data-stu-id="b2a0b-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="b2a0b-140">Parameter Beschreibungen müssen Benutzer über zwei Dinge informieren: wie der-Parameter (seine Auswirkung) und was Sie für die Parameterwerte eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="b2a0b-141">Praktische Beispiele schreiben</span><span class="sxs-lookup"><span data-stu-id="b2a0b-141">Write practical examples</span></span>
<span data-ttu-id="b2a0b-142">In den Beispielen sollte gezeigt werden, wie alle Parameter verwendet werden, aber es ist wichtig zu veranschaulichen, wie das Cmdlet in realen Aufgaben verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="b2a0b-143">Beginnen Sie mit einem einfachen Beispiel, und schreiben Sie immer komplexere Beispiele.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="b2a0b-144">Im letzten Beispiel wird gezeigt, wie das Cmdlet in einer Pipeline verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="b2a0b-145">Verwenden des Felds "Notizen"</span><span class="sxs-lookup"><span data-stu-id="b2a0b-145">Use the Notes field</span></span>
<span data-ttu-id="b2a0b-146">Verwenden Sie das Feld Notizen, um die Konzepte zu erläutern, die Benutzer benötigen, um das Cmdlet zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="b2a0b-147">Sie können auch Notizen verwenden, um Benutzern zu helfen, häufige Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="b2a0b-148">Vermeiden Sie URLs, wenn Sie sich ändern.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="b2a0b-149">Geben Sie stattdessen die zu suchenden Nutzungsbedingungen an.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="b2a0b-150">Testen der Hilfe</span><span class="sxs-lookup"><span data-stu-id="b2a0b-150">Test your Help</span></span>
<span data-ttu-id="b2a0b-151">Testen Sie die Hilfe wie beim Testen des Codes.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="b2a0b-152">Bitten Sie Freunde und Kollegen, Ihre Hilfe Inhalte zu lesen und Feedback zu geben.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="b2a0b-153">Sie können auch Feedback aus Newsgroups anfordern.</span><span class="sxs-lookup"><span data-stu-id="b2a0b-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2a0b-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b2a0b-154">See Also</span></span>

 [<span data-ttu-id="b2a0b-155">Erstellen der Cmdlet-Hilfedatei</span><span class="sxs-lookup"><span data-stu-id="b2a0b-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="b2a0b-156">Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-157">Vorgehensweise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="b2a0b-158">Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-159">Vorgehensweise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="b2a0b-160">Vorgehensweise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-161">Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-162">Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-163">Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-164">Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="b2a0b-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b2a0b-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b2a0b-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
