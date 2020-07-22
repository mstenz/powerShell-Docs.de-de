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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="87349-102">Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="87349-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="87349-103">In diesem Abschnitt wird beschrieben, wie Sie Verweise auf andere Inhalte hinzufügen, die mit einem Hilfethema für PowerShell-Cmdlets verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="87349-103">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="87349-104">Da diese Verweise in einem Befehlsfenster angezeigt werden, werden Sie nicht direkt mit dem Inhalt verknüpft, auf den verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="87349-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="87349-105">In den Hilfe Themen zu Cmdlets, die in PowerShell enthalten sind, verweisen diese Links auf andere Cmdlets, konzeptionelle Inhalte ( `about_` ) und andere Dokumente und Hilfedateien, die nicht mit PowerShell verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="87349-105">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="87349-106">Der folgende XML-Code zeigt, wie Sie einen **relatedLinks** -Knoten hinzufügen, der zwei Verweise auf Verwandte Themen enthält.</span><span class="sxs-lookup"><span data-stu-id="87349-106">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

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
