---
title: Deklarieren von Parameter Sätzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365609"
---
# <a name="how-to-declare-parameter-sets"></a>Deklarieren von Parametersätzen

In diesem Beispiel wird gezeigt, wie zwei Parametersätze definiert werden, wenn Sie die Parameter für ein Cmdlet deklarieren. Jeder Parametersatz verfügt sowohl über einen eindeutigen Parameter als auch über einen freigegebenen Parameter, der von beiden Parametersätzen verwendet wird. Weitere Informationen zu Parametersätzen, einschließlich der Angabe des Standardparameter Satzes, finden Sie unter [Cmdlet-Parametersätze](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Definieren Sie nach Möglichkeit den eindeutigen Parameter eines Parameter Satzes als erforderlichen Parameter. Wenn Sie jedoch möchten, dass das Cmdlet ohne Angabe von Parametern ausgeführt wird, kann der Unique-Parameter ein optionaler Parameter sein. Beispielsweise ist der Unique-Parameter des Cmdlets "`Get-Command`" optional.

## <a name="how-to-define-two-parameter-sets"></a>Definieren von zwei Parameter Sätzen

1. Fügen Sie dem Parameter-Attribut für den Unique-Parameter des ersten Parameter Satzes das `ParameterSet`-Schlüsselwort hinzu.

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

2. Fügen Sie dem Parameter-Attribut für den Unique-Parameter des zweiten Parameter Satzes das `ParameterSet`-Schlüsselwort hinzu.

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

3. Fügen Sie für den Parameter, der zu beiden Parametersätzen gehört, ein Parameter Attribut für jeden Parametersatz hinzu, und fügen Sie dann jedem Satz das `ParameterSet`-Schlüsselwort hinzu. In jedem Parameter Attribut können Sie angeben, wie dieser Parameter definiert wird. Ein Parameter kann in einem Satz optional sein und in einem anderen obligatorisch sein.

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

[Cmdlet-Parameter Sätze](./cmdlet-parameter-sets.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
