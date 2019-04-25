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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083415"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie ein Cmdlet-Hilfethemas Windows PowerShell® einen Abschnitt "Hinweise" hinzugefügt. Im Abschnitt Hinweise werden erläutert, die leicht in andere strukturierte Abschnitte, z. B. eine ausführlichere Erläuterung der Parameter nicht passen. Dieser Inhalt kann enthalten, Kommentare zur Funktionsweise von des-Cmdlets mit einem bestimmten Anbieter, einige eindeutige noch wichtiger ist, verwendet das Cmdlet, oder die Möglichkeiten, mögliche fehlerbedingungen zu vermeiden.

Es gibt keine Beschränkungen auf die Anzahl der Anmerkungen zu dieser Version, die einen Abschnitt "Hinweise" hinzugefügt werden können. Fügen Sie für jede Beachten Sie, ein Paar von \<Maml:alert > tags zu den \<Maml:alertset > Knoten. Der Inhalt jeder Notiz wird hinzugefügt, in einer Gruppe von \<maml: para > Tags. Verwenden von leeren \<maml: para > Tags für die Analyse.

Das folgende XML zeigt ein \<Maml:alertset >-Knoten mit zwei Anmerkungen zu dieser Version. Beachten Sie, dass jeder Notiz ein optionales \<maml: Title >-Tag (Titel können verwendet werden, um eine beliebige Anzahl von gruppieren \<Maml:alert > Tags), und dass jeder Notiz eine leere Zeile, die nach dem Inhalt um den Abstand verfügt.

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



