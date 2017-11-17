# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="9b968-101">Styleguide für PowerShell-Dokumente</span><span class="sxs-lookup"><span data-stu-id="9b968-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="9b968-102">Titel/Überschriften</span><span class="sxs-lookup"><span data-stu-id="9b968-102">Titles/Headings</span></span>

* <span data-ttu-id="9b968-103">Titel/Überschriften (alles, dem \# vorangestellt ist) müssen mit einem Zeilenumbruch ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="9b968-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="9b968-104">Nur der erste Buchstaben des Titels und alle Eigennamen im Titel sollten groß geschrieben werden</span><span class="sxs-lookup"><span data-stu-id="9b968-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="9b968-105">Nur 1 H1 pro Dokument</span><span class="sxs-lookup"><span data-stu-id="9b968-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="9b968-106">Wenn Sie Referenzinhalte bearbeiten, werden die H2s von platyPS vorgeschriebenen und sollten nicht hinzugefügt oder entfernt werden, da dies zu einer Buildunterbrechung führt</span><span class="sxs-lookup"><span data-stu-id="9b968-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="9b968-107">Verwenden Sie nur \#-Stilheader (im Gegensatz zum „=“ oder dem Stilheader \-)</span><span class="sxs-lookup"><span data-stu-id="9b968-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="9b968-108">Richtig</span><span class="sxs-lookup"><span data-stu-id="9b968-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="9b968-109">Falsch</span><span class="sxs-lookup"><span data-stu-id="9b968-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="9b968-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b968-110">Syntax</span></span>

* <span data-ttu-id="9b968-111">Verwenden Sie \\` bei der Kommunikation über ein Cmdlet im Absatz, um Cmdlet-Namen zu markieren</span><span class="sxs-lookup"><span data-stu-id="9b968-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="9b968-112">Richtiges Beispiel: Dieses `Write-Host`-Cmdlet ermöglicht es...</span><span class="sxs-lookup"><span data-stu-id="9b968-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="9b968-113">Falsches Beispiel: Dieses **Write-Host**-Cmdlet kann... und wird per Pipeline übertragen an das out-file-Cmdlet...</span><span class="sxs-lookup"><span data-stu-id="9b968-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="9b968-114">Beim Schreiben eines Artikels (im Gegensatz zu Referenzinhalt) sollte die erste Instanz eines Cmdlet-Namens ein Link zur Cmdlet-Dokumentation sein</span><span class="sxs-lookup"><span data-stu-id="9b968-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="9b968-115">Alle Blöcke der PowerShell-Syntax sollten &#96;&#96;&#96;powershell verwenden</span><span class="sxs-lookup"><span data-stu-id="9b968-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="9b968-116">Starten Sie PowerShell-Befehle nicht mit „`PS C:\>`“</span><span class="sxs-lookup"><span data-stu-id="9b968-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="9b968-117">Richtiges Beispiel:</span><span class="sxs-lookup"><span data-stu-id="9b968-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="9b968-118">Falsches Beispiel:</span><span class="sxs-lookup"><span data-stu-id="9b968-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="9b968-119">Ausgabe, die von PowerShell-Befehlen ausgegeben wurde, sollte kommentiert werden, um sie am Empfangen von Syntaxhervorhebung zu hindern</span><span class="sxs-lookup"><span data-stu-id="9b968-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="9b968-120">Eigenschaftsnamen und Parameternamen sollten **fett** geschrieben werden</span><span class="sxs-lookup"><span data-stu-id="9b968-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="9b968-121">PowerShell-Cmdlets haben die [Pascal-Schreibweise](https://en.wikipedia.org/wiki/PascalCase).</span><span class="sxs-lookup"><span data-stu-id="9b968-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="9b968-122">Verben sind durch einen Bindestrich von Substantiven getrennt.</span><span class="sxs-lookup"><span data-stu-id="9b968-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="9b968-123">Listen</span><span class="sxs-lookup"><span data-stu-id="9b968-123">Lists</span></span>

* <span data-ttu-id="9b968-124">Beenden Sie Listenelemente nicht mit einem Punkt (sofern sie nicht mehrere Sätze enthalten)</span><span class="sxs-lookup"><span data-stu-id="9b968-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="9b968-125">Wenn Ihre Liste mehrere Sätze enthält, erwägen Sie die Verwendung eines Header 3/4/5 (falls zutreffend) unter Ihrer primären Idee</span><span class="sxs-lookup"><span data-stu-id="9b968-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="9b968-126">Links</span><span class="sxs-lookup"><span data-stu-id="9b968-126">Links</span></span>

* <span data-ttu-id="9b968-127">Links werden immer mit MarkDown-Syntax `[friendlyname](url)` gekennzeichnet</span><span class="sxs-lookup"><span data-stu-id="9b968-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="9b968-128">Links sollten einen Anzeigenamen haben, falls zutreffend, am besten den Titel der verknüpften Seite</span><span class="sxs-lookup"><span data-stu-id="9b968-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="9b968-129">**Ausnahme**: Links zu Seiten, die nicht von Microsoft stammen, sollten nur eine URL enthalten</span><span class="sxs-lookup"><span data-stu-id="9b968-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="9b968-130">Alle Elemente im Abschnitt „Verwandte Links“ am unteren Rand sollten mit einem Link versehen sein.</span><span class="sxs-lookup"><span data-stu-id="9b968-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="9b968-131">Zeilenumbrüche</span><span class="sxs-lookup"><span data-stu-id="9b968-131">Line breaks</span></span>

* <span data-ttu-id="9b968-132">Sie müssen semantische Zeilenumbrüche einschließen</span><span class="sxs-lookup"><span data-stu-id="9b968-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="9b968-133">Sie sollten Zeilen auf 100 Zeichen einschränken (Element öffnen: Tools helfen uns dies zu überprüfen).</span><span class="sxs-lookup"><span data-stu-id="9b968-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="9b968-134">Sie können zusätzliche Zeilenumbrüche für PS4+ entfernen, aber NICHT für ps3 (Überprüfung erforderlich)</span><span class="sxs-lookup"><span data-stu-id="9b968-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
