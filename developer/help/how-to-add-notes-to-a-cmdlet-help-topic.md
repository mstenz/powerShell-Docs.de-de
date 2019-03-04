---
title: Hinzufügen von Anmerkungen zu dieser zu einem Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862266"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="ed18a-102">Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="ed18a-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="ed18a-103">In diesem Abschnitt wird beschrieben, wie ein Cmdlet-Hilfethemas Windows PowerShell® einen Abschnitt "Hinweise" hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ed18a-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="ed18a-104">Im Abschnitt Hinweise werden erläutert, die leicht in andere strukturierte Abschnitte, z. B. eine ausführlichere Erläuterung der Parameter nicht passen.</span><span class="sxs-lookup"><span data-stu-id="ed18a-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="ed18a-105">Dieser Inhalt kann enthalten, Kommentare zur Funktionsweise von des-Cmdlets mit einem bestimmten Anbieter, einige eindeutige noch wichtiger ist, verwendet das Cmdlet, oder die Möglichkeiten, mögliche fehlerbedingungen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="ed18a-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="ed18a-106">Es gibt keine Beschränkungen auf die Anzahl der Anmerkungen zu dieser Version, die einen Abschnitt "Hinweise" hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="ed18a-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="ed18a-107">Fügen Sie für jede Beachten Sie, ein Paar von \<Maml:alert > tags zu den \<Maml:alertset > Knoten.</span><span class="sxs-lookup"><span data-stu-id="ed18a-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="ed18a-108">Der Inhalt jeder Notiz wird hinzugefügt, in einer Gruppe von \<maml: para > Tags.</span><span class="sxs-lookup"><span data-stu-id="ed18a-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="ed18a-109">Verwenden von leeren \<maml: para > Tags für die Analyse.</span><span class="sxs-lookup"><span data-stu-id="ed18a-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="ed18a-110">Das folgende XML zeigt ein \<Maml:alertset >-Knoten mit zwei Anmerkungen zu dieser Version.</span><span class="sxs-lookup"><span data-stu-id="ed18a-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="ed18a-111">Beachten Sie, dass jeder Notiz ein optionales \<maml: Title >-Tag (Titel können verwendet werden, um eine beliebige Anzahl von gruppieren \<Maml:alert > Tags), und dass jeder Notiz eine leere Zeile, die nach dem Inhalt um den Abstand verfügt.</span><span class="sxs-lookup"><span data-stu-id="ed18a-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



