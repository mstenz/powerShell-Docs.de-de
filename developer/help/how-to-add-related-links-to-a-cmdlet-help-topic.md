---
title: Hinzufügen von Links zu verwandten Themen zu einem Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855396"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema

Dieser Abschnitt beschreibt, wie Verweise auf andere Inhalte hinzufügen, die mit einem Windows PowerShell® Cmdlet-Hilfethema verknüpft ist. Da diese Verweise in einem Befehlsfenster angezeigt werden, verknüpfen sie nicht direkt auf den Inhalt auf die verwiesen wird.

In den Cmdlet-Hilfethemen, die in Windows PowerShell® enthalten sind, verweisen diesen Links, andere Cmdlets, die konzeptionellen Inhalt ("About_"), und andere Dokumente und die Hilfedateien, die nicht mit Windows PowerShell® verknüpft sind.

Das folgende XML zeigt, wie einen RelatedLinks-Knoten hinzugefügt, der zwei Verweise zu verwandten Themen enthält.

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



