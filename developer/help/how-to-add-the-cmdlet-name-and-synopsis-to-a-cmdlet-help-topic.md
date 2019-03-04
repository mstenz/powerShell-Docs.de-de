---
title: Hinzufügen von der Cmdlet-Namen und eine Zusammenfassung zu einer Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861826"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="a5700-102">Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="a5700-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a5700-103">Dieser Abschnitt beschreibt, wie Sie Inhalte hinzufügen, die in den Abschnitten "NAME" und "Zusammenfassung" der Cmdlet-Hilfe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a5700-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="a5700-104">Dieser Inhalt wird in der Hilfedatei befehlsknoten für jedes Cmdlet hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5700-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="a5700-105">Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden.</span><span class="sxs-lookup"><span data-stu-id="a5700-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="a5700-106">Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a5700-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="a5700-107">Cmdlet-Namen und eine Zusammenfassung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="a5700-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="a5700-108">Die Cmdlet-Hilfe kann es sich um zwei Beschreibungen für das-Cmdlet anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a5700-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="a5700-109">Die erste Beschreibung ist eine kurze Beschreibung, die als die Zusammenfassung bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="a5700-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="a5700-110">Die zweite Beschreibung wird eine ausführlichere Beschreibung, die hier erörtert wird [hinzufügen die ausführliche Beschreibung zu einem Cmdlet-Hilfethemas](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="a5700-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="a5700-111">Sowohl diese Beschreibungen sollte als einen einzelnen Absatz geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="a5700-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="a5700-112">Wiederholen Sie in der Zusammenfassung nicht den Cmdlet-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="a5700-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="a5700-113">Den Benutzer darüber informiert, dass das Cmdlet Get-Server auf einen Server ruft ist kurz, aber nicht informativ.</span><span class="sxs-lookup"><span data-stu-id="a5700-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="a5700-114">Stattdessen verwenden Sie die Synonyme und Hinzufügen von Details zu die Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="a5700-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="a5700-115">Beispiel: "Ruft ein Objekt, das einen lokalen Computer oder Remotecomputer darstellt."</span><span class="sxs-lookup"><span data-stu-id="a5700-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="a5700-116">Verwenden Sie einfache Verben wie "get", "erstellen" und "ändern" aus, in der Zusammenfassung.</span><span class="sxs-lookup"><span data-stu-id="a5700-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="a5700-117">Vermeiden Sie "set" da vage ist, und mit Effekten Wörter wie "ändern."</span><span class="sxs-lookup"><span data-stu-id="a5700-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="a5700-118">Beispiel: "Ruft Informationen über die Authenticode-Signatur in einer Datei."</span><span class="sxs-lookup"><span data-stu-id="a5700-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="a5700-119">Im aktiv geschrieben.</span><span class="sxs-lookup"><span data-stu-id="a5700-119">Write in active voice.</span></span> <span data-ttu-id="a5700-120">Zum Beispiel "verwenden das TimeSpan-Objekt..." ist viel klarer als "das TimeSpan-Objekt, verwendet werden kann..."</span><span class="sxs-lookup"><span data-stu-id="a5700-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="a5700-121">Vermeiden Sie das Verb "Display" aus, wenn die Cmdlets, die beschreibt, die Objekte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a5700-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="a5700-122">Obwohl Windows PowerShell Cmdlet Daten angezeigt wird, ist es wichtig, Computerbenutzer in das Konzept eingeführt, die mit dem Cmdlet die .NET Framework-Objekte zurückgegeben, deren Daten nicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="a5700-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="a5700-123">Wenn Sie die Anzeige zu verdeutlichen, kann der Benutzer nicht beachten Sie, dass möglicherweise mit dem-Cmdlet zurückgegeben wurden, viele andere nützliche Eigenschaften und Methoden, die nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a5700-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5700-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a5700-124">See Also</span></span>

 [<span data-ttu-id="a5700-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a5700-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)