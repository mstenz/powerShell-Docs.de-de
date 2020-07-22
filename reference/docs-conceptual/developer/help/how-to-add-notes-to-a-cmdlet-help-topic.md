---
title: Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893406"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Hinzufügen von Anmerkungen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einem Hilfethema zu PowerShell-Cmdlets einen Abschnitt **Notizen** hinzufügen. Der Abschnitt " **Notizen** " wird verwendet, um Details zu erläutern, die nicht problemlos in die anderen strukturierten Abschnitte passen, wie z. b. eine ausführlichere Erläuterung eines Parameters. Dieser Inhalt kann Kommentare dazu enthalten, wie das Cmdlet mit einem bestimmten Anbieter funktioniert, einige eindeutige, aber wichtige Verwendungsmöglichkeiten des Cmdlets oder Möglichkeiten, mögliche Fehlerbedingungen zu vermeiden.

Es gibt keine Beschränkung für die Anzahl von Notizen, die Sie zu einem Abschnitt mit Hinweisen hinzufügen können. Fügen Sie für jeden Hinweis dem Knoten ein Tagpaar hinzu `<maml:alert>` `<maml:alertset>` . Der Inhalt der einzelnen Notiz wird in einem Satz von Tags hinzugefügt `<maml:para>` . Verwenden Sie leere `<maml:para>` Tags für den Abstand.

Der folgende XML-Code zeigt einen- `<maml:alertset>` Knoten mit zwei Notizen. Beachten Sie, dass jeder Hinweis über ein optionales `<maml:title>` Tag verfügt (Titel können verwendet werden, um beliebige Tags zu gruppieren `<maml:alert>` ) und dass jede Notiz eine leere Zeile nach dem Inhalt für den Abstand hat.

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
