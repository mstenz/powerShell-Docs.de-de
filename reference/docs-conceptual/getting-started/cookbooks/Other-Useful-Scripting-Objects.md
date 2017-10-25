---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Andere nützliche Skriptobjekte"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="db5a4-103">Andere nützliche Skriptobjekte</span><span class="sxs-lookup"><span data-stu-id="db5a4-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="db5a4-104">Die folgenden Objekte bieten zusätzliche Skriptfunktionalität in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="db5a4-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="db5a4-105">Sie sind nicht Teil der **$psISE**-Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="db5a4-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="db5a4-106">Nützliche Skriptobjekte</span><span class="sxs-lookup"><span data-stu-id="db5a4-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="db5a4-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="db5a4-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="db5a4-108">Es gibt einige Einschränkungen für die Interaktion von Windows PowerShell ISE mit Konsolenanwendungen.</span><span class="sxs-lookup"><span data-stu-id="db5a4-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="db5a4-109">Ein Befehl oder ein Automatisierungsskript, das einen Benutzereingriff erfordert, funktioniert möglicherweise anders, als wenn es von der Windows PowerShell-Konsole aus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="db5a4-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="db5a4-110">Möglicherweise wollen Sie die Ausführung dieser Skripts oder Befehle im Befehlsbereich von Windows PowerShell ISE sperren.</span><span class="sxs-lookup"><span data-stu-id="db5a4-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="db5a4-111">Das Objekt **$psUnsupportedConsoleApplications** hält eine Liste solcher Befehle vor.</span><span class="sxs-lookup"><span data-stu-id="db5a4-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="db5a4-112">Falls Sie versuchen, die Befehle in dieser Liste auszuführen, erhalten Sie die Meldung, dass sie nicht unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="db5a4-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="db5a4-113">Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="db5a4-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="db5a4-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="db5a4-114">$psLocalHelp</span></span>
 <span data-ttu-id="db5a4-115">Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen Hilfethemen und den entsprechenden Links in der lokalen kompilierten HTML-Hilfedatei verwaltet.</span><span class="sxs-lookup"><span data-stu-id="db5a4-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="db5a4-116">Es wird bei der Suche der lokalen Hilfe für ein bestimmtes Thema verwendet.</span><span class="sxs-lookup"><span data-stu-id="db5a4-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="db5a4-117">Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen.</span><span class="sxs-lookup"><span data-stu-id="db5a4-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="db5a4-118">Das folgende Codebeispiel zeigt einige Beispiele für Schlüssel-Wert-Paare, die in **$psLocalHelp**enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="db5a4-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="db5a4-119">Beispielausgabe</span><span class="sxs-lookup"><span data-stu-id="db5a4-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="db5a4-120">Key : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="db5a4-120">Key : Add-Computer</span></span>|<span data-ttu-id="db5a4-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="db5a4-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="db5a4-122">Key : Add-Content</span><span class="sxs-lookup"><span data-stu-id="db5a4-122">Key : Add-Content</span></span>|<span data-ttu-id="db5a4-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="db5a4-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="db5a4-124">Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="db5a4-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="db5a4-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="db5a4-125">$psOnlineHelp</span></span>
 <span data-ttu-id="db5a4-126">Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen den Titeln der Hilfethemen und den entsprechenden externen URLs verwaltet.</span><span class="sxs-lookup"><span data-stu-id="db5a4-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="db5a4-127">Es wird verwendet, um die Hilfe für ein bestimmtes Thema im Web zu finden.</span><span class="sxs-lookup"><span data-stu-id="db5a4-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="db5a4-128">Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen.</span><span class="sxs-lookup"><span data-stu-id="db5a4-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="db5a4-129">Beispielausgabe</span><span class="sxs-lookup"><span data-stu-id="db5a4-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="db5a4-130">Key : Add-Computer</span><span class="sxs-lookup"><span data-stu-id="db5a4-130">Key : Add-Computer</span></span>|<span data-ttu-id="db5a4-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="db5a4-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="db5a4-132">Key : Add-Content</span><span class="sxs-lookup"><span data-stu-id="db5a4-132">Key : Add-Content</span></span>|<span data-ttu-id="db5a4-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="db5a4-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="db5a4-134">Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="db5a4-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="db5a4-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="db5a4-135">See Also</span></span>
- [<span data-ttu-id="db5a4-136">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="db5a4-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
