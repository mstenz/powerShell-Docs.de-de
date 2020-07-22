---
title: Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema
ms.date: 09/12/2016
ms.openlocfilehash: 7557b3856d8470434070dd286cd7e30c9ba015c5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893372"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie Verweise auf andere Inhalte hinzufügen, die mit einem Hilfethema für PowerShell-Cmdlets verknüpft sind. Da diese Verweise in einem Befehlsfenster angezeigt werden, werden Sie nicht direkt mit dem Inhalt verknüpft, auf den verwiesen wird.

In den Hilfe Themen zu Cmdlets, die in PowerShell enthalten sind, verweisen diese Links auf andere Cmdlets, konzeptionelle Inhalte ( `about_` ) und andere Dokumente und Hilfedateien, die nicht mit PowerShell verknüpft sind.

Der folgende XML-Code zeigt, wie Sie einen **relatedLinks** -Knoten hinzufügen, der zwei Verweise auf Verwandte Themen enthält.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```
