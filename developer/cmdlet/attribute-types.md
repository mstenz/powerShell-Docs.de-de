---
title: Attributtypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863806"
---
# <a name="attribute-types"></a>Attributtypen

Cmdlet-Attribute können nach Funktionalität gruppiert werden.
Die folgenden Abschnitte beschreiben die verfügbaren Attribute und beschreiben, was das Laufzeitmodul erledigt, wenn das Attribut aufgerufen wird.

## <a name="cmdlet-attributes"></a>Cmdlet-Attribute

### <a name="cmdlet"></a>Cmdlet

Identifiziert eine .NET Framework-Klasse als ein Cmdlet.
Dies ist das erforderliche base-Attribut.
Weitere Informationen finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parameterattribute

### <a name="parameter"></a>Parameter

Identifiziert eine öffentliche Eigenschaft in der Cmdlet-Klasse als Cmdlet-Parameter.
Weitere Informationen finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Gibt einen oder mehrere Aliase für einen Parameter an.
Weitere Informationen finden Sie unter [Alias Attributdeklaration](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Validierungsattribute Argument

### <a name="validatecount"></a>ValidateCount

Gibt die minimale und maximale Anzahl von Argumenten, die für einen Cmdlet-Parameter zulässig sind.
Weitere Informationen finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength auf

Gibt eine minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter-Argument.
Weitere Informationen finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Gibt an, das Muster eines regulären Ausdrucks, das das Argument der Cmdlet-Parameter übereinstimmen muss.
Weitere Informationen finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Gibt die minimalen und maximalen Werte für ein Cmdlet-Parameter-Argument.
Weitere Informationen finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Gibt einen Satz gültiger Werte für das Argument der Cmdlet-Parameter.
Weitere Informationen finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
