---
title: Fehler und Ausnahmen im erweiterten Typsystem
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 0e0b158e51d15db266415fb1ea6bb16fba319e62
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86218017"
---
# <a name="errors-and-exceptions-in-the-extended-type-system"></a>Fehler und Ausnahmen im erweiterten Typsystem

Fehler können während der Initialisierung von Typdaten in ETS auftreten, beim Zugriff auf ein Member eines **psobject** -Objekts oder bei Verwendung einer der Hilfsprogrammklassen, z. b. **LanguagePrimitives**.

## <a name="runtime-errors"></a>Laufzeitfehler

Bei einer Ausnahme sind bei der Umwandlung alle Ausnahmen, die während der Laufzeit von ETS ausgelöst werden, entweder eine **extendedtypesystemexception** -Ausnahme oder eine Ausnahme, die von der **extendedtypesystemexception** -Klasse abgeleitet wird. Dadurch können Skriptentwickler diese Ausnahmen mithilfe der- `Trap` Anweisung in Ihrem Skript abfangen.

## <a name="errors-getting-member-values"></a>Fehler beim erhalten von Element Werten

Alle Fehler, die beim Aufrufen des Werts eines ETS-Members (Eigenschaft, Methode oder parametrisierte Eigenschaft) auftreten, bewirken, dass eine **getvalueexception** -oder **getvaluinput vocationexception** -Ausnahme ausgelöst wird.
Wenn in ETS erkannt wird, dass ein Fehler aufgetreten ist, wird eine **getvalueexception** -Ausnahme ausgelöst. Wenn der zugrunde liegende Getter eines referenzierten Members erkennt, dass ein Fehler aufgetreten ist, wird eine **getvalueinvocationexception** -Ausnahme ausgelöst, die die innere Ausnahme enthält, die den Get-Aufruf Fehler verursacht hat.

## <a name="errors-setting-member-values"></a>Fehler beim Festlegen von Element Werten

Alle Fehler, die beim Festlegen des Werts einer ETS-Eigenschaft auftreten, bewirken, dass eine **setvalueexception** -oder **setvalueinvocationexception** -Ausnahme ausgelöst wird. Wenn in ETS erkannt wird, dass ein Fehler aufgetreten ist, wird eine **setvalueexception** -Ausnahme ausgelöst. Wenn der zugrunde liegende Setter einer Eigenschaft, auf die verwiesen wird, erkennt, dass ein Fehler aufgetreten ist, wird eine **setvalueinvocationexception** -Ausnahme ausgelöst, die die innere Ausnahme enthält, die den Fehler beim Aufruf des Satzes verursacht hat.

## <a name="errors-invoking-a-method"></a>Fehler beim Aufrufen einer Methode.

Alle Fehler, die beim Aufrufen einer ETS-Methode auftreten, bewirken, dass eine **methodexception** -oder **methodinvocationexception** -Ausnahme ausgelöst wird. Wenn ETS erkennt, dass ein Fehler aufgetreten ist, wird eine **methodexception** -Ausnahme ausgelöst. Wenn die referenzierte Methode erkennt, dass ein Fehler aufgetreten ist, wird eine **methodinvocationexception** -Ausnahme ausgelöst, die die innere Ausnahme enthält, die den Aufruf Fehler verursacht hat.

## <a name="casting-errors"></a>Umwandlungs Fehler

Wenn versucht wird, eine ungültige Umwandlung auszuführen, wird eine **psinvalidcastexception** ausgelöst. Da diese Ausnahme von **System. InvalidCastException**abgeleitet wird, kann Sie nicht direkt aus dem Skript eingeschlossen werden. Beachten Sie, dass die Entität, die die Umwandlung versucht, **psinvalidcastexception** in einer **psruntimeexception** umschließen muss, damit diese von Skripts abrechenbar ist. Wenn versucht wird, den Wert eines **pspropertyset**-, **psmembership set**-, **psmethodinfo**-Elements oder eines Members der "read **onlypsmembership infocollection ' 1"** festzulegen, wird eine **NotSupportedException** ausgelöst.

## <a name="common-runtime-errors"></a>Allgemeine Laufzeitfehler

Alle anderen häufigen Laufzeitfehler, die auftreten, sind vom Typ **extendedtypesystemexception** Exception ohne zusätzliche spezifische Ausnahme Typen.

## <a name="initialization-errors"></a>Initialisierungsfehler

Fehler können auftreten, wenn initialisiert wird `types.ps1xml` . Diese Fehler werden in der Regel angezeigt, wenn die PowerShell-Laufzeit gestartet wird. Sie können jedoch auch angezeigt werden, wenn ein Modul geladen wird.
