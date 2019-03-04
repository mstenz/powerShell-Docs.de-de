---
title: Deklarieren von Eigenschaften, die als Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861376"
---
# <a name="declaring-properties-as-parameters"></a>Deklarieren von Eigenschaften als Parameter

Dieses Thema enthält grundlegende Informationen, die Sie verstehen müssen, bevor Sie mit die Parametern eines Cmdlets deklarieren.

Um den Parametern eines Cmdlets in der Cmdlet-Klasse zu deklarieren, definieren Sie die öffentlichen Eigenschaften, die jeden Parameter darstellen, und fügen Sie dann auf jede Eigenschaft eine oder mehrere Parameter-Attribute hinzu. Die Windows PowerShell-Laufzeit verwendet die Parameterattribute bezeichnen die Eigenschaft als Cmdlet-Parameter. Die grundlegende Syntax zum Deklarieren der Parameter-Attribut ist `[Parameter()]`.

Hier ist ein Beispiel für eine Eigenschaft, die als ein erforderlicher Parameter definiert.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Hier sind einige wichtige Aspekte für Informationen zu Parametern.

- Parameter muss explizit als öffentlich markiert werden. Parameter, die nicht als öffentlicher Standard auf interne gekennzeichnet sind, und werden von der Windows PowerShell-Laufzeit nicht gefunden werden.

- Parameter müssen als Microsoft .NET Framework-Typen zu besseren parametervalidierung definiert sein. Beispielsweise sollten Parameter, die auf einen Wert aus dem Satz von Werten beschränkt sind, als ein Enumerationstyp definiert werden. Parameter, die einen Uniform Resource Identifier (URI)-Wert akzeptieren muss vom Typ [System.Uri](/dotnet/api/System.Uri).

- Vermeiden Sie die allgemeine Zeichenfolgen-Parameter für alle außer Freitext-Eigenschaften.

- Sie können einen Parameter an eine beliebige Anzahl von Parametersätzen hinzufügen. Weitere Informationen zu Parametersätze, finden Sie unter [Cmdlet Parametersätze](./cmdlet-parameter-sets.md).

Windows PowerShell bietet auch einen Satz von allgemeinen Parametern, die automatisch für jedes Cmdlet verfügbar sind. Weitere Informationen zu diesen Parametern und ihre Aliase finden Sie unter [allgemeinen Cmdlet-Parameter](./common-parameter-names.md).

## <a name="see-also"></a>Weitere Informationen

[-Cmdlet allgemeine Parameter](./common-parameter-names.md)

[Typen von Cmdlet-Parameter](./types-of-cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
