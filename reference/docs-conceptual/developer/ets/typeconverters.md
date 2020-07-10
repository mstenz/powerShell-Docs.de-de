---
title: Typkonverter für erweiterte Typsysteme
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: f709a64febe68733b79ed8af804714d3f3ddeaac
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217939"
---
# <a name="ets-type-converters"></a>ETS-Typkonverter

ETS verwendet zwei grundlegende Typen von Typkonvertern, wenn ein-Befehl an die-Methode gerichtet wird `LanguagePrimitives.ConvertTo(System.Object, System.Type)` . Wenn diese Methode aufgerufen wird, versucht PowerShell, die Typkonvertierung mit ihren standardmäßigen PowerShell-sprach Konvertern oder einem benutzerdefinierten Konverter auszuführen. Wenn die Konvertierung von PowerShell nicht durchgeführt werden kann, wird eine **psinvalidcastexception** -Ausnahme ausgelöst.

## <a name="standard-windows-powershell-language-converters"></a>Standard mäßige Windows PowerShell-sprach Konverter

Diese Standard Konvertierungen werden vor allen benutzerdefinierten Konvertierungen geprüft und können nicht überschrieben werden. In der folgenden Tabelle werden die Typkonvertierungen aufgelistet, die von PowerShell beim Aufrufen der-Methode durchgeführt werden `ConvertTo(System.Object, System.Type)` . Beachten Sie, dass Verweise auf die Parameter **valueToConvert** und **ResultType** auf Parameter der `ConvertTo(System.Object,System.Type)` Methode verweisen.

| From (valueToConvert) |  To (ResultType)  |                                                                               Rückgabe                                                                               |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NULL                  | Zeichenfolge            | ""                                                                                                                                                                  |
| NULL                  | Char              | '\0'                                                                                                                                                                |
| NULL                  | Numeric           | `0`des Typs, der im **ResultType** -Parameter angegeben ist.                                                                                                          |
| NULL                  | Boolean           | Ergebnisse des Aufrufes der- `IsTrue(System.Object)(Null)` Methode.                                                                                                        |
| NULL                  | PSObject          | Neues Objekt vom Typ " **psobject**".                                                                                                                                    |
| NULL                  | Nicht-Werttyp    | Normal.                                                                                                                                                               |
| NULL                  | Nullable &lt; T&gt; | Normal.                                                                                                                                                               |
| Abgeleitete Klasse         | Basisklasse        | **valueToConvert**                                                                                                                                                  |
| Dagegen              | Void              | **Automationnull. Value**                                                                                                                                            |
| Dagegen              | Zeichenfolge            | Ruft den `ToString` Mechanismus auf.                                                                                                                                         |
| Dagegen              | Boolean           | `IsTrue(System.Object) (valueToConvert)`                                                                                                                            |
| Dagegen              | PSObject          | Ergebnisse des Aufrufes der- `AsPSObject(System.Object) (valueToConvert)` Methode.                                                                                         |
| Dagegen              | XML-Dokument      | Konvertiert **valueToConvert** in eine Zeichenfolge und ruft dann den **XmlDocument** -Konstruktor auf.                                                                                      |
| Array                 | Array             | Versucht, jedes Element des Arrays zu konvertieren.                                                                                                                      |
| Singleton             | Array             | `Array[0]`entspricht **valueToConvert** , das in den Elementtyp des Arrays konvertiert wird.                                                                            |
| IDictionary           | Hash Tabelle        | Ergebnisse des Aufrufes Hashtable-Aufrufes (valueToConvert).                                                                                                                       |
| Zeichenfolge                | Char[]            | `valueToConvert.ToCharArray`                                                                                                                                        |
| Zeichenfolge                | Regex             | Ergebnisse des Aufrufes `Regx(valueToConvert)` .                                                                                                                          |
| Zeichenfolge                | Typ              | Gibt den entsprechenden Typ mithilfe des **valueToConvert** -Parameters zum Durchsuchen von **runspaceconfiguration.** Assemblys zurück.                                                 |
| String                | Numeric           | Wenn **valueToConvert** den Wert "" hat, wird `0` der **ResultType**zurückgegeben. Andernfalls wird die Kultur "Kultur invariant" verwendet, um einen numerischen Wert zu erhalten.                       |
| Integer               | System.Enum       | Konvertiert die Ganzzahl in die Konstante, wenn die Ganzzahl durch die-Enumeration definiert wird. Wenn die Ganzzahl nicht definiert ist, wird eine **psinvalidcastexception** -Ausnahme ausgelöst. |

## <a name="custom-conversions"></a>Benutzerdefinierte Konvertierungen

Wenn PowerShell den Typ nicht mit einem standardmäßigen PowerShell-sprach Konverter konvertieren kann, prüft er, ob benutzerdefinierte Konverter verwendet werden. PowerShell sucht in der in diesem Abschnitt beschriebenen Reihenfolge nach verschiedenen Typen von benutzerdefinierten Konvertern. Beachten Sie, dass Verweise auf die Parameter **valueToConvert** und **ResultType** auf Parameter der `ConvertTo(System.Object, System.Type)` Methode verweisen. Wenn ein benutzerdefinierter Konverter eine Ausnahme auslöst, wird kein weiterer Versuch unternommen, das Objekt zu konvertieren, und diese Ausnahme wird in eine **psinvalidcastexception** -Ausnahme umschließt, die dann ausgelöst wird.

## <a name="powershell-type-converter"></a>PowerShell-Typkonverter

PowerShell-Typkonverter werden zum Konvertieren eines einzelnen Typs oder einer Typenfamilie verwendet, z. b. alle Typen, die von der **System. enumum** -Klasse abgeleitet werden. Um einen PowerShell-Typkonverter zu erstellen, müssen Sie eine pstypeer Converter-Klasse implementieren und diese Implementierung der Zielklasse zuordnen. Es gibt zwei Möglichkeiten, den PowerShell-Typkonverter der Zielklasse zuzuordnen.

- Durch die typkonfigurationsdatei
- Durch Anwenden des **TypeConverterAttribute** -Attributs auf die Zielklasse

PowerShell-Typkonverter, die von der " [pstypeer Converter](/dotnet/api/system.management.automation.pstypeconverter) "-Klasse abgeleitet sind, stellen Methoden zum Konvertieren eines Objekts in einen bestimmten Typ oder von einem bestimmten Typ bereit. Wenn der **valueToConvert** -Parameter ein Objekt enthält, dem ein PowerShell-Typkonverter zugeordnet ist, ruft PowerShell das`PSTypeConverter.ConvertTo(System.Object, System.Type,System.IFormatProvider, System.Boolean)`
-Methode des zugeordneten Konverters, um das Objekt in den durch den **ResultType** -Parameter angegebenen Typ zu konvertieren. Wenn der **ResultType** -Parameter auf einen Typ verweist, dem ein PowerShell-Typkonverter zugeordnet ist, ruft PowerShell das`PSTypeConverter.ConvertFrom(System.Object,System.Type, System.IFormatProvider, System.Boolean)`
-Methode des zugeordneten Konverters, um das Objekt von dem durch den **ResultType** -Parameter angegebenen Typ zu konvertieren.

## <a name="system-type-converter"></a>Systemtyp Konverter

Systemtyp Konverter werden verwendet, um eine bestimmte Zielklasse zu konvertieren. Diese Art von Konverter kann nicht zum Konvertieren einer Klassenfamilie verwendet werden. Um einen Systemtyp Konverter zu erstellen, müssen Sie eine [TypeConverter](/dotnet/api/system.management.automation.runspaces.typedata.typeconverter#System_Management_Automation_Runspaces_TypeData_TypeConverter) -Klasse implementieren und diese Implementierung der Zielklasse zuordnen. Es gibt zwei Möglichkeiten, den Systemtyp Konverter der Zielklasse zuzuordnen.

- Durch die typkonfigurationsdatei
- Durch Anwenden des TypeConverterAttribute-Attributs auf die Zielklasse

## <a name="parse-converter"></a>Konverter analysieren

Wenn der **valueToConvert** -Parameter eine Zeichenfolge ist und der Objekttyp des **ResultType** -Parameters über eine- `Parse` Methode verfügt, wird die- `Parse` Methode aufgerufen, um die Zeichenfolge zu konvertieren.

## <a name="constructor-converter"></a>Konstruktorkonverter

Wenn der Objekttyp des **ResultType** -Parameters über einen Konstruktor verfügt, der über einen einzelnen Parameter verfügt, der mit dem-Objekt des **valueToConvert** -Parameters identisch ist, wird dieser Konstruktor aufgerufen.

## <a name="implicit-cast-operator-converter"></a>Impliziter Umwandlungs Operator Konverter

Wenn der **valueToConvert** -Parameter einen impliziten Umwandlungs Operator aufweist, der in **ResultType**konvertiert, wird der Umwandlungs Operator aufgerufen. Wenn der **ResultType** -Parameter über einen impliziten Umwandlungs Operator verfügt, der von **valueToConvert**konvertiert, wird der Cast-Operator aufgerufen.

## <a name="explicit-cast-operator-converter"></a>Expliziter Cast Operator Konverter

Wenn der **valueToConvert** -Parameter über einen expliziten Umwandlungs Operator verfügt, der in **ResultType**konvertiert wird, wird der Cast-Operator aufgerufen. Wenn der **ResultType** -Parameter über einen expliziten Umwandlungs Operator verfügt, der von **valueToConvert**konvertiert, wird der Cast-Operator aufgerufen.
