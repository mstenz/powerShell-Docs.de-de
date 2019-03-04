---
title: Unterstützung von Onlinehilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857916"
---
# <a name="supporting-online-help"></a><span data-ttu-id="3b59a-102">Unterstützung für Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="3b59a-102">Supporting Online Help</span></span>

<span data-ttu-id="3b59a-103">Ab Windows PowerShell 3.0 stehen zwei Methoden zur Unterstützung der `Get-Help` Online-Features für Windows PowerShell-Befehle.</span><span class="sxs-lookup"><span data-stu-id="3b59a-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="3b59a-104">In diesem Thema wird erläutert, wie Sie dieses Feature für unterschiedliche Befehlstypen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="3b59a-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="3b59a-105">Informationen zu Online-Hilfe</span><span class="sxs-lookup"><span data-stu-id="3b59a-105">About Online Help</span></span>

<span data-ttu-id="3b59a-106">Onlinehilfe war schon immer ein wesentlicher Bestandteil des Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b59a-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="3b59a-107">Obwohl die `Get-Help` Cmdlet zeigt die Hilfethemen an der Eingabeaufforderung an, die viele Benutzer bevorzugen die Erfahrung online zu lesen, einschließlich farbcodierung, links und Freigabe Ideen in Community-Inhalt und Wiki-basierten Dokumenten.</span><span class="sxs-lookup"><span data-stu-id="3b59a-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="3b59a-108">Wichtiger ist, wird vor der Einführung der aktualisierbaren Hilfe, online-Hilfe die aktuelle Version der Hilfedateien bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="3b59a-109">Mit dem Aufkommen der aktualisierbaren Hilfe in Windows PowerShell 3.0 spielt die Onlinehilfe weiterhin eine wichtige Rolle.</span><span class="sxs-lookup"><span data-stu-id="3b59a-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="3b59a-110">Zusätzlich zu den flexibler Installationsoptionen enthält die Onlinehilfe zu Hilfe für Benutzer, die nicht oder können keine aktualisierbare Hilfe zum Herunterladen der Hilfethemen.</span><span class="sxs-lookup"><span data-stu-id="3b59a-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="3b59a-111">Wie Get-Help-Online funktioniert</span><span class="sxs-lookup"><span data-stu-id="3b59a-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="3b59a-112">Für Benutzer finden Sie die online-Hilfethemen für Befehle, die `Get-Help` Befehl verfügt über einen Parameter "Online", das die Onlineversion des Hilfethemas für einen Befehl im Standardinternetbrowser des Benutzers geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="3b59a-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="3b59a-113">Zum Beispiel der folgende Befehl für das Onlinehilfethema öffnet die `Invoke-Command` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b59a-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="3b59a-114">Zum Implementieren `Get-Help` -Online, die `Get-Help` Cmdlet sucht für einen Uniform Resource Identifier (URI) für das Hilfethema für online-Version in den folgenden Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="3b59a-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="3b59a-115">Der erste Link im Abschnitt "Verwandte Links" des Hilfethemas für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="3b59a-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="3b59a-116">Das Hilfethema muss auf dem Computer des Benutzers installiert werden.</span><span class="sxs-lookup"><span data-stu-id="3b59a-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="3b59a-117">Dieses Feature wurde in Windows PowerShell 2.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="3b59a-118">Der "HelpUri"-Eigenschaft von einem der Befehle.</span><span class="sxs-lookup"><span data-stu-id="3b59a-118">The HelpUri property of any command.</span></span> <span data-ttu-id="3b59a-119">Der "HelpUri"-Eigenschaft wird zugegriffen werden kann, selbst wenn das Hilfethema für den Befehl nicht auf dem Computer des Benutzers installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3b59a-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="3b59a-120">Dieses Feature wurde in Windows PowerShell 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="3b59a-121">`Get-Help` Sucht für einen URI in den ersten Eintrag in "Verwandte Links" vor dem Abrufen des HelpUri-Eigenschaftswert.</span><span class="sxs-lookup"><span data-stu-id="3b59a-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="3b59a-122">Wenn der Wert der Eigenschaft falsch ist oder geändert wurde, können Sie es überschreiben, indem Sie einen anderen Wert eingeben, in dem ersten dazugehörigen Link.</span><span class="sxs-lookup"><span data-stu-id="3b59a-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="3b59a-123">Dem ersten dazugehörigen Link funktioniert jedoch nur, wenn die Hilfethemen auf dem Computer des Benutzers installiert sind.</span><span class="sxs-lookup"><span data-stu-id="3b59a-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="3b59a-124">Einen URI hinzufügen, der dem ersten dazugehörigen Link eines Hilfethemas für den Befehl</span><span class="sxs-lookup"><span data-stu-id="3b59a-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="3b59a-125">Sie können die unterstützen `Get-Help` -Online für jeden Befehl, indem Sie einen gültigen URI an den ersten Eintrag im Abschnitt "Verwandte Links" des XML-basierte Hilfethemas für den Befehl hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3b59a-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="3b59a-126">Diese Option ist nur in XML-basierte Hilfethemen und funktioniert nur, wenn das Hilfethema auf dem Computer des Benutzers installiert ist.</span><span class="sxs-lookup"><span data-stu-id="3b59a-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="3b59a-127">Wenn das Hilfethema installiert ist, und der URI wird aufgefüllt, dieser Wert hat Vorrang vor den **HelpUri** Eigenschaft des Befehls.</span><span class="sxs-lookup"><span data-stu-id="3b59a-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="3b59a-128">Weitere Informationen zu XML-Hilfethemen für Befehle, finden Sie unter [Writing XML-Based Hilfethemen zu Befehlen](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3b59a-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="3b59a-129">Um dieses Feature zu unterstützen, muss der URI in angezeigt werden die `maml:uri` Element unterhalb der ersten `maml:relatedLinks/maml:navigationLink` Element in der `maml:relatedLinks` Element.</span><span class="sxs-lookup"><span data-stu-id="3b59a-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="3b59a-130">Das folgende XML zeigt die korrekte Platzierung des URI.</span><span class="sxs-lookup"><span data-stu-id="3b59a-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="3b59a-131">Die "Online-Version:" Text in die `maml:linkText` Element ist eine bewährte Methode, aber es ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3b59a-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="3b59a-132">Der "HelpUri"-Eigenschaft hinzufügen auf einen Befehl</span><span class="sxs-lookup"><span data-stu-id="3b59a-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="3b59a-133">In diesem Abschnitt wird gezeigt, wie Befehle mit unterschiedlichen Typen der "HelpUri"-Eigenschaft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="3b59a-134">Hinzufügen einer HelpUri-Eigenschaft zu einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b59a-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="3b59a-135">Für Cmdlets, die in geschriebenen C#, Hinzufügen einer **HelpUri** -Attribut auf die Cmdlet-Klasse.</span><span class="sxs-lookup"><span data-stu-id="3b59a-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="3b59a-136">Der Wert des Attributs muss ein URI sein, die mit "http" oder "Https" beginnt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="3b59a-137">Der folgende Code zeigt das HelpUri-Attribut des der `Get-History` Cmdlet-Klasse.</span><span class="sxs-lookup"><span data-stu-id="3b59a-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="3b59a-138">Hinzufügen einer HelpUri-Eigenschaft eine erweiterte Funktion</span><span class="sxs-lookup"><span data-stu-id="3b59a-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="3b59a-139">Für erweiterte Funktionen Hinzufügen einer **HelpUri** Eigenschaft, um die **CmdletBinding** Attribut.</span><span class="sxs-lookup"><span data-stu-id="3b59a-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="3b59a-140">Der Wert der Eigenschaft muss ein URI sein, die mit "http" oder "Https" beginnt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="3b59a-141">Der folgende Code zeigt das HelpUri-Attribut der New-Calendar-Funktion</span><span class="sxs-lookup"><span data-stu-id="3b59a-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="3b59a-142">Hinzufügen eines HelpUri-Attributs zu einem CIM-Befehl</span><span class="sxs-lookup"><span data-stu-id="3b59a-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="3b59a-143">CIM-Befehle, Hinzufügen einer **HelpUri** -Attribut auf die **CmdletMetadata** Element in der CDXML-Datei.</span><span class="sxs-lookup"><span data-stu-id="3b59a-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="3b59a-144">Der Wert des Attributs muss ein URI sein, die mit "http" oder "Https" beginnt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="3b59a-145">Der folgende Code zeigt das HelpUri-Attribut des Start-Debug-CIM-Befehls</span><span class="sxs-lookup"><span data-stu-id="3b59a-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="3b59a-146">Hinzufügen eines HelpUri-Attributs zu einem Workflow</span><span class="sxs-lookup"><span data-stu-id="3b59a-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="3b59a-147">Für Workflows, die in der Windows PowerShell-Sprache geschrieben werden, Hinzufügen einer **. ExternalHelp** Comment-Anweisung an den Workflowcode.</span><span class="sxs-lookup"><span data-stu-id="3b59a-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="3b59a-148">Der Wert der Richtlinie muss ein URI sein, die mit "http" oder "Https" beginnt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="3b59a-149">Der "HelpUri"-Eigenschaft wird für XAML-basierten Workflows in Windows PowerShell nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3b59a-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="3b59a-150">Der folgende code zeigt die. ExternalHelp-Direktive in einer Workflowdatei.</span><span class="sxs-lookup"><span data-stu-id="3b59a-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```