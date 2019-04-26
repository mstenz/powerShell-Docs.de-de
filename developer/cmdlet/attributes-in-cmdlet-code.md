---
title: Attribute in der Cmdlet-Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068680"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="541ef-102">Attribute im Cmdlet-Code</span><span class="sxs-lookup"><span data-stu-id="541ef-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="541ef-103">Um die allgemeine Funktionalität von Windows PowerShell zu verwenden, werden die Klassen und die öffentlichen Eigenschaften, die definiert, in der Cmdlet-Code mit Attributen ergänzt.</span><span class="sxs-lookup"><span data-stu-id="541ef-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="541ef-104">Die folgende Klassendefinition verwendet beispielsweise das Cmdlet-Attribut zum Identifizieren von Microsoft .NET Framework-Klasse in der die **Get-Proc** Cmdlet implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="541ef-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="541ef-105">(Dieses Cmdlet wird in diesem Dokument als Beispiel verwendet und ist vergleichbar mit der `Get-Process` Cmdlet von Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="541ef-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="541ef-106">Diese Attribute werden als Metadaten betrachtet, da ihre Implementierung von der Implementierung von der Cmdlet-Code getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="541ef-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="541ef-107">Wenn die Windows PowerShell-Laufzeit das Cmdlet ausgeführt wird, erkennt die Attribute und führt dann die entsprechende Aktion für jedes Attribut.</span><span class="sxs-lookup"><span data-stu-id="541ef-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="541ef-108">Obwohl Sie möglicherweise Ihre eigene Version der durch diese Attribute bereitgestellten Funktionen implementieren möchten, wird ein gute Cmdlet-Entwurf diese allgemeine Funktionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="541ef-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="541ef-109">Weitere Informationen zu den verschiedenen Attributen, die in Ihre Cmdlets deklariert werden kann, finden Sie unter [Attributtypen](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="541ef-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="541ef-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="541ef-110">See Also</span></span>

[<span data-ttu-id="541ef-111">Typen von Attributen</span><span class="sxs-lookup"><span data-stu-id="541ef-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="541ef-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="541ef-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
