---
title: Erweiterte Typsystem-Klassenmember
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: c066bd69c0ab20cceff96aa789654e80443758e5
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217946"
---
# <a name="extended-type-system-class-members"></a>Erweiterte Typsystem-Klassenmember

ETS verweist auf eine Reihe verschiedener Arten von Membern, deren Typen durch die **psmembership Types** -Enumeration definiert werden. Diese Elementtypen umfassen Eigenschaften, Methoden, Member und Element Sätze, die jeweils durch ihren eigenen CLR-Typ definiert sind. Beispielsweise wird eine **NoteProperty** durch ihren eigenen **psnoteproperty** -Typ definiert. Diese einzelnen CLR-Typen verfügen sowohl über eigene eindeutige Eigenschaften als auch über gemeinsame Eigenschaften, die von der [psmembership Info-Klasse](/dotnet/api/system.management.automation.psmemberinfo)geerbt werden.

## <a name="the-psmemberinfo-class"></a>Die psmembership Info-Klasse

Die **psmembership Info** -Klasse dient als Basisklasse für alle ETS-Elementtypen. Diese Klasse stellt die folgenden Basis Eigenschaften für alle Member CLR-Typen bereit.

- **Name** -Eigenschaft: der Name des Members. Dieser Name kann vom Basisobjekt definiert oder von PowerShell definiert werden, wenn angepasste Member oder Erweiterte Member verfügbar gemacht werden.
- **Value** -Eigenschaft: der Wert, der vom jeweiligen Member zurückgegeben wird. Jeder Elementtyp definiert, wie er seinen Elementwert behandelt.
- **Typameofvalue** -Eigenschaft: Dies ist der Name des CLR-Typs des Werts, der von der Value-Eigenschaft zurückgegeben wird.

## <a name="accessing-members"></a>Zugreifen auf Member

Auf Auflistungen von Membern kann **über die Eigenschaften**, **Methoden**und **Eigenschaften** des **psobject** -Objekts zugegriffen werden.

## <a name="ets-properties"></a>ETS-Eigenschaften

ETS-Eigenschaften sind Elemente, die als Eigenschaft behandelt werden können. Im Wesentlichen können Sie auf der linken Seite eines Ausdrucks angezeigt werden. Dazu zählen Alias Eigenschaften, Code Eigenschaften, PowerShell-Eigenschaften, Notiz Eigenschaften und Skript Eigenschaften. Weitere Informationen zu diesen Eigenschaften Typen finden Sie unter [ETS-Eigenschaften](properties.md).

## <a name="ets-methods"></a>ETS-Methoden

ETS-Methoden sind Member, die Argumente annehmen, möglicherweise Ergebnisse zurückgeben und nicht auf der linken Seite eines Ausdrucks angezeigt werden können. Dazu zählen Code Methoden, PowerShell-Methoden und Skript Methoden.
Weitere Informationen zu diesen Methoden Typen finden Sie unter [ETS-Methoden](methods.md).
