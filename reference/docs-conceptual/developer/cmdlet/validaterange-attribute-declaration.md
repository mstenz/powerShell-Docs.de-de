---
title: Validaterange-Attribut Deklaration | Microsoft-Dokumentation
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
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692016"
---
# <a name="validaterange-attribute-declaration"></a>Attributdeklaration: ValidateRange

Das validaterange-Attribut gibt die minimalen und maximalen Werte (den Bereich) für das Cmdlet-Parameter Argument an. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parameter

`MinRange`([System. Object](/dotnet/api/system.object)) erforderlich. Gibt den zulässigen Mindestwert an.

`MaxRange`([System. Object](/dotnet/api/system.object)) erforderlich. Gibt den maximal zulässigen Wert an.

## <a name="remarks"></a>Hinweise

- Die Windows PowerShell-Laufzeit löst einen Konstruktionsfehler aus, wenn der Wert des- `MinRange` Parameters größer als der Wert des- `MaxRange` Parameters ist.

- Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Validierungs Fehler aus:

  - Wenn der Wert des Arguments kleiner als das `MinRange` Limit oder größer als das Limit ist `MaxRange` .

  - Wenn das Argument nicht vom gleichen Typ wie der `MinRange` und die Parameter ist `MaxRange` .

- Das validaterange-Attribut wird von der [System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
