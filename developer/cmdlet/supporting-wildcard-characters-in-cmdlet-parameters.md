---
title: Unterstützung von Platzhalterzeichen in der Cmdlet-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059608"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="00051-102">Unterstützung für Platzhalter in Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="00051-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="00051-103">Häufig müssen Sie ein Cmdlet zum Ausführen für eine Gruppe von Ressourcen nicht für eine einzelne Ressource zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="00051-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="00051-104">Suchen alle Dateien in einem Datenspeicher, die den gleichen Namen oder die Erweiterung kann z. B. ein Cmdlet müssen.</span><span class="sxs-lookup"><span data-stu-id="00051-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="00051-105">Sie müssen Unterstützung für Platzhalterzeichen angeben, beim Entwerfen eines Cmdlets, das für eine Gruppe von Ressourcen ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="00051-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="00051-106">Verwenden von Platzhalterzeichen wird mitunter als *Platzhaltermuster*.</span><span class="sxs-lookup"><span data-stu-id="00051-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="00051-107">Windows PowerShell-Cmdlets, die Platzhalter verwenden</span><span class="sxs-lookup"><span data-stu-id="00051-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="00051-108">Viele Windows PowerShell-Cmdlets unterstützen Platzhalterzeichen für die Parameterwerte.</span><span class="sxs-lookup"><span data-stu-id="00051-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="00051-109">Verfügt beispielsweise fast alle Cmdlets, die über eine `Name` oder `Path` Parameter unterstützt Platzhalterzeichen für diese Parameter.</span><span class="sxs-lookup"><span data-stu-id="00051-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="00051-110">(Zwar die meisten Cmdlets, die eine `Path` Parameter haben. auch eine `LiteralPath` Parameter, der Platzhalterzeichen nicht unterstützt.) Der folgende Befehl zeigt, wie ein Platzhalterzeichen verwendet wird, um alle Cmdlets in der aktuellen Sitzung zurückzugeben, deren Name das Get-Verb enthält.</span><span class="sxs-lookup"><span data-stu-id="00051-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="00051-111">**PS > Get-Command Get -\***</span><span class="sxs-lookup"><span data-stu-id="00051-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="00051-112">Unterstützte Platzhalterzeichen</span><span class="sxs-lookup"><span data-stu-id="00051-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="00051-113">Windows PowerShell unterstützt die folgenden Platzhalterzeichen handeln.</span><span class="sxs-lookup"><span data-stu-id="00051-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="00051-114">Platzhalterzeichen</span><span class="sxs-lookup"><span data-stu-id="00051-114">Wildcard character</span></span>|<span data-ttu-id="00051-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="00051-115">Description</span></span>|<span data-ttu-id="00051-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="00051-116">Example</span></span>|<span data-ttu-id="00051-117">Treffer</span><span class="sxs-lookup"><span data-stu-id="00051-117">Matches</span></span>|<span data-ttu-id="00051-118">Stimmt nicht überein mit</span><span class="sxs-lookup"><span data-stu-id="00051-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="00051-119">Entspricht null oder mehr Zeichen, beginnend mit der angegebenen Position</span><span class="sxs-lookup"><span data-stu-id="00051-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="00051-120">a\*</span><span class="sxs-lookup"><span data-stu-id="00051-120">a\*</span></span>|<span data-ttu-id="00051-121">A, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="00051-121">A, ag, Apple</span></span>||
|<span data-ttu-id="00051-122">?</span><span class="sxs-lookup"><span data-stu-id="00051-122">?</span></span>|<span data-ttu-id="00051-123">Übereinstimmungen Anycharacter an der angegebenen position</span><span class="sxs-lookup"><span data-stu-id="00051-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="00051-124">? n</span><span class="sxs-lookup"><span data-stu-id="00051-124">?n</span></span>|<span data-ttu-id="00051-125">Ein im, auf</span><span class="sxs-lookup"><span data-stu-id="00051-125">An, in, on</span></span>|<span data-ttu-id="00051-126">ausgeführt wurde</span><span class="sxs-lookup"><span data-stu-id="00051-126">ran</span></span>|
|<span data-ttu-id="00051-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="00051-127">[ ]</span></span>|<span data-ttu-id="00051-128">Entspricht einen Bereich von Zeichen</span><span class="sxs-lookup"><span data-stu-id="00051-128">Matches a range of characters</span></span>|<span data-ttu-id="00051-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="00051-129">[a-l]ook</span></span>|<span data-ttu-id="00051-130">Buch, Cook, suchen</span><span class="sxs-lookup"><span data-stu-id="00051-130">book, cook, look</span></span>|<span data-ttu-id="00051-131">dauerte</span><span class="sxs-lookup"><span data-stu-id="00051-131">took</span></span>|
|<span data-ttu-id="00051-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="00051-132">[ ]</span></span>|<span data-ttu-id="00051-133">Stimmt mit den angegebenen Zeichen</span><span class="sxs-lookup"><span data-stu-id="00051-133">Matches the specified characters</span></span>|<span data-ttu-id="00051-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="00051-134">[bc]ook</span></span>|<span data-ttu-id="00051-135">Buch, cook</span><span class="sxs-lookup"><span data-stu-id="00051-135">book, cook</span></span>|<span data-ttu-id="00051-136">Suchen Sie</span><span class="sxs-lookup"><span data-stu-id="00051-136">look</span></span>|

<span data-ttu-id="00051-137">Wenn Sie Cmdlets, die Platzhalterzeichen unterstützt entwerfen, können Sie für Kombinationen von Platzhalterzeichen.</span><span class="sxs-lookup"><span data-stu-id="00051-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="00051-138">Beispielsweise der folgende Befehl verwendet den `Get-ChildItem` Cmdlet zum Abrufen von alle TXT-Dateien, die sich im Ordner c:\Techdocs und, beginnen mit den Buchstaben "a" bis "l."</span><span class="sxs-lookup"><span data-stu-id="00051-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="00051-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="00051-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="00051-140">Der vorherige Befehl verwendet den Bereich Platzhalter **[a-l]** um anzugeben, dass der Dateiname mit den Zeichen "a" bis "l." beginnen soll</span><span class="sxs-lookup"><span data-stu-id="00051-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="00051-141">Anschließend verwendet der Befehl die \* Platzhalterzeichen als Platzhalter für alle Zeichen zwischen den ersten Buchstaben des Dateinamens und der Erweiterung TXT.</span><span class="sxs-lookup"><span data-stu-id="00051-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="00051-142">Im folgenden Beispiel wird ein Bereich Platzhaltermuster, die ohne des Buchstabens "d", aber mit umfasst alle anderen Buchstaben von "a" bis "f."</span><span class="sxs-lookup"><span data-stu-id="00051-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="00051-143">**Get-Childitem c:\techdocs\\[a-Cef]\*txt**</span><span class="sxs-lookup"><span data-stu-id="00051-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="00051-144">Behandeln von Literalzeichen in Platzhaltermuster</span><span class="sxs-lookup"><span data-stu-id="00051-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="00051-145">Wenn die Platzhaltermuster, das Sie angeben, Literalzeichen enthält, verwenden Sie ein rückwärts geneigtes Apostroph (') als Escapezeichen ein.</span><span class="sxs-lookup"><span data-stu-id="00051-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="00051-146">Wenn Sie programmgesteuert Literalzeichen angeben, verwenden Sie ein einzelnes Hochkomma.</span><span class="sxs-lookup"><span data-stu-id="00051-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="00051-147">Wenn Sie literale Zeichen an der Eingabeaufforderung angeben, verwenden Sie zwei Graviszeichen.</span><span class="sxs-lookup"><span data-stu-id="00051-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="00051-148">Im folgenden Format enthält beispielsweise zwei eckige Klammern, die buchstäblich berücksichtigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="00051-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="00051-149">"John Smith \`[\*"] "(programmgesteuert angegeben)</span><span class="sxs-lookup"><span data-stu-id="00051-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="00051-150">"John Smith \` \`[\*\`"] "(an der Eingabeaufforderung angegeben)</span><span class="sxs-lookup"><span data-stu-id="00051-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="00051-151">Diesem Muster entsprechen "John Smith [Marketing]" oder "John Smith [Entwicklung]".</span><span class="sxs-lookup"><span data-stu-id="00051-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="00051-152">Platzhalterzeichen und Cmdlet-Ausgabe</span><span class="sxs-lookup"><span data-stu-id="00051-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="00051-153">Bei der cmdletparameter Platzhalterzeichen unterstützt, generiert ein Cmdlet-Vorgang in der Regel eine arrayausgabe.</span><span class="sxs-lookup"><span data-stu-id="00051-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="00051-154">In einigen Fällen ist es nicht sinnvoll, unterstützt ein Array ausgegeben werden, da der Benutzer möglicherweise nur ein einziges Element zu einem Zeitpunkt verwendet.</span><span class="sxs-lookup"><span data-stu-id="00051-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="00051-155">Z. B. die `Set-Location` Cmdlet unterstützt ein Array ausgeben, da der Benutzer mit nur einem einzigen Ort festlegt.</span><span class="sxs-lookup"><span data-stu-id="00051-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="00051-156">In diesem Fall das Cmdlet immer noch unterstützt Platzhalterzeichen an zentraler Stelle Auflösung wird erzwungen.</span><span class="sxs-lookup"><span data-stu-id="00051-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="00051-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="00051-157">See Also</span></span>

[<span data-ttu-id="00051-158">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="00051-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="00051-159">WildcardPattern-Klasse</span><span class="sxs-lookup"><span data-stu-id="00051-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
