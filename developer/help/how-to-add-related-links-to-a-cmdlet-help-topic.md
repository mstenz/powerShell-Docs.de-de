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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083344"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="f5d0d-102">Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="f5d0d-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="f5d0d-103">Dieser Abschnitt beschreibt, wie Verweise auf andere Inhalte hinzufügen, die mit einem Windows PowerShell® Cmdlet-Hilfethema verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="f5d0d-104">Da diese Verweise in einem Befehlsfenster angezeigt werden, verknüpfen sie nicht direkt auf den Inhalt auf die verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="f5d0d-105">In den Cmdlet-Hilfethemen, die in Windows PowerShell® enthalten sind, verweisen diesen Links, andere Cmdlets, die konzeptionellen Inhalt ("About_"), und andere Dokumente und die Hilfedateien, die nicht mit Windows PowerShell® verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="f5d0d-106">Das folgende XML zeigt, wie einen RelatedLinks-Knoten hinzugefügt, der zwei Verweise zu verwandten Themen enthält.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



