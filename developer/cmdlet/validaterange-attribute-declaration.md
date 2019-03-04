---
title: ValidateRange Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857036"
---
# <a name="validaterange-attribute-declaration"></a>Attributdeklaration: ValidateRange

Die ValidateRange-Attribut gibt an, die minimalen und maximalen Werte (Bereich) für das Argument der Cmdlet-Parameter. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parameter

`MinRange` (["System.Object"](/dotnet/api/system.object)) erforderlich. Gibt an, der zulässige Mindestwert.

`MaxRange` (["System.Object"](/dotnet/api/system.object)) erforderlich. Gibt den zulässigen Höchstwert an.

## <a name="remarks"></a>Hinweise

- Die Windows PowerShell-Laufzeit löst einen Fehler für die Erstellung bei den Wert des der `MinRange` -Parameter ist größer als der Wert von der `MaxRange` Parameter.

- Die Windows PowerShell-Laufzeit löst einen Validierungsfehler in den folgenden Situationen aus:

    - Wenn der Wert des Arguments ist kleiner als der `MinRange` Grenzwert oder größer als die `MaxRange` Grenzwert.

    - Wenn das Argument ist nicht vom gleichen Typ wie die `MinRange` und `MaxRange` Parameter.

- Das ValidateRange-Attribut definiert ist, indem die [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
