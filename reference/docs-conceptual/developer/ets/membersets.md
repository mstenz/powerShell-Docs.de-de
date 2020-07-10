---
title: Erweiterte typsystemmember-Sätze
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 11e1e7819efecc1f1d8164ef32fb97cda978e748
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217945"
---
# <a name="ets-member-sets"></a>ETS-Element Sätze

Mithilfe von Element Sätzen können Sie die Member des **psobject** -Objekts in zwei Teilmengen partitionieren, damit auf die Elemente der Teilmengen über Ihren Teilmengen Namen verwiesen werden kann. Die zwei Typen von Teilmengen enthalten Eigenschafts Sätze und Element Sätze. Wenn beispielsweise PowerShell Element Sätze verwendet, gibt es einen bestimmten Eigenschaften Satz mit dem Namen **defaultdisplaypropertyset** , der zur Laufzeit bestimmt, welche Eigenschaften für ein bestimmtes **psobject** -Objekt angezeigt werden.

## <a name="property-sets"></a>Eigenschaftensätze

Eigenschafts Sätze können beliebig viele Eigenschaften eines **psobject** -Typs enthalten. Im Allgemeinen kann ein Eigenschaften Satz immer dann verwendet werden, wenn eine Auflistung von Eigenschaften (desselben Typs) benötigt wird. Der Eigenschaften Satz wird erstellt, indem der `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` -Konstruktor mit dem Namen des Eigenschaften Satzes und den Namen der Eigenschaften, auf die verwiesen wird, aufgerufen wird. Das erstellte **pspropertyset** -Objekt kann dann als Alias verwendet werden, der auf die Eigenschaften in der Gruppe verweist. Die [pspropertyset](/dotnet/api/system.management.automation.pspropertyset) -Klasse verfügt über die folgenden Eigenschaften und Methoden.

- **IsInstance** -Eigenschaft: Ruft einen **booleschen** Wert ab, der die Quelle der Eigenschaft angibt.
- **Membership Type** -Eigenschaft: Ruft den Typ der Eigenschaften im Eigenschaften Satz ab.
- **Name** -Eigenschaft: Ruft den Namen des Eigenschaften Satzes ab.
- **Referencedpropertynames** -Eigenschaft: Ruft die Namen der Eigenschaften im Eigenschaften Satz ab.
- **Typameofvalue** -Eigenschaft: Ruft eine **PropertySet** -Enumerationskonstante ab, die diese Menge als Eigenschaften Satz definiert.
- **Value** -Eigenschaft: Ruft das **pspropertyset** -Objekt ab oder legt es fest.
- `PSPropertySet.Copy`Method: erstellt eine exakte Kopie des **pspropertyset** -Objekts.
- `PSMemberSet.ToString`Method: konvertiert das **pspropertyset** -Objekt in eine Zeichenfolge.

## <a name="member-sets"></a>Element Sätze

Element Sätze können beliebig viele erweiterte Member eines beliebigen Typs enthalten. Der Member-Satz wird durch Aufrufen von erstellt.`PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`
Konstruktor mit dem Namen des Element Satzes und den Namen der Member, auf die verwiesen wird. Das erstellte **pspropertyset** -Objekt kann dann als Alias verwendet werden, der auf die Elemente in der Gruppe verweist. Die [psmembership Set](/dotnet/api/system.management.automation.psmemberset) -Klasse verfügt über die folgenden Eigenschaften und Methoden.

- **IsInstance** -Eigenschaft: Ruft einen **booleschen** Wert ab, der die Quelle des Members angibt.
- **Members** -Eigenschaft: Ruft alle Member des Element Satzes ab.
- **Membership Type** -Eigenschaft: Ruft eine Enumerationskonstante für den **mitgliedsatz** ab, die diese Menge als Element Satz definiert.
- **Methods** -Eigenschaft: Ruft die Methoden ab, die im Element Satz enthalten sind.
- **Properties** -Eigenschaft: Ruft die Eigenschaften ab, die im Element Satz enthalten sind.
- **Typameofvalue** -Eigenschaft: Ruft eine Enumerationskonstante für den **mitgliedsatz** ab, die diese Menge als Element Satz definiert.
- **Value** -Eigenschaft: Ruft das **psmembership set** -Objekt ab.
- `PSMemberSet.Copy`Method: erstellt eine exakte Kopie des **psmembership Set** -Objekts.
- `PSMemberSet.ToString`Method: konvertiert das **psmembership Set** -Objekt in eine Zeichenfolge.
