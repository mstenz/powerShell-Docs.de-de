---
title: Erweiterte Typsystem Eigenschaften
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 27da913b07dbc5f06ee46e5433208871168c36a5
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217934"
---
# <a name="ets-properties"></a>ETS-Eigenschaften

Eigenschaften sind Elemente, die als Eigenschaft behandelt werden können. Im Wesentlichen können Sie auf der linken Seite eines Ausdrucks angezeigt werden. Zu den verfügbaren Eigenschaften gehören Alias-, Code-, Notiz-und Skript Eigenschaften.

## <a name="alias-property"></a>Alias-Eigenschaft

Eine Alias Eigenschaft ist eine Eigenschaft, die auf eine andere Eigenschaft verweist, die das **psobject** -Objekt enthält. Es wird hauptsächlich zum Umbenennen der referenzierten Eigenschaft verwendet. Sie kann jedoch auch verwendet werden, um den Wert der referenzierten Eigenschaft in einen anderen Typ zu konvertieren. In Bezug auf ETS ist dieser Eigenschaftentyp immer ein erweiterter Member und wird durch die [psaliasproperty](/dotnet/api/system.management.automation.psaliasproperty) -Klasse definiert. Die-Klasse enthält die folgenden Eigenschaften.

- Configuration Manager-Eigenschaft: der CLR **-Typ,** mit dem der Wert des referenzierten Members konvertiert wird.
- **Isge-** Eigenschaft: gibt an, ob der Wert der Eigenschaft, auf die verwiesen wird, abgerufen werden kann.
  Diese Eigenschaft wird dynamisch festgelegt, indem die **isgeamp** ; Eigenschaft der referenzierten Eigenschaft überprüft wird.
- **IsSettable** Property: gibt an, ob der Wert der Eigenschaft, auf die verwiesen wird, festgelegt werden kann. Diese Eigenschaft wird dynamisch festgelegt, indem die **IsSettable** -Eigenschaft der referenzierten Eigenschaft überprüft wird.
- **Membership Type** -Eigenschaft: eine **aliasproperty** -Enumerationskonstante, die diese Eigenschaft als Alias Eigenschaft definiert.
- **Referencedmembership Name** -Eigenschaft: der Name der referenzierten Eigenschaft, auf die dieser Alias verweist.
- **Typameofvalue** -Eigenschaft: der vollständige Name des CLR-Typs des Werts der Eigenschaft, auf die verwiesen wird.
- **Value** -Eigenschaft: der Wert der Eigenschaft, auf die verwiesen wird.

## <a name="code-property"></a>Code-Eigenschaft

Eine Code Eigenschaft ist eine Eigenschaft, bei der es sich um einen Getter und Setter handelt, der in einer CLR-Sprache definiert ist. Damit eine Code Eigenschaft verfügbar wird, muss ein Entwickler die-Eigenschaft in einer CLR-Sprache schreiben, kompilieren und die resultierende Assembly versenden. Diese Assembly muss im Runspace verfügbar sein, in dem die Code Eigenschaft gewünscht ist. In Bezug auf ETS ist dieser Eigenschaftentyp immer ein erweiterter Member und wird durch die Klasse [pscodeproperty](/dotnet/api/system.management.automation.pscodeproperty) definiert. Die-Klasse enthält die folgenden Eigenschaften.

- **Gettercodereferenzierungseigenschaft** : die Methode, die verwendet wird, um den Wert der Code-Eigenschaft zu erhalten.
- **Isgeamp** ; Eigenschaft: gibt an, ob der Wert der Eigenschaft Code abgerufen werden kann, die **settercodereferenzierungseigenschaft** : die Methode, mit der der Wert der Code-Eigenschaft festgelegt wird.
- **IsSettable** -Eigenschaft: gibt an, ob der Wert der Code-Eigenschaft festgelegt werden kann, dass die **settercodereferenzierungseigenschaft** nicht NULL ist.
- **Membership Type** -Eigenschaft: eine **CodeProperty** -Enumerationskonstante, die diese Eigenschaft als Code Eigenschaft definiert.
- **Settercodereferenzierungseigenschaft** : die Methode, die verwendet wird, um den Wert der Code-Eigenschaft zu erhalten.
- **Typameofvalue** -Eigenschaft: der CLR-Typ des Code Eigenschafts Werts, der von den Eigenschaften Get-Vorgang zurückgegeben wird.
- **Value** -Eigenschaft: der Wert der Code-Eigenschaft. Wenn diese Eigenschaft abgerufen wird, wird der gettercodereferenzierungscode aufgerufen, der das aktuelle **psobject** -Objekt übergibt und den von dem Aufruf zurückgegebenen Wert zurückgibt. Wenn diese Eigenschaft festgelegt ist, wird der Setter-Code in der **settercodereferenzierungseigenschaft** aufgerufen und übergibt das aktuelle **psobject** -Objekt als erstes Argument und das-Objekt, das zum Festlegen des Werts als zweites Argument verwendet wird.

## <a name="note-property"></a>Note-Eigenschaft

Eine Hinweis Eigenschaft ist eine Eigenschaft, die über eine Name-Wert-Kopplung verfügt. In Bezug auf ETS ist dieser Eigenschaftentyp immer ein erweiterter Member und wird durch die [psnoteproperty](/dotnet/api/system.management.automation.psnoteproperty) -Klasse definiert. Die-Klasse enthält die folgenden Eigenschaften.

- **Isge-** Eigenschaft: gibt an, ob der Wert der Note-Eigenschaft abgerufen werden kann.
- **IsSettable** -Eigenschaft: gibt an, ob der Wert der Note-Eigenschaft festgelegt werden kann.
- **Membership Type** -Eigenschaft: eine **NoteProperty** -Enumerationskonstante, die diese Eigenschaft als Notiz Eigenschaft definiert.
- **Typameofvalue** -Eigenschaft: der voll qualifizierte Typname des Objekts, das durch den Get-Vorgang der Note-Eigenschaft zurückgegeben wird.
- **Value**: der Wert der Note-Eigenschaft.

## <a name="powershell-property"></a>PowerShell-Eigenschaft

Eine PowerShell-Eigenschaft ist eine Eigenschaft, die für das Basisobjekt definiert ist, oder eine Eigenschaft, die über einen Adapter verfügbar gemacht wird. Sie kann sowohl auf CLR-Felder als auch auf CLR-Eigenschaften verweisen. In Bezug auf ETS kann dieser Typ von Eigenschaft entweder ein Basismember oder ein Adapter Element sein und wird durch die [psproperty](/dotnet/api/system.management.automation.psproperty) -Klasse definiert. Die-Klasse enthält die folgenden Eigenschaften.

- **Isgetfähige** Eigenschaft: gibt an, ob der Wert der Basis Eigenschaft oder der angepassten Eigenschaft abgerufen werden kann.
- **IsSettable** -Eigenschaft: gibt an, ob der Wert der Basis Eigenschaft oder der angepassten Eigenschaft festgelegt werden kann.
- **Membership Type** -Eigenschaft: eine eigenschaftenenumerationskonstante, die diese Eigenschaft als PowerShell-Eigenschaft definiert.
- **Typameofvalue** -Eigenschaft: der voll qualifizierte Name des Eigenschafts Werttyps. Für eine Eigenschaft, deren Wert eine Zeichenfolge ist, ist der Eigenschafts Werttyp z. b. **System. String**.
- **Value** -Eigenschaft: der Wert der Eigenschaft. Wenn der Get-oder Set-Vorgang für eine Eigenschaft aufgerufen wird, die diesen Vorgang nicht unterstützt, wird eine **getvalueexception** -oder **setvalueexception** -Ausnahme ausgelöst.

## <a name="powershell-script-property"></a>PowerShell-Skript Eigenschaft

Eine Skript Eigenschaft ist eine Eigenschaft, die über Getter-und Setter-Skripts verfügt. In Bezug auf ETS ist dieser Eigenschaftentyp immer ein erweiterter Member und wird durch die [psscriptproperty](/dotnet/api/system.management.automation.psscriptproperty) -Klasse definiert. Die-Klasse enthält die folgenden Eigenschaften.

- **Getterscript** -Eigenschaft: das Skript, das zum Abrufen des Skript Eigenschafts Werts verwendet wird.
- **Isgeamp** ; Eigenschaft: gibt an, ob die **getterscript** -Eigenschaft einen Skriptblock verfügbar macht.
- **IsSettable** -Eigenschaft: gibt an, ob die **setterscript** -Eigenschaft einen Skriptblock verfügbar macht.
- **Membership Type** -Eigenschaft: eine scriptproperty-Enumerationskonstante, die diese Eigenschaft als Skript Eigenschaft identifiziert.
- **Setterscript** -Eigenschaft: das Skript, das verwendet wird, um den Wert der Skript Eigenschaft festzulegen.
- **Typameofvalue** -Eigenschaft: der voll qualifizierte Typname des Objekts, das vom Getter-Skript zurückgegeben wurde. In diesem Fall wird " **System. Object** " immer zurückgegeben.
- **Value** -Eigenschaft: der Wert der Script-Eigenschaft. Ein Get Ruft das Getter-Skript auf und gibt den bereitgestellten Wert zurück. Ein Satz Ruft das Setter-Skript auf.
