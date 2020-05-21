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
ms.openlocfilehash: 1a365a167c245006bb882a542aedb5c43cfc4c96
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557106"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einem Windows PowerShell-® Cmdlet-Hilfethema einen Abschnitt Notizen hinzufügen. Der Abschnitt "Notizen" wird verwendet, um Details zu erläutern, die nicht problemlos in die anderen strukturierten Abschnitte passen, wie z. b. eine ausführlichere Erläuterung eines Parameters. Dieser Inhalt kann Kommentare dazu enthalten, wie das Cmdlet mit einem bestimmten Anbieter funktioniert, einige eindeutige, aber wichtige Verwendungsmöglichkeiten des Cmdlets oder Möglichkeiten, mögliche Fehlerbedingungen zu vermeiden.

Es gibt keine Beschränkung für die Anzahl von Notizen, die Sie zu einem Abschnitt mit Hinweisen hinzufügen können. Fügen Sie für jeden Hinweis \< dem \< Knoten MAML: alertset> ein paar von MAML: Alert> Tags hinzu. Der Inhalt der einzelnen Notiz wird in einem Satz von \< MAML: para>-Tags hinzugefügt. Verwenden Sie leere \< MAML: para>-Tags für den Abstand.

Der folgende XML-Code zeigt einen \< MAML: alertset-> Knoten mit zwei Notizen. Beachten Sie, dass jeder Hinweis über einen optionalen \< MAML: Title-> Tag verfügt (Titel können verwendet werden, um einen beliebigen Satz von \< MAML: Alert> Tags zu gruppieren), und jede Notiz hat eine leere Zeile nach dem Inhalt für den Abstand.

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
