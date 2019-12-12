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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361269"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einem Windows PowerShell-® Cmdlet-Hilfethema einen Abschnitt Notizen hinzufügen. Der Abschnitt "Notizen" wird verwendet, um Details zu erläutern, die nicht problemlos in die anderen strukturierten Abschnitte passen, wie z. b. eine ausführlichere Erläuterung eines Parameters. Dieser Inhalt kann Kommentare dazu enthalten, wie das Cmdlet mit einem bestimmten Anbieter funktioniert, einige eindeutige, aber wichtige Verwendungsmöglichkeiten des Cmdlets oder Möglichkeiten, mögliche Fehlerbedingungen zu vermeiden.

Es gibt keine Beschränkung für die Anzahl von Notizen, die Sie zu einem Abschnitt mit Hinweisen hinzufügen können. Fügen Sie für jeden Hinweis dem Knoten \<MAML: alertset > ein paar \<MAML: Alert > Tags hinzu. Der Inhalt der einzelnen Notiz wird innerhalb einer Gruppe von \<MAML: para >-Tags hinzugefügt. Verwenden Sie leere \<MAML: para > Tags für den Abstand.

Der folgende XML-Code zeigt einen \<MAML: alertset-> Knoten mit zwei Notizen. Beachten Sie, dass jede Notiz über einen optionalen \<MAML: Title > Tag verfügt (Titel können zum Gruppieren beliebiger \<MAML: Alert > Tags verwendet werden) und dass jede Notiz eine leere Zeile nach dem Inhalt für den Abstand hat.

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



