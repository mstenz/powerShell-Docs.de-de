---
title: Hinzufügen verwandter Links zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361219"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie Verweise auf andere Inhalte hinzufügen, die sich auf ein Windows PowerShell-® Cmdlet-Hilfethema beziehen. Da diese Verweise in einem Befehlsfenster angezeigt werden, werden Sie nicht direkt mit dem Inhalt verknüpft, auf den verwiesen wird.

In den Hilfe Themen zu Cmdlets, die in Windows PowerShell® enthalten sind, verweisen diese Links auf andere Cmdlets, konzeptionelle Inhalte ("About_") und andere Dokumente und Hilfedateien, die nicht mit Windows PowerShell-® verknüpft sind.

Der folgende XML-Code zeigt, wie Sie einen relatedLinks-Knoten hinzufügen, der zwei Verweise auf Verwandte Themen enthält.

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



