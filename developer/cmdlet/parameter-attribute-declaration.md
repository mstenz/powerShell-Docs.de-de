---
title: Parameter-Attributdeklaration | Microsoft-Dokumentation
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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735133"
---
# <a name="parameter-attribute-declaration"></a>Attributdeklaration: Parameter

Der Parameter-Attribut identifiziert eine öffentliche Eigenschaft von der Cmdlet-Klasse als Cmdlet-Parameter.

## <a name="syntax"></a>Syntax

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parameter

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. `True` Gibt an, dass die Cmdlet-Parameter erforderlich ist. Wenn ein erforderlicher Parameter nicht angegeben wird, wenn das-Cmdlet aufgerufen wird, fordert Windows PowerShell den Benutzer einen Parameterwert an. Die Standardeinstellung ist `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional benannter Parameter. Gibt an, dass der Parameter festgelegt, dass dieses Cmdlet-Parameter gehört. Wenn kein Parametersatz angegeben wird, gehört der Parameter alle Parametersätze.

`Position` ([System. Int32](/dotnet/api/System.Int32)) Optional benannter Parameter. Gibt die Position des Parameters in einem Windows PowerShell-Befehl.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. `True` Gibt an, dass es sich bei der Cmdlet-Parameter den Wert von einem Pipelineobjekt akzeptiert. Geben Sie dieses Schlüsselwort ein, wenn das Cmdlet die vollständige greift auf Objekt "," nicht nur eine Eigenschaft des Objekts. Die Standardeinstellung ist `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. `True` Gibt an, dass der Cmdlet-Parameter den Wert aus einer Eigenschaft eines Objekts der Pipeline annimmt, der den gleichen Namen oder den gleichen Alias als dieser Parameter aufweist. Wenn das-Cmdlet hat beispielsweise eine `Name` Parameter und das Pipelineobjekt verfügt auch über eine `Name` -Eigenschaft wird der Wert des der `Name` Eigenschaft zugewiesen wird der `Name` -Parameter des Cmdlets. Die Standardeinstellung ist `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter. `True` Gibt an, dass die Cmdlet-Parameter. alle übrigen Argumente akzeptiert, die an das Cmdlet übergeben werden. Die Standardeinstellung ist `false`.

`HelpMessage` Optional benannter Parameter. Gibt eine kurze Beschreibung des Parameters an. Windows PowerShell zeigt diese an, wenn ein Cmdlet ausgeführt wird, und ein obligatorischen Parameter nicht angegeben ist.

`HelpMessageBaseName` Optional benannter Parameter. Gibt den Speicherort, in dem Ressourcen-IDs gespeichert. Dieser Parameter kann beispielsweise eine Ressourcenassembly angeben, die Hilfe zu Meldungen enthält, die Sie lokalisieren möchten.

`HelpMessageResourceId` Optional benannter Parameter. Gibt den Ressourcenbezeichner für eine hilfemeldung an.

## <a name="remarks"></a>Hinweise

- Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Cmdlet-Parametern deklarieren](./how-to-declare-cmdlet-parameters.md).

- Ein Cmdlet kann eine beliebige Anzahl von Parametern haben. Allerdings für eine bessere benutzererfahrung, begrenzen Sie die Anzahl von Parametern an.

- Parameter müssen auf öffentlichen nicht statischen Felder oder Eigenschaften deklariert werden. Parameter sollten Eigenschaften deklariert werden. Die Eigenschaft muss einen öffentlichen Set-Accessor, haben und wenn die `ValueFromPipeline` oder `ValueFromPipelineByPropertyName` -Schlüsselwort angegeben ist, die Eigenschaft muss einen öffentlichen Get-Accessor haben.

- Wenn Sie positionelle Parameter angeben, die Anzahl von Positionsparametern, die in einem Parameter, die auf weniger als fünf festlegen. Und Positionsparameter müssen nicht zusammenhängend sein. Positionen 5, 100 und 250 funktionieren genauso wie die Positionen 0, 1 und 2.

- Wenn die `Position` -Schlüsselwort ist nicht angegeben, die der Cmdlet-Parameter muss mit seinem Namen verwiesen werden.

- Wenn Sie Parameter verwenden, beachten Sie Folgendes:

    - Jeder Parametersatz müssen mindestens eine unique-Parameter. Gute Cmdlet-Design gibt an, dass dieser eindeutige Parameter auch nach Möglichkeit obligatorisch sein soll. Wenn Ihr Cmdlet ohne Parameter ausgeführt werden soll, darf nicht der unique-Parameter erforderlich sein.

    - Keine Parametersatz sollte mehr als eine positionelle Parameter mit der gleichen Position enthalten.

    - Sollte nur einen Parameter in einem Parametersatz deklarieren `ValueFromPipeline = true`. Es können mehrere Parameter definieren `ValueFromPipelineByPropertyName = true`.

    - Es können mehrere Parameter definieren `ValueFromPipelineByPropertyName = true`.

- Weitere Informationen zu den Richtlinien für Parameternamen verwendet, finden Sie unter [Cmdlet-Parameternamen](standard-cmdlet-parameter-names-and-types.md).

- Der Parameter-Attribut wird definiert, durch die [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Klasse.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet-Parameternamen](standard-cmdlet-parameter-names-and-types.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
