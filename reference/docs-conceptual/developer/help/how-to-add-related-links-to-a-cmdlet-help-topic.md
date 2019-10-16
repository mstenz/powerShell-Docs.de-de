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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="daa8d-102">Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="daa8d-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="daa8d-103">In diesem Abschnitt wird beschrieben, wie Sie Verweise auf andere Inhalte hinzufügen, die sich auf ein Windows PowerShell-® Cmdlet-Hilfethema beziehen.</span><span class="sxs-lookup"><span data-stu-id="daa8d-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="daa8d-104">Da diese Verweise in einem Befehlsfenster angezeigt werden, werden Sie nicht direkt mit dem Inhalt verknüpft, auf den verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="daa8d-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="daa8d-105">In den Hilfe Themen zu Cmdlets, die in Windows PowerShell® enthalten sind, verweisen diese Links auf andere Cmdlets, konzeptionelle Inhalte ("About_") und andere Dokumente und Hilfedateien, die nicht mit Windows PowerShell-® verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="daa8d-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="daa8d-106">Der folgende XML-Code zeigt, wie Sie einen relatedLinks-Knoten hinzufügen, der zwei Verweise auf Verwandte Themen enthält.</span><span class="sxs-lookup"><span data-stu-id="daa8d-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



