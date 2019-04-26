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
# <a name="attributes-in-cmdlet-code"></a>Attribute im Cmdlet-Code

Um die allgemeine Funktionalität von Windows PowerShell zu verwenden, werden die Klassen und die öffentlichen Eigenschaften, die definiert, in der Cmdlet-Code mit Attributen ergänzt. Die folgende Klassendefinition verwendet beispielsweise das Cmdlet-Attribut zum Identifizieren von Microsoft .NET Framework-Klasse in der die **Get-Proc** Cmdlet implementiert wird. (Dieses Cmdlet wird in diesem Dokument als Beispiel verwendet und ist vergleichbar mit der `Get-Process` Cmdlet von Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Diese Attribute werden als Metadaten betrachtet, da ihre Implementierung von der Implementierung von der Cmdlet-Code getrennt ist. Wenn die Windows PowerShell-Laufzeit das Cmdlet ausgeführt wird, erkennt die Attribute und führt dann die entsprechende Aktion für jedes Attribut.

Obwohl Sie möglicherweise Ihre eigene Version der durch diese Attribute bereitgestellten Funktionen implementieren möchten, wird ein gute Cmdlet-Entwurf diese allgemeine Funktionen verwendet.

Weitere Informationen zu den verschiedenen Attributen, die in Ihre Cmdlets deklariert werden kann, finden Sie unter [Attributtypen](./attribute-types.md).

## <a name="see-also"></a>Weitere Informationen

[Typen von Attributen](./attribute-types.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
