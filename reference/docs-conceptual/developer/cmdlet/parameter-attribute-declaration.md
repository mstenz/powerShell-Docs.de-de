---
title: Deklaration des Parameter Attributs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365359"
---
# <a name="parameter-attribute-declaration"></a>Attributdeklaration: Parameter

Das Parameter Attribut identifiziert eine öffentliche Eigenschaft der Cmdlet-Klasse als Cmdlet-Parameter.

## <a name="syntax"></a>Syntax

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

der optionale benannte Parameter `Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)). `True` gibt an, dass der Cmdlet-Parameter erforderlich ist. Wenn ein erforderlicher Parameter nicht bereitgestellt wird, wenn das Cmdlet aufgerufen wird, fordert Windows PowerShell den Benutzer auf, einen Parameterwert einzugeben. Der Standardwert ist `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) optionaler benannter Parameter. Gibt den Parametersatz an, zu dem dieser Cmdlet-Parameter gehört. Wenn kein Parametersatz angegeben wird, gehört der Parameter zu allen Parametersätzen.

`Position` ([System. Int32](/dotnet/api/System.Int32)) optionaler benannter Parameter. Gibt die Position des Parameters innerhalb eines Windows PowerShell-Befehls an.

der optionale benannte Parameter `ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)). `True` gibt an, dass der Cmdlet-Parameter seinen Wert von einem Pipeline Objekt annimmt. Geben Sie dieses Schlüsselwort an, wenn das Cmdlet auf das gesamte Objekt zugreift, nicht nur auf eine Eigenschaft des Objekts. Der Standardwert ist `false`.

der optionale benannte Parameter `ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)). `True` gibt an, dass der Cmdlet-Parameter seinen Wert von einer Eigenschaft eines Pipeline Objekts annimmt, das entweder denselben Namen oder denselben Alias wie dieser Parameter hat. Wenn das Cmdlet z. b. über einen `Name`-Parameter verfügt und das Pipeline Objekt auch eine `Name`-Eigenschaft aufweist, wird der Wert der Eigenschaft `Name` dem `Name`-Parameter des Cmdlets zugewiesen. Der Standardwert ist `false`.

der optionale benannte Parameter `ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)). `True` gibt an, dass der Cmdlet-Parameter alle verbleibenden Argumente annimmt, die an das Cmdlet übergeben werden. Der Standardwert ist `false`.

`HelpMessage` optional benannte Parameter. Gibt eine kurze Beschreibung des Parameters an. Windows PowerShell zeigt diese Meldung an, wenn ein Cmdlet ausgeführt wird und kein obligatorischer Parameter angegeben ist.

`HelpMessageBaseName` optional benannte Parameter. Gibt den Speicherort der Ressourcen Bezeichner an. Mit diesem Parameter kann z. b. eine Ressourcenassembly angegeben werden, die Hilfe Meldungen enthält, die Sie lokalisieren möchten.

`HelpMessageResourceId` optional benannte Parameter. Gibt den Ressourcen Bezeichner für eine Hilfe Nachricht an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Deklarieren von Cmdlet-Parametern](./how-to-declare-cmdlet-parameters.md).

- Ein Cmdlet kann eine beliebige Anzahl von Parametern aufweisen. Um jedoch eine bessere Benutzer Leistung zu erzielen, begrenzen Sie die Anzahl der Parameter.

- Parameter müssen für öffentliche, nicht statische Felder oder Eigenschaften deklariert werden. Parameter sollten in Eigenschaften deklariert werden. Die-Eigenschaft muss über einen öffentlichen Set-Accessor verfügen, und wenn das Schlüsselwort "`ValueFromPipeline`" oder "`ValueFromPipelineByPropertyName`" angegeben ist, muss die-Eigenschaft über einen öffentlichen get-Accessor verfügen.

- Wenn Sie Positions Parameter angeben, begrenzen Sie die Anzahl der positionellen Parameter in einem Parameter, der auf weniger als fünf festgelegt ist. Und Positions Parameter müssen nicht zusammenhängend sein. Die Positionen 5, 100 und 250 funktionieren identisch mit den Positionen 0, 1 und 2.

- Wenn das `Position`-Schlüsselwort nicht angegeben ist, muss der Name des Cmdlet-Parameters referenziert werden.

- Beachten Sie bei der Verwendung von Parametersätzen Folgendes:

    - Jeder Parametersatz muss mindestens einen eindeutigen Parameter aufweisen. Ein gutes Cmdlet-Design gibt an, dass dieser eindeutige Parameter nach Möglichkeit auch obligatorisch sein sollte. Wenn das Cmdlet ohne Parameter ausgeführt werden soll, kann der Unique-Parameter nicht obligatorisch sein.

    - Kein Parametersatz sollte mehr als einen positionellen Parameter mit der gleichen Position enthalten.

    - Nur ein Parameter in einem Parametersatz sollte `ValueFromPipeline = true` deklarieren. Mit mehreren Parametern können `ValueFromPipelineByPropertyName = true` definiert werden.

    - Mit mehreren Parametern können `ValueFromPipelineByPropertyName = true` definiert werden.

- Weitere Informationen zu den Richtlinien für Parameternamen finden [Sie unter Cmdlet-Parameternamen](standard-cmdlet-parameter-names-and-types.md).

- Das Parameter Attribut wird von der [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet-Parameter Namen](standard-cmdlet-parameter-names-and-types.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
