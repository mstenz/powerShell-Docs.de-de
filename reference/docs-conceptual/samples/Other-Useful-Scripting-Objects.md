---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andere nützliche Skriptobjekte
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325159"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="9c3ec-103">Andere nützliche Skriptobjekte</span><span class="sxs-lookup"><span data-stu-id="9c3ec-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="9c3ec-104">Die folgenden Objekte bieten zusätzliche Skriptfunktionalität in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="9c3ec-105">Sie sind nicht Teil der **$psISE**-Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="9c3ec-106">Nützliche Skriptobjekte</span><span class="sxs-lookup"><span data-stu-id="9c3ec-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="9c3ec-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="9c3ec-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="9c3ec-108">Es gibt einige Einschränkungen für die Interaktion von Windows PowerShell ISE mit Konsolenanwendungen.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="9c3ec-109">Ein Befehl oder ein Automatisierungsskript, das einen Benutzereingriff erfordert, funktioniert möglicherweise anders, als wenn es von der Windows PowerShell-Konsole aus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="9c3ec-110">Möglicherweise wollen Sie die Ausführung dieser Skripts oder Befehle im Befehlsbereich von Windows PowerShell ISE sperren.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="9c3ec-111">Das Objekt **$psUnsupportedConsoleApplications** hält eine Liste solcher Befehle vor.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="9c3ec-112">Falls Sie versuchen, die Befehle in dieser Liste auszuführen, erhalten Sie die Meldung, dass sie nicht unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="9c3ec-113">Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="9c3ec-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="9c3ec-114">$psLocalHelp</span></span>

<span data-ttu-id="9c3ec-115">Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen Hilfethemen und den entsprechenden Links in der lokalen kompilierten HTML-Hilfedatei verwaltet.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="9c3ec-116">Es wird bei der Suche der lokalen Hilfe für ein bestimmtes Thema verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="9c3ec-117">Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="9c3ec-118">Das folgende Codebeispiel zeigt einige Beispiele für Schlüssel-Wert-Paare, die in `$psLocalHelp` enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="9c3ec-119">Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="9c3ec-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="9c3ec-120">$psOnlineHelp</span></span>

<span data-ttu-id="9c3ec-121">Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen den Titeln der Hilfethemen und den entsprechenden externen URLs verwaltet.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="9c3ec-122">Es wird verwendet, um die Hilfe für ein bestimmtes Thema im Web zu finden.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="9c3ec-123">Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="9c3ec-124">Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.</span><span class="sxs-lookup"><span data-stu-id="9c3ec-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="9c3ec-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9c3ec-125">See Also</span></span>

[<span data-ttu-id="9c3ec-126">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="9c3ec-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
