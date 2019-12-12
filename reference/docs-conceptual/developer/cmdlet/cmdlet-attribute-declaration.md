---
title: Cmdlet-Attribut Deklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363539"
---
# <a name="cmdlet-attribute-declaration"></a>Attributdeklaration: Cmdlet

Das Cmdlet-Attribut identifiziert eine Microsoft .NET Framework-Klasse als Cmdlet und gibt das Verb und das Substantiv an, das zum Aufrufen des Cmdlets verwendet wird.

## <a name="syntax"></a>Syntax

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

`VerbName` ([System. String](/dotnet/api/System.String)) erforderlich. Gibt das Cmdlet-Verb an. Dieses Verb gibt die Aktion an, die vom Cmdlet ausgeführt wird. Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md) und [erforderliche Entwicklungs Richtlinien](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) erforderlich. Gibt das Cmdlet-Substantiv an. Dieses Substantiv gibt die Ressource an, auf die das Cmdlet angewendet wird. Weitere Informationen zu Cmdlet-Nomen finden Sie unter [Cmdlet-Deklaration](./cmdlet-class-declaration.md) und [Richtlinien für die Entwicklung von Richtlinien](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter. `True` gibt an, dass das Cmdlet Aufrufe der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode unterstützt, die dem Cmdlet eine Möglichkeit bietet, den Benutzer vor einer Aktion aufzufordern, durch die das System geändert wird. `False`, der Standardwert, gibt an, dass das Cmdlet Aufrufe der [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode nicht unterstützt. Weitere Informationen zu Bestätigungs Anforderungen finden Sie unter [Anfordern einer Bestätigung](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System. Management. Automation. confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) optionaler benannter Parameter. Gibt an, wann die Aktion des Cmdlets durch einen aufzurufenden Befehl der [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode bestätigt werden soll. " [System. Management. Automation. Cmdlet. Schulter Process](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " wird nur aufgerufen, wenn der "confirmimpact"-Wert des Cmdlets (standardmäßig Mittel) gleich oder größer als der Wert der `$ConfirmPreference` Variable ist. Dieser Parameter sollte nur angegeben werden, wenn der `SupportsShouldProcess`-Parameter angegeben wird.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) optionaler benannter Parameter. Gibt den Standardparameter Satz an, den die Windows PowerShell-Laufzeit versucht, zu verwenden, wenn nicht bestimmt werden kann, welcher Parameter verwendet werden soll. Beachten Sie, dass diese Situation vermieden werden kann, indem der Unique-Parameter jedes Parameters einen obligatorischen Parameter festgelegt wird.

Es gibt einen Fall, in dem Windows PowerShell den Standardparameter Satz nicht verwenden kann, auch wenn ein standardmäßiger Parametersatz Name angegeben wird. Windows PowerShell Runtime kann nicht zwischen Parametersätzen unterscheiden, die ausschließlich auf dem Objekttyp basieren. Wenn Sie z. b. einen Parametersatz haben, der eine Zeichenfolge als Dateipfad annimmt, und eine andere Gruppe, die ein **FileInfo** -Objekt direkt annimmt, kann Windows PowerShell nicht bestimmen, welcher Parameter auf Grundlage der an das Cmdlet übergebenen Werte verwendet werden soll. Außerdem wird der Standardparameter Satz nicht verwendet. In diesem Fall löst Windows PowerShell, selbst wenn Sie einen Standardparameter Satz-Namen angeben, eine mehrdeutige Parametersatz-Fehlermeldung aus.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter. `True` gibt an, dass das Cmdlet innerhalb einer Transaktion verwendet werden kann. Wenn `True` angegeben wird, fügt die Windows PowerShell-Laufzeit den `UseTransaction`-Parameter der Parameterliste des Cmdlets hinzu. `False`, der Standardwert, gibt an, dass das Cmdlet nicht innerhalb einer Transaktion verwendet werden kann.

## <a name="remarks"></a>Hinweise

- Mit dem Verb und dem Substantiv werden das registrierte Cmdlet identifiziert und das Cmdlet innerhalb eines Skripts aufgerufen.

- Wenn das Cmdlet von der Windows PowerShell-Konsole aus aufgerufen wird, ähnelt der Befehl dem folgenden Befehl:

**Verbname-nounname**

- Alle Cmdlets, die Ressourcen außerhalb von Windows PowerShell ändern, sollten das `SupportsShouldProcess`-Schlüsselwort enthalten, wenn das Cmdlet-Attribut deklariert wird, sodass das Cmdlet die [System. Management. Automation. Cmdlet. dendprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode vor der Ausführung des Cmdlets aufruft. Wenn der [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Rückruf `false`zurückgibt, sollte die Aktion nicht durchgeführt werden. Weitere Informationen zu den Bestätigungs Anforderungen, die vom [System. Management. Automation. Cmdlet. daudprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Befehl generiert werden, finden Sie unter [anfordern der Bestätigung](./requesting-confirmation-from-cmdlets.md).

Die Cmdlet-Parameter "`Confirm`" und "`WhatIf`" sind nur für Cmdlets verfügbar, die [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Aufrufe unterstützen.

## <a name="example"></a>Beispiel

In der folgenden Klassendefinition wird das-Cmdlet-Attribut verwendet, um die .NET Framework-Klasse für ein **Get-proc-** Cmdlet zu identifizieren, das Informationen zu den auf dem lokalen Computer laufenden Prozessen abruft.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Weitere Informationen zum **Get-proc-** Cmdlet finden Sie unter [getproc-Tutorial](./getproc-tutorial.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
