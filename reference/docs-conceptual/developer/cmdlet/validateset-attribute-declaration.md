---
title: Validateset-Attribut Deklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364279"
---
# <a name="validateset-attribute-declaration"></a>Attributdeklaration: ValidateSet

Das validatesetattribute-Attribut gibt einen Satz möglicher Werte für ein Cmdlet-Parameter Argument an. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

Wenn dieses Attribut angegeben wird, bestimmt die Windows PowerShell-Laufzeit, ob das angegebene Argument für den Cmdlet-Parameter mit einem Element im angegebenen Element Satz übereinstimmt. Das-Cmdlet wird nur ausgeführt, wenn das Parameter Argument mit einem Element im Satz übereinstimmt. Wenn keine Entsprechung gefunden wird, wird von der Windows PowerShell-Laufzeit ein Fehler ausgelöst.

## <a name="syntax"></a>Syntax

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parameter

`ValidValues` ([System. String](/dotnet/api/System.String)) ist erforderlich. Gibt die gültigen Parameter Element Werte an. Im folgenden Beispiel wird gezeigt, wie ein-Element oder mehrere-Elemente angegeben werden.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

der optionale benannte Parameter `IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)). Der Standardwert `true` gibt an, dass der Fall ignoriert wird. Bei einem Wert von "`false`" wird die Groß-/Kleinschreibung berücksichtigt.

## <a name="remarks"></a>Hinweise

- Dieses Attribut kann nur einmal pro Parameter verwendet werden.

- Wenn der Parameterwert ein Array ist, muss jedes Element des Arrays mit einem Element des Attribut Satzes identisch sein.

- Das validatesetattribute-Attribut wird von der [System. Management. Automation. validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
