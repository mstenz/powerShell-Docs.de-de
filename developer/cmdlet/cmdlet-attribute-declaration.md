---
title: -Cmdlet Attributdeklaration | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068622"
---
# <a name="cmdlet-attribute-declaration"></a>Attributdeklaration: Cmdlet

Das Cmdlet-Attribut identifiziert eine Microsoft .NET Framework-Klasse, wie ein Cmdlet und gibt an, die Verb- und verwendet, um das-Cmdlet aufzurufen.

## <a name="syntax"></a>Syntax

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

`VerbName` ([System.String](/dotnet/api/System.String)) erforderlich. Gibt das Cmdlet-Verb. Dieses Verb gibt an, welche Aktion das-Cmdlet. Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md) und [Entwicklungsrichtlinien erforderlich](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) erforderlich. Gibt das Cmdlet-Nomen. Diese Nomen gibt an, die Ressource, der mit dem-Cmdlet verarbeitet wird. Weitere Informationen zu den Cmdlet-Nomen, finden Sie unter [Cmdlet Deklaration](./cmdlet-class-declaration.md) und [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. `True` Gibt an, dass das Cmdlet Aufrufe unterstützt die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode, die mit dem Cmdlet bietet eine Möglichkeit, den Benutzer aufzufordern, bevor eine Aktion, die ändert das System ausgeführt wird. `False`, der Standardwert gibt an, dass das Cmdlet keine Aufrufe unterstützt die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode. Weitere Informationen zu Anforderungen, die Bestätigung finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional benannter Parameter. Gibt an, wenn die Aktion des-Cmdlets durch einen Aufruf von bestätigt werden, damit die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode. [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wird nur aufgerufen, wenn die "confirmimpact" des-Cmdlets (standardmäßig "Mittel") gleich oder größer als der Wert der Wert der `$ConfirmPreference` Variable. Dieser Parameter muss angegeben werden nur dann, wenn die `SupportsShouldProcess` Parameter angegeben ist.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional benannter Parameter. Gibt an, dass die Standardparameter festgelegt, dass die Windows PowerShell-Laufzeit versucht, mit denen sie nicht bestimmen kann, welcher Parametersatz um zu verwenden. Beachten Sie, dass diese Situation lässt, indem Sie den unique-Parameter für die einzelnen Parameter legen Sie einen obligatorischen Parameter machen.

Ist dies ein Fall, in denen Windows PowerShell verwenden, kann nicht den Standardparameter, die festlegen, auch wenn der Name des Parametersatzes ein Standardwert angegeben ist. Die Windows PowerShell-Laufzeit kann nicht zwischen Parametersätze, die ausschließlich anhand von Objekttyp unterscheiden. Z. B. Wenn Sie verwenden einen Parametersatz, der eine Zeichenfolge als den Dateipfad und einen weiteren Satz akzeptiert hat eine **"FileInfo"** Objekt direkt von Windows PowerShell kann nicht bestimmt werden die Werte, die an die Parametersatz verwenden anhand der -Cmdlet, noch wird den Standard-Parametersatz verwendet. Auch wenn Sie ein Standardparameter Name angegeben, löst Windows PowerShell in diesem Fall eine mehrdeutige Parameter Set-Fehlermeldung aus.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. `True` Gibt an, dass das Cmdlet in einer Transaktion verwendet werden kann. Wenn `True` angegeben ist, fügt die Windows PowerShell-Laufzeit die `UseTransaction` Parameter an die Parameterliste des-Cmdlets. `False`, der Standardwert gibt an, mit dem-Cmdlet kann nicht innerhalb einer Transaktion verwendet werden.

## <a name="remarks"></a>Hinweise

- Verb- und die werden zusammen, um Ihre registrierten Cmdlet zu identifizieren und Ihr Cmdlet in einem Skript aufrufen verwendet.

- Wenn das Cmdlet über die Windows PowerShell-Konsole aufgerufen wird, ähnelt der Befehl den folgenden Befehl aus:

**VerbName-NounName**

- Alle Cmdlets, die Ressourcen außerhalb der Windows PowerShell ändern sollte enthalten die `SupportsShouldProcess` -Schlüsselwort, wenn das Cmdlet-Attribut deklariert ist, das dem-Cmdlet aufrufen, kann die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode auf, bevor Sie das Cmdlet die zugehörige Aktion ausführt. Wenn die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aufrufen, gibt `false`, die Aktion nicht durchgeführt werden soll. Weitere Informationen über die Bestätigungs-Anforderungen von generiert die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).

Die `Confirm` und `WhatIf` Cmdlet-Parameter sind nur für Cmdlets, die unterstützen verfügbar [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aufrufen.

## <a name="example"></a>Beispiel

Die folgende Klassendefinition verwendet das Cmdlet-Attribut zum Identifizieren von .NET Framework-Klasse für eine **Get-Proc** -Cmdlet, das Informationen über die auf dem lokalen Computer ausgeführten Prozesse abgerufen.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Weitere Informationen zu den **Get-Proc** -Cmdlet, finden Sie unter [GetProc Tutorial](./getproc-tutorial.md).

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
