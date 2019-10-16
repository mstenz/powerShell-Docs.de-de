---
title: OutputType-Attribut Deklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365339"
---
# <a name="outputtype-attribute-declaration"></a>Attributdeklaration: OutputType

Das `OutputType`-Attribut identifiziert die .NET Framework Typen, die von einem Cmdlet, einer Funktion oder einem Skript zurückgegeben werden.

## <a name="syntax"></a>Syntax

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

Der Typ (`string[]` oder `Type[]`) ist erforderlich. Gibt die Typen an, die von der Cmdlet-Funktion oder dem Skript zurückgegeben werden.

Parametersetname (String []) ist optional. Gibt die Parametersätze an, die die im `type`-Parameter angegebenen Typen zurückgeben.

providercmdlet ist optional. Gibt das Anbieter-Cmdlet an, das die im `type`-Parameter angegebenen Typen zurückgibt.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
