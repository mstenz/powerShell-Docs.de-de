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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364579"
---
# <a name="attribute-types"></a>Attributtypen

Cmdlet-Attribute können nach Funktionalität gruppiert werden.
In den folgenden Abschnitten werden die verfügbaren Attribute beschrieben, und es wird beschrieben, was die Laufzeit bewirkt, wenn das Attribut aufgerufen wird.

## <a name="cmdlet-attributes"></a>Cmdlet-Attribute

### <a name="cmdlet"></a>Cmdlet

Identifiziert eine .NET Framework Klasse als Cmdlet.
Dies ist das erforderliche Basis Attribut.
Weitere Informationen finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parameter Attribute

### <a name="parameter"></a>Parameter

Identifiziert eine öffentliche Eigenschaft in der Cmdlet-Klasse als Cmdlet-Parameter.
Weitere Informationen finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Gibt mindestens einen Alias für einen Parameter an.
Weitere Informationen finden Sie unter [Alias Attribut Deklaration](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Argument Validierungs Attribute

### <a name="validatecount"></a>Validatecount

Gibt die minimale und maximale Anzahl von Argumenten an, die für einen Cmdlet-Parameter zulässig sind.
Weitere Informationen finden Sie unter [validatecount-Attribut Deklaration](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Gibt eine minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter Argument an.
Weitere Informationen finden Sie unter [validateLength-Attribut Deklaration](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Gibt ein Muster für einen regulären Ausdruck an, dem das Cmdlet-Parameter Argument entsprechen muss.
Weitere Informationen finden Sie unter [validatepattern-Attribut Deklaration](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>Validaterange

Gibt die minimalen und maximalen Werte für ein Cmdlet-Parameter Argument an.
Weitere Informationen finden Sie unter [validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Gibt einen Satz gültiger Werte für das Cmdlet-Parameter Argument an.
Weitere Informationen finden Sie unter [validateset-Attribut Deklaration](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
