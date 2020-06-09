---
title: 'Anhang A: Hilfesyntax'
description: In diesem Artikel wird erläutert, wie Sie die Syntax eines Cmdlets lesen und verstehen, wenn es mit „Get-Help“ dargestellt wird.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437981"
---
# <a name="appendix-a---help-syntax"></a>Anhang A: Hilfesyntax

Das folgende Beispiel zeigt den Abschnitt **SYNTAX** der Hilfe für das Cmdlet `Get-EventLog`.

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

In diesem Beispiel wird nur der relevante Teil der Hilfe angezeigt.

Die Syntax besteht hauptsächlich aus mehreren Sätzen von öffnenden und schließenden Klammern (`[]`). Diese haben zwei unterschiedliche Bedeutungen, je nachdem, wie sie verwendet werden. Alles, was in eckigen Klammern enthalten ist, ist optional, es sei denn, es handelt sich um einen Satz leerer eckiger Klammern (`[]`). Leere eckige Klammern kommen nur nach einem Datentyp vor, z. B. `<string[]>`. Dies bedeutet, dass für einen bestimmten Parameter mehr als ein Wert dieses Typs akzeptiert werden kann.

Der erste Parameter im ersten Parametersatz von `Get-EventLog` ist **LogName**. LogName steht in eckigen Klammern, was bedeutet, dass es sich um einen Positionsparameter handelt. Anders ausgedrückt: Die Angabe des Namens des Parameters selbst ist optional, solange er an der richtigen Position angegeben wird. Die Informationen in den spitzen Klammern (`<>`) hinter dem Parameternamen zeigen an, dass er einen einzelnen **Zeichen folgen**wert benötigt. Der gesamte Parametername und Datentyp stehen nicht in eckigen Klammern, sodass der Parameter **LogName** erforderlich ist, wenn dieser Parametersatz verwendet wird.

```powershell
Get-EventLog [-LogName] <String>
```

Der zweite Parameter ist **InstanceId**. Beachten Sie, dass der Parametername und der Datentyp vollständig in eckigen Klammern stehen. Dies bedeutet, dass der Parameter **InstanceId** optional, nicht obligatorisch ist. Beachten Sie außerdem, dass **InstanceId** von einem eigenen Satz eckiger Klammern umgeben ist. Wie bei dem Parameter **LogName** bedeutet dies, dass dies ein Positionsparameter ist. Es gibt noch einen letzten Satz eckiger Klammern hinter dem Datentyp. Dies bedeutet, dass er mehr als einen Wert in Form eines Arrays oder einer durch Trennzeichen getrennten Liste akzeptieren kann.

```
[[-InstanceId] <Int64[]>]
```

Der zweite Parametersatz verfügt über einen Parameter **Liste**. Dabei handelt es sich um einen Switch-Parameter, weil dem Parameternamen kein Datentyp folgt. Wenn der Parameter **List** angegeben wird, ist der Wert **True**. Wenn er nicht angegeben wird, lautet der Wert **False**.

```
[-List]
```

Die Syntaxinformationen für einen Befehl können auch mithilfe von `Get-Command` unter Verwendung des Parameters **Syntax** abgerufen werden. Dies ist eine praktische Abkürzung, die ich immer verwende. Dies ermöglicht mir, schnell zu lernen, wie ein Befehl verwendet wird, ohne mehrere Seiten mit Hilfeinformationen durchlesen zu müssen. Wenn ich dann trotzdem noch weitere Informationen benötige, verwende ich doch den eigentlichen Hilfeinhalt.

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

Je mehr Sie das Hilfesystem in PowerShell verwenden, desto einfacher wird es, sich alle unterschiedlichen Nuancen zu merken. Bevor Sie es bemerken, wird Ihnen seine Verwendung zur zweiten Natur.
