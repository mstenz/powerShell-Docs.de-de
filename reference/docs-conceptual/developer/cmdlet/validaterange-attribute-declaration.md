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
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369129"
---
# <a name="validaterange-attribute-declaration"></a>Attributdeklaration: ValidateRange

Das validaterange-Attribut gibt die minimalen und maximalen Werte (den Bereich) für das Cmdlet-Parameter Argument an. Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.

## <a name="syntax"></a>Syntax

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parameter

`MinRange` ([System. Object](/dotnet/api/system.object)) erforderlich. Gibt den zulässigen Mindestwert an.

`MaxRange` ([System. Object](/dotnet/api/system.object)) erforderlich. Gibt den maximal zulässigen Wert an.

## <a name="remarks"></a>Hinweise

- Die Windows PowerShell-Laufzeit löst einen Konstruktionsfehler aus, wenn der Wert des `MinRange`-Parameters größer als der Wert des `MaxRange`-Parameters ist.

- Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Validierungs Fehler aus:

    - Wenn der Wert des Arguments kleiner ist als das `MinRange` Limit oder größer als das `MaxRange` Limit.

    - Wenn das Argument nicht denselben Typ wie die `MinRange` und die `MaxRange` Parameter hat.

- Das validaterange-Attribut wird von der [System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
