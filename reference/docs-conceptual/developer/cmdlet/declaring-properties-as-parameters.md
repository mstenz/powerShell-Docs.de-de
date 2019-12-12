---
title: Deklarieren von Eigenschaften als Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365749"
---
# <a name="declaring-properties-as-parameters"></a>Deklarieren von Eigenschaften als Parameter

Dieses Thema enthält grundlegende Informationen, die Sie kennen müssen, bevor Sie die Parameter eines Cmdlets deklarieren.

Um die Parameter eines Cmdlets in der Cmdlet-Klasse zu deklarieren, definieren Sie die öffentlichen Eigenschaften, die die einzelnen Parameter darstellen, und fügen Sie jeder Eigenschaft ein oder mehrere Parameter Attribute hinzu. Die Windows PowerShell-Laufzeit verwendet die Parameter Attribute, um die Eigenschaft als Cmdlet-Parameter zu identifizieren. Die grundlegende Syntax zum Deklarieren des Parameter Attributs ist `[Parameter()]`.

Im folgenden finden Sie ein Beispiel für eine Eigenschaft, die als erforderlicher Parameter definiert ist.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Im folgenden finden Sie einige Dinge, die Sie über Parameter berücksichtigen sollten.

- Ein Parameter muss explizit als public gekennzeichnet werden. Parameter, die nicht als öffentlich gekennzeichnet sind, sind standardmäßig intern und werden von der Windows PowerShell-Laufzeit nicht gefunden.

- Parameter sollten als Microsoft .NET Frameworktypen definiert werden, um eine bessere Parameter Validierung bereitzustellen. Beispielsweise sollten Parameter, die auf einen Wert aus einer Menge von Werten beschränkt sind, als Enumerationstyp definiert werden. Parameter, die einen Uniform Resource Identifier-Wert (URI) annehmen, müssen den Typ " [System. Uri](/dotnet/api/System.Uri)" aufweisen.

- Vermeiden Sie grundlegende Zeichen folgen Parameter für alle außer frei Form Texteigenschaften.

- Sie können einem Parameter eine beliebige Anzahl von Parametersätzen hinzufügen. Weitere Informationen zu Parametersätzen finden Sie unter [Cmdlet-Parametersätze](./cmdlet-parameter-sets.md).

Windows PowerShell bietet auch eine Reihe allgemeiner Parameter, die für jedes Cmdlet automatisch verfügbar sind. Weitere Informationen zu diesen Parametern und ihren Aliasen finden [Sie unter Allgemeine Cmdlet-Parameter](./common-parameter-names.md).

## <a name="see-also"></a>Weitere Informationen

[Allgemeine Cmdlet-Parameter](./common-parameter-names.md)

[Typen von Cmdlet-Parametern](./types-of-cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
