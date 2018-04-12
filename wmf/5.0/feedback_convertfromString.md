---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="97dc6-102">Extrahieren und Analysieren von strukturierten Objekten aus einer Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="97dc6-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="97dc6-103">Auch das Cmdlet „ConvertFrom-String“ weist einige neue Funktionen auf:</span><span class="sxs-lookup"><span data-stu-id="97dc6-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="97dc6-104">Die „ExtentText“-Eigenschaft wird standardmäßig entfernt.</span><span class="sxs-lookup"><span data-stu-id="97dc6-104">Removes the extent text property by default.</span></span> <span data-ttu-id="97dc6-105">Sie können sie mit dem „-IncludeExtent“-Parameter einschließen.</span><span class="sxs-lookup"><span data-stu-id="97dc6-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="97dc6-106">Viele Fehlerbehebungen beim lernenden Algorithmus basierend auf Feedback von MVPs und Community.</span><span class="sxs-lookup"><span data-stu-id="97dc6-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="97dc6-107">Neuer „-UpdateTemplate“-Parameter zum Speichern der Ergebnisse des lernenden Algorithmus in einem Kommentar in der Vorlagendatei.</span><span class="sxs-lookup"><span data-stu-id="97dc6-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="97dc6-108">Dadurch wird der Lernprozess (die langsamste Phase) zu einem einmaligen Aufwand.</span><span class="sxs-lookup"><span data-stu-id="97dc6-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="97dc6-109">Das Ausführen von „Convert-String“ mit einer Vorlage, die den codierten lernenden Algorithmus enthält, erfolgt nun fast unmittelbar.</span><span class="sxs-lookup"><span data-stu-id="97dc6-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="97dc6-110">Extrahieren und Analysieren von strukturierten Objekten aus einer Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="97dc6-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="97dc6-111">In Zusammenarbeit mit [Microsoft Research](http://research.microsoft.com/) wurde das neue Cmdlet **ConvertFrom-String** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="97dc6-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="97dc6-112">Dieses Cmdlet unterstützt zwei Modi: getrennte Analyse und von einem automatisch generierten Beispiel gesteuerte Analyse.</span><span class="sxs-lookup"><span data-stu-id="97dc6-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="97dc6-113">Bei der getrennten Analyse wird die Eingabe standardmäßig bei Leerzeichen getrennt, wobei den resultierenden Gruppen Eigenschaftsnamen zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="97dc6-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="97dc6-114">Sie können das Trennzeichen anpassen:</span><span class="sxs-lookup"><span data-stu-id="97dc6-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="97dc6-115">1 \[C:\\temp\] &gt;&gt; „Hello World“ | ConvertFrom-String | Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="97dc6-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="97dc6-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="97dc6-116">P1    P2</span></span>
--    --

<span data-ttu-id="97dc6-117">Das Cmdlet unterstützt auch die von einem automatisch generierten Beispiel gesteuerte Analyse basierend auf den Forschungsarbeiten zu [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) von [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="97dc6-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="97dc6-118">Nehmen wir zum Einstieg ein textbasiertes Adressbuch:</span><span class="sxs-lookup"><span data-stu-id="97dc6-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="97dc6-119">Kopieren Sie einige Beispiele in eine Datei, die Sie als Vorlage verwenden werden:</span><span class="sxs-lookup"><span data-stu-id="97dc6-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="97dc6-120">Setzen Sie Daten, die Sie extrahieren möchten, in geschweifte Klammern, und geben Sie ihnen einen Namen.</span><span class="sxs-lookup"><span data-stu-id="97dc6-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="97dc6-121">Da die **Name**-Eigenschaft und ihre zugehörigen anderen Eigenschaften mehrfach vorkommen können, müssen Sie ein Sternchen (\*) verwenden, um anzugeben, dass dadurch mehrere Datensätze generiert werden (statt eine Reihe von Eigenschaften in einen Datensatz zu extrahieren):</span><span class="sxs-lookup"><span data-stu-id="97dc6-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="97dc6-122">Ausgehend von diesen Beispielen kann **ConvertFrom-String** nun eine objektbasierte Ausgabe automatisch aus Eingabedateien mit ähnlicher Struktur extrahieren.</span><span class="sxs-lookup"><span data-stu-id="97dc6-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="97dc6-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="97dc6-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="97dc6-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="97dc6-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="97dc6-125">ExtentText                     Name               City     State</span><span class="sxs-lookup"><span data-stu-id="97dc6-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="97dc6-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="97dc6-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="97dc6-127">Um extrahierten Text weiter zu bearbeiten, erfasst die **ExtentText**-Eigenschaft den unformatierten Text, anhand dessen der Datensatz extrahiert wurde.</span><span class="sxs-lookup"><span data-stu-id="97dc6-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="97dc6-128">Wenn Sie Feedback zu diesem Feature geben oder Inhalte teilen möchten, bei denen beim Schreiben von Beispielen Probleme auftreten, senden Sie eine E-Mail an <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="97dc6-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>