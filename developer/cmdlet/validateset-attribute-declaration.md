---
title: ValidateSet Attributdeklaration | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067066"
---
# <a name="validateset-attribute-declaration"></a>Attributdeklaration: ValidateSet

Die ValidateSetAttribute-Attribut gibt an, einen Satz möglicher Werte für ein Cmdlet-Parameter-Argument. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

Wenn dieses Attribut angegeben wird, bestimmt die Windows PowerShell-Laufzeit an, ob das angegebene Argument für die Cmdlet-Parameter ein Element in der Gruppe angegebenen Element entspricht. Das Cmdlet ausgeführt wird, nur dann, wenn das Parameterargument ein Element in der Gruppe entspricht. Wenn keine Übereinstimmung gefunden wird, wird ein Fehler von der Windows PowerShell-Laufzeit ausgelöst.

## <a name="syntax"></a>Syntax

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parameter

`ValidValues` ([System.String](/dotnet/api/System.String)) erforderlich. Gibt die gültigen Parameterwerte des Elements an. Das folgende Beispiel zeigt, wie Sie ein Element oder mehrere Elemente angeben.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. Der Standardwert von `true` gibt an, dass die Groß-/Kleinschreibung ignoriert wird. Der Wert `false` macht das Cmdlet Groß-/Kleinschreibung beachtet.

## <a name="remarks"></a>Hinweise

- Dieses Attribut kann nur einmal pro Parameter verwendet werden.

- Wenn der Wert des Parameters ein Array ist, muss jedes Element des Arrays ein Element von dem festgelegten Attribut übereinstimmen.

- Das ValidateSetAttribute-Attribut definiert ist, indem die [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
