---
title: Vorgehensweise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361269"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="7fabc-102">Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="7fabc-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7fabc-103">In diesem Abschnitt wird beschrieben, wie Sie einem Windows PowerShell-® Cmdlet-Hilfethema einen Abschnitt Notizen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7fabc-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7fabc-104">Der Abschnitt "Notizen" wird verwendet, um Details zu erläutern, die nicht problemlos in die anderen strukturierten Abschnitte passen, wie z. b. eine ausführlichere Erläuterung eines Parameters.</span><span class="sxs-lookup"><span data-stu-id="7fabc-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="7fabc-105">Dieser Inhalt kann Kommentare dazu enthalten, wie das Cmdlet mit einem bestimmten Anbieter funktioniert, einige eindeutige, aber wichtige Verwendungsmöglichkeiten des Cmdlets oder Möglichkeiten, mögliche Fehlerbedingungen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="7fabc-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="7fabc-106">Es gibt keine Beschränkung für die Anzahl von Notizen, die Sie zu einem Abschnitt mit Hinweisen hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="7fabc-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="7fabc-107">Fügen Sie für jeden Hinweis dem Knoten \<maml: alertset > ein paar von \<maml: Alert > Tags hinzu.</span><span class="sxs-lookup"><span data-stu-id="7fabc-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="7fabc-108">Der Inhalt der einzelnen Notiz wird innerhalb eines Satzes von \<maml: para > Tags hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7fabc-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="7fabc-109">Verwenden Sie leere \<maml: para > Tags für den Abstand.</span><span class="sxs-lookup"><span data-stu-id="7fabc-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="7fabc-110">Der folgende XML-Code zeigt einen \<maml: alertset-> Knoten mit zwei Notizen.</span><span class="sxs-lookup"><span data-stu-id="7fabc-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="7fabc-111">Beachten Sie, dass jeder Hinweis über einen optionalen \<maml: Title > Tag verfügt (Titel können verwendet werden, um einen beliebigen Satz von \<maml: Alert > Tags zu gruppieren) und dass jede Notiz eine leere Zeile nach dem Inhalt für den Abstand enthält.</span><span class="sxs-lookup"><span data-stu-id="7fabc-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



