---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShell-Skripterstellung
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094050"
---
# <a name="powershell"></a><span data-ttu-id="66ce0-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="66ce0-103">PowerShell</span></span>

<span data-ttu-id="66ce0-104">PowerShell basiert auf dem .NET Framework und ist eine aufgabenbasierte Befehlszeilenshell und Skriptsprache. Sie wurde speziell für Administratoren und Poweruser entworfen, um das Verwalten von mehreren Betriebssystemen (Linux, macOS, Unix und Windows) und die anwendungsbezogenen Prozesse auf diesen Betriebssystemen schnell zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="66ce0-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="66ce0-105">PowerShell ist Open Source</span><span class="sxs-lookup"><span data-stu-id="66ce0-105">PowerShell is open source</span></span>

<span data-ttu-id="66ce0-106">Der grundlegende PowerShell-Quellcode ist jetzt auf GitHub verfügbar und für Community-Beiträge offen.</span><span class="sxs-lookup"><span data-stu-id="66ce0-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="66ce0-107">Informationen dazu finden Sie unter [PowerShell-Quellcode auf GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="66ce0-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="66ce0-108">Sie können sich alles Notwendige [hier](https://github.com/PowerShell/PowerShell#get-powershell) im Abschnitt „Get PowerShell“ (PowerShell herunterladen) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="66ce0-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="66ce0-109">Beginnen Sie alternativ mit einer kurzen Einführung unter [Getting Started (Erste Schritte)](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="66ce0-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="66ce0-110">PowerShell-Entwurfsziele</span><span class="sxs-lookup"><span data-stu-id="66ce0-110">PowerShell design goals</span></span>
<span data-ttu-id="66ce0-111">PowerShell soll Befehlszeilen- und Skriptumgebungen verbessern. Es beseitigt lange bestehende Probleme und führt neue Features ein.</span><span class="sxs-lookup"><span data-stu-id="66ce0-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="66ce0-112">Erkennbarkeit</span><span class="sxs-lookup"><span data-stu-id="66ce0-112">Discoverability</span></span>
<span data-ttu-id="66ce0-113">Sie können sich leicht mit den Features in PowerShell vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="66ce0-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="66ce0-114">Um z. B. eine Liste von Cmdlets zu finden, die zum Anzeigen und Ändern von Windows-Diensten dienen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="66ce0-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="66ce0-115">Nachdem Sie ermittelt haben, welches Cmdlet welche Aufgabe erledigt, können Sie mithilfe des Cmdlets `Get-Help` mehr über das Cmdlet erfahren.</span><span class="sxs-lookup"><span data-stu-id="66ce0-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="66ce0-116">Geben Sie z.B. zum Anzeigen der Hilfe zum Cmdlet `Get-Service` Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="66ce0-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="66ce0-117">Die meisten Cmdlets geben Objekte aus, die bearbeitet und dann in Text für die Anzeige gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="66ce0-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="66ce0-118">Um die Ausgabe dieses Cmdlets vollständig zu verstehen, leiten Sie seine Ausgabe an das Cmdlet `Get-Member` weiter.</span><span class="sxs-lookup"><span data-stu-id="66ce0-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="66ce0-119">Der folgende Befehl zeigt z.B. Informationen zu den Elementen des Objekts an, das vom Cmdlet `Get-Service` ausgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="66ce0-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="66ce0-120">Konsistenz</span><span class="sxs-lookup"><span data-stu-id="66ce0-120">Consistency</span></span>
<span data-ttu-id="66ce0-121">Das Verwalten von Systemen kann ein komplexer Vorgang sein, und Tools mit einer konsistenten Schnittstelle helfen, die inhärente Komplexität im Griff zu behalten.</span><span class="sxs-lookup"><span data-stu-id="66ce0-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="66ce0-122">Leider zeichnen sich weder Befehlszeilentools noch skriptfähige COM-Objekte durch ihre Konsistenz aus.</span><span class="sxs-lookup"><span data-stu-id="66ce0-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="66ce0-123">PowerShell besticht durch Konsistenz.</span><span class="sxs-lookup"><span data-stu-id="66ce0-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="66ce0-124">Wenn Sie z.B. gelernt haben, wie das Cmdlet `Sort-Object` verwendet wird, können Sie mit diesem Wissen die Ausgabe sämtlicher Cmdlets sortieren.</span><span class="sxs-lookup"><span data-stu-id="66ce0-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="66ce0-125">Sie müssen also nicht für jedes Cmdlet eine andere Sortierroutine erlernen.</span><span class="sxs-lookup"><span data-stu-id="66ce0-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="66ce0-126">Darüber hinaus müssen Cmdlet-Entwickler keine Sortierfunktionen für ihre Cmdlets entwerfen.</span><span class="sxs-lookup"><span data-stu-id="66ce0-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="66ce0-127">PowerShell bietet ihnen ein Framework, das grundlegende Funktionen bereitstellt und Konsistenz bei vielen Aspekten der Schnittstelle erzwingt.</span><span class="sxs-lookup"><span data-stu-id="66ce0-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="66ce0-128">Das Framework bietet nicht mehr einige der Wahlmöglichkeiten, die normalerweise dem Entwickler überlassen werden, vereinfacht aber im Gegenzug die Entwicklung zuverlässiger und benutzerfreundlicher Cmdlets wesentlich.</span><span class="sxs-lookup"><span data-stu-id="66ce0-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="66ce0-129">Interaktive und Skriptumgebung</span><span class="sxs-lookup"><span data-stu-id="66ce0-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="66ce0-130">PowerShell ist sowohl eine interaktive Umgebung als auch eine Skriptumgebung, die Zugriff auf Befehlszeilentools und COM-Objekte bietet, mit der Sie von der Leistungsfähigkeit der .NET Framework Class Library (FCL) profitieren können.</span><span class="sxs-lookup"><span data-stu-id="66ce0-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="66ce0-131">Diese Umgebung verbessert die Windows-Eingabeaufforderung, die eine interaktive Umgebung mit mehreren Befehlszeilentools bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="66ce0-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="66ce0-132">Sie verbessert auch WSH-Skripts (Windows Script Host), mit denen Sie können mehrere Befehlszeilentools und COM-Automatisierungsobjekte verwenden können, die aber keine interaktive Umgebung bieten.</span><span class="sxs-lookup"><span data-stu-id="66ce0-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="66ce0-133">Durch die Kombination dieser Features erweitert PowerShell die Möglichkeiten des interaktiven Benutzers und Skripterstellers und vereinfacht die Systemverwaltung.</span><span class="sxs-lookup"><span data-stu-id="66ce0-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="66ce0-134">Objektorientierung</span><span class="sxs-lookup"><span data-stu-id="66ce0-134">Object Orientation</span></span>
<span data-ttu-id="66ce0-135">Obwohl Sie mit PowerShell interagieren, indem Sie Befehle als Text eingeben, ist PowerShell objekt- und nicht textbasiert.</span><span class="sxs-lookup"><span data-stu-id="66ce0-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="66ce0-136">Die Ausgabe eines Befehls ist ein Objekt.</span><span class="sxs-lookup"><span data-stu-id="66ce0-136">The output of a command is an object.</span></span>
<span data-ttu-id="66ce0-137">Sie können das Ausgabeobjekt als Eingabe an einen anderen Befehl weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="66ce0-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="66ce0-138">Daher bietet PowerShell eine vertraute Schnittstelle für Personen, die mit anderen Shells vertraut sind, und führt gleichzeitig ein neues, leistungsstarkes Befehlszeilenmodell ein.</span><span class="sxs-lookup"><span data-stu-id="66ce0-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="66ce0-139">Das Konzept des Übermittelns von Daten zwischen Befehlen wird erweitert, indem Sie Objekte anstelle von Text übermitteln können.</span><span class="sxs-lookup"><span data-stu-id="66ce0-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="66ce0-140">Einfacher Übergang zur Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="66ce0-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="66ce0-141">PowerShell vereinfacht den Übergang von der interaktiven Eingabe von Befehlen zum Erstellen und Ausführen von Skripts.</span><span class="sxs-lookup"><span data-stu-id="66ce0-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="66ce0-142">Sie können Befehle an der PowerShell-Eingabeaufforderung eingeben, um die Befehle zu ermitteln, die eine Aufgabe ausführen.</span><span class="sxs-lookup"><span data-stu-id="66ce0-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="66ce0-143">Dann können Sie diese Befehle in einer Aufzeichnung oder einem Verlauf speichern, bevor Sie sie in eine Datei zur Verwendung als Skript kopieren.</span><span class="sxs-lookup"><span data-stu-id="66ce0-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
