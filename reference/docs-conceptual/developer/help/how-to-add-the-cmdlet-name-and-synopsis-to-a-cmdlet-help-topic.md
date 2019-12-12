---
title: Vorgehensweise beim Hinzufügen des Cmdlet-namens und der Synchronisierungs Datei zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361189"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="c3e1f-102">Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="c3e1f-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c3e1f-103">In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die in den Abschnitten "Name" und "Synopsis" der Cmdlet-Hilfe angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="c3e1f-104">In der Hilfedatei wird dieser Inhalt dem Befehls Knoten für jedes Cmdlet hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c3e1f-105">Eine umfassende Übersicht über eine Hilfedatei erhalten Sie, indem Sie eine der dll-Help. XML-Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="c3e1f-106">Beispielsweise enthält die Datei Microsoft. PowerShell. Commands. Management. dll-Help. XML Inhalte für mehrere der Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="c3e1f-107">So fügen Sie den Cmdlet-Namen und eine Synchronisierungs Datei hinzu</span><span class="sxs-lookup"><span data-stu-id="c3e1f-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="c3e1f-108">Die Cmdlet-Hilfe kann zwei Beschreibungen für das Cmdlet anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="c3e1f-109">Die erste Beschreibung ist eine kurze Beschreibung, die als Synopsis bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="c3e1f-110">Die zweite Beschreibung ist eine ausführlichere Beschreibung, die im [Thema Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md)erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="c3e1f-111">Beide Beschreibungen sollten als einzelner Absatz geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="c3e1f-112">Wiederholen Sie in der Synchronisierungs Datei den Namen des Cmdlets nicht.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="c3e1f-113">Der Benutzer wird darüber informiert, dass das Cmdlet "Get-Server" einen Server erhält, aber nicht informativ ist.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="c3e1f-114">Verwenden Sie stattdessen Synonyme, und fügen Sie der Beschreibung Details hinzu.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="c3e1f-115">Beispiel: "Ruft ein Objekt ab, das einen lokalen oder Remote Computer darstellt."</span><span class="sxs-lookup"><span data-stu-id="c3e1f-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="c3e1f-116">Verwenden Sie einfache Verben wie "Get", "Create" und "Change" in der Synchronisierungs Datei.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="c3e1f-117">Vermeiden Sie die Verwendung von "Set", da sie ungenau ist, und achten Sie auf die Verwendung von "ändern".</span><span class="sxs-lookup"><span data-stu-id="c3e1f-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="c3e1f-118">Beispiel: "Ruft Informationen über die Authenticode-Signatur in einer Datei ab."</span><span class="sxs-lookup"><span data-stu-id="c3e1f-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="c3e1f-119">Schreiben Sie in die aktive Sprache.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-119">Write in active voice.</span></span> <span data-ttu-id="c3e1f-120">Beispiel: "verwenden Sie das TimeSpan-Objekt..." ist viel klarer als "das TimeSpan-Objekt kann verwendet werden..."</span><span class="sxs-lookup"><span data-stu-id="c3e1f-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="c3e1f-121">Vermeiden Sie das Verb "Display", wenn Sie Cmdlets beschreiben, die Objekte erhalten.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="c3e1f-122">Obwohl in Windows PowerShell Cmdlet-Daten angezeigt werden, ist es wichtig, Benutzer zu dem Konzept zu bringen, das vom Cmdlet zurückgegeben wird, .NET Framework Objekte, deren Daten möglicherweise nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="c3e1f-123">Wenn Sie die Anzeige hervorheben, erkennt der Benutzer möglicherweise nicht, dass das Cmdlet möglicherweise viele andere nützliche Eigenschaften und Methoden zurückgegeben hat, die nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c3e1f-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3e1f-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c3e1f-124">See Also</span></span>

 [<span data-ttu-id="c3e1f-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c3e1f-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)