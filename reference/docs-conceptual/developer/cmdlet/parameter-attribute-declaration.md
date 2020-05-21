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
ms.openlocfilehash: 7482690c44cdaabf23b886107ac5d112c0fa5c9d
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692390"
---
# <a name="parameter-attribute-declaration"></a>Attributdeklaration: Parameter

Das Parameter Attribut identifiziert eine öffentliche Eigenschaft der Cmdlet-Klasse als Cmdlet-Parameter.

## <a name="syntax"></a>Syntax

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

`Mandatory`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter. `True`Gibt an, dass der Cmdlet-Parameter erforderlich ist. Wenn ein erforderlicher Parameter nicht bereitgestellt wird, wenn das Cmdlet aufgerufen wird, fordert Windows PowerShell den Benutzer auf, einen Parameterwert einzugeben. Der Standardwert ist `false`.

`ParameterSetName`([System. String](/dotnet/api/System.String)) optionaler benannter Parameter. Gibt den Parametersatz an, zu dem dieser Cmdlet-Parameter gehört. Wenn kein Parametersatz angegeben wird, gehört der Parameter zu allen Parametersätzen.

`Position`([System. Int32](/dotnet/api/System.Int32)) optionaler benannter Parameter. Gibt die Position des Parameters innerhalb eines Windows PowerShell-Befehls an.

`ValueFromPipeline`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter. `True`Gibt an, dass der Cmdlet-Parameter seinen Wert von einem Pipeline Objekt annimmt. Geben Sie dieses Schlüsselwort an, wenn das Cmdlet auf das gesamte Objekt zugreift, nicht nur auf eine Eigenschaft des Objekts. Der Standardwert ist `false`.

`ValueFromPipelineByPropertyName`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter. `True`Gibt an, dass der Cmdlet-Parameter seinen Wert von einer Eigenschaft eines Pipeline Objekts annimmt, das entweder denselben Namen oder denselben Alias wie dieser Parameter hat. Wenn das Cmdlet beispielsweise über einen `Name` -Parameter verfügt und das Pipeline Objekt auch über eine- `Name` Eigenschaft verfügt, wird der Wert der-Eigenschaft dem- `Name` `Name` Parameter des Cmdlets zugewiesen. Der Standardwert ist `false`.

`ValueFromRemainingArguments`([System. Boolean](/dotnet/api/System.Boolean)) optionaler benannter Parameter. `True`Gibt an, dass der Cmdlet-Parameter alle verbleibenden Argumente annimmt, die an das Cmdlet übergeben werden. Der Standardwert ist `false`.

`HelpMessage`Optionaler benannter Parameter. Gibt eine kurze Beschreibung des Parameters an. Windows PowerShell zeigt diese Meldung an, wenn ein Cmdlet ausgeführt wird und kein obligatorischer Parameter angegeben ist.

`HelpMessageBaseName`Optionaler benannter Parameter. Gibt den Speicherort der Ressourcen Bezeichner an. Mit diesem Parameter kann z. b. eine Ressourcenassembly angegeben werden, die Hilfe Meldungen enthält, die Sie lokalisieren möchten.

`HelpMessageResourceId`Optionaler benannter Parameter. Gibt den Ressourcen Bezeichner für eine Hilfe Nachricht an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Deklarieren von Cmdlet-Parametern](./how-to-declare-cmdlet-parameters.md).

- Ein Cmdlet kann eine beliebige Anzahl von Parametern aufweisen. Um jedoch eine bessere Benutzer Leistung zu erzielen, begrenzen Sie die Anzahl der Parameter.

- Parameter müssen für öffentliche, nicht statische Felder oder Eigenschaften deklariert werden. Parameter sollten in Eigenschaften deklariert werden. Die-Eigenschaft muss über einen öffentlichen Set-Accessor verfügen, und wenn das- `ValueFromPipeline` oder- `ValueFromPipelineByPropertyName` Schlüsselwort angegeben ist, muss die-Eigenschaft über einen öffentlichen get-Accessor verfügen.

- Wenn Sie Positions Parameter angeben, begrenzen Sie die Anzahl der positionellen Parameter in einem Parameter, der auf weniger als fünf festgelegt ist. Und Positions Parameter müssen nicht zusammenhängend sein. Die Positionen 5, 100 und 250 funktionieren identisch mit den Positionen 0, 1 und 2.

- Wenn das `Position` Schlüsselwort nicht angegeben wird, muss der Name des Cmdlet-Parameters referenziert werden.

- Beachten Sie bei der Verwendung von Parametersätzen Folgendes:

  - Jeder Parametersatz muss mindestens einen eindeutigen Parameter aufweisen. Ein gutes Cmdlet-Design gibt an, dass dieser eindeutige Parameter nach Möglichkeit auch obligatorisch sein sollte. Wenn das Cmdlet ohne Parameter ausgeführt werden soll, kann der Unique-Parameter nicht obligatorisch sein.

  - Kein Parametersatz sollte mehr als einen positionellen Parameter mit der gleichen Position enthalten.

  - Nur ein Parameter in einem Parametersatz muss deklarieren `ValueFromPipeline = true` . Mehrere Parameter können definieren `ValueFromPipelineByPropertyName = true` .

  - Mehrere Parameter können definieren `ValueFromPipelineByPropertyName = true` .

- Weitere Informationen zu den Richtlinien für Parameternamen finden [Sie unter Cmdlet-Parameternamen](standard-cmdlet-parameter-names-and-types.md).

- Das Parameter Attribut wird von der [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Klasse definiert.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet-Parameter Namen](standard-cmdlet-parameter-names-and-types.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
