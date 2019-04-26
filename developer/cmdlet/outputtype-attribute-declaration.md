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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067602"
---
# <a name="outputtype-attribute-declaration"></a>Attributdeklaration: OutputType

Die `OutputType` Attribut identifiziert, die .NET Framework-Typen, die von einem Cmdlet, Funktion oder Skript zurückgegeben.

## <a name="syntax"></a>Syntax

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

Typ (`string[]` oder `Type[]`) erforderlich. Gibt die Typen, die von der Cmdlet-Funktion oder Skript zurückgegeben.

ParameterSetName (testeigenschaftentyp Optional. Gibt an, der Parameter legt fest, die im angegebenen Typen zurückgeben der `type` Parameter.

ProviderCmdlet Optional. Gibt an, das Anbieter-Cmdlet, das im angegebenen Typen gibt die `type` Parameter.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
