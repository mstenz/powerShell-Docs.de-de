---
title: Attribute im Cmdlet-Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369999"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="befdb-102">Attribute im Cmdlet-Code</span><span class="sxs-lookup"><span data-stu-id="befdb-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="befdb-103">Um die von Windows PowerShell bereitgestellte allgemeine Funktionalität zu verwenden, werden die im Cmdlet-Code definierten Klassen und öffentlichen Eigenschaften mit Attributen versehen.</span><span class="sxs-lookup"><span data-stu-id="befdb-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="befdb-104">Die folgende Klassendefinition verwendet beispielsweise das Cmdlet-Attribut, um die Microsoft .NET Framework-Klasse zu identifizieren, in der das Cmdlet " **Get-proc** " implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="befdb-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="befdb-105">(Dieses Cmdlet wird in diesem Dokument als Beispiel verwendet und ähnelt dem Cmdlet "`Get-Process`", das von Windows PowerShell bereitgestellt wird.)</span><span class="sxs-lookup"><span data-stu-id="befdb-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="befdb-106">Diese Attribute werden als Metadaten betrachtet, da ihre Implementierung von der Implementierung des Cmdlet-Codes getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="befdb-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="befdb-107">Wenn das Cmdlet von der Windows PowerShell-Laufzeit ausgeführt wird, werden die Attribute erkannt und anschließend die entsprechende Aktion für jedes Attribut ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="befdb-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="befdb-108">Obwohl Sie möglicherweise Ihre eigene Version der Funktionalität implementieren möchten, die von diesen Attributen bereitgestellt wird, verwendet ein gutes Cmdlet-Design diese gemeinsamen Funktionen.</span><span class="sxs-lookup"><span data-stu-id="befdb-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="befdb-109">Weitere Informationen zu den verschiedenen Attributen, die in den Cmdlets deklariert werden können, finden Sie unter [Attributtypen](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="befdb-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="befdb-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="befdb-110">See Also</span></span>

[<span data-ttu-id="befdb-111">Attributtypen</span><span class="sxs-lookup"><span data-stu-id="befdb-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="befdb-112">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="befdb-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
