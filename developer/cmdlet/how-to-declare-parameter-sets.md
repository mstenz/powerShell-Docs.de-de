---
title: 'Gewusst wie: Deklarieren von Parametersätzen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859696"
---
# <a name="how-to-declare-parameter-sets"></a>Deklarieren von Parametersätzen

Dieses Beispiel zeigt, wie zwei Parametersätze definiert werden, wenn Sie die Parameter für ein Cmdlet zu deklarieren. Jeder Parametersatz sind eine unique-Parameter und freigegebene Parameter, der von beiden Parametersätze verwendet wird. Weitere Informationen zu Parametern Mengen, einschließlich der Parameter den Standardsatz an finden Sie unter [Cmdlet Parametersätze](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Wann immer möglich, definieren Sie den unique-Parameter eines Parameters, der als ein erforderlicher Parameter festlegen. Wenn Sie Ihr Cmdlet ohne Angabe von Parametern ausführen möchten, kann allerdings der unique-Parameter einen optionalen Parameter sein. Z. B. die unique-Parameter von der `Get-Command` Cmdlet ist optional.

## <a name="how-to-define-two-parameter-sets"></a>Gewusst wie: Definieren von zwei Parametersätze

1. Hinzufügen der `ParameterSet` Schlüsselwort, das Parameter-Attribut eindeutig als Parameter für den ersten Parametersatz.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Hinzufügen der `ParameterSet` Schlüsselwort, das Parameter-Attribut eindeutig als Parameter für den zweiten Parametersatz.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Für den Parameter, die zu beiden Parametersätzen gehört, für jeden Parameter einen Parameter-Attribut hinzufügen und dann die `ParameterSet` Schlüsselwort, um jeden Satz. In jedem Parameter-Attribut können Sie angeben, wie dieser Parameter definiert ist. Ein Parameter kann optional in einem Satz und in einer anderen obligatorisch sein.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter legt fest](./cmdlet-parameter-sets.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
