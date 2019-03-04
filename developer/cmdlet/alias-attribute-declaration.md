---
title: Alias-Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855046"
---
# <a name="alias-attribute-declaration"></a>Attributdeklaration: Alias

Der Alias-Attribut ermöglicht den Benutzer, unterschiedliche Namen für die Cmdlet-Parameter anzugeben. Aliase können verwendet werden, um die Tastenkombinationen für einen Parameternamen angeben, oder bieten andere Namen, die für verschiedene Szenarien geeignet sind.

## <a name="syntax"></a>Syntax

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parameter

`aliasName` (Testeigenschaftentyp Erforderlich. Gibt einen Satz von durch Trennzeichen getrennte Aliasnamen für die Cmdlet-Parameter.

## <a name="remarks"></a>Hinweise

- Der Alias-Attribut wird mit dem Parameter-Attribut verwendet, wenn Sie einen Cmdlet-Parameter angeben. Weitere Informationen dazu, wie Sie diese Attribute deklarieren können, finden Sie unter [wie Cmdlet-Parametern deklarieren](./how-to-declare-cmdlet-parameters.md).

- Jeder Aliasname muss innerhalb eines Cmdlets eindeutig sein. Windows PowerShell führt keine Überprüfung auf doppelte Aliasnamen durch.

- Der Alias-Attribut wird einmal für jeden Parameter in einem Cmdlet verwendet.

- Der Alias-Attribut wird definiert, durch die [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) Klasse.

## <a name="see-also"></a>Weitere Informationen

[Parameteraliase](./parameter-aliases.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
