---
title: Deklarieren von Cmdlet-Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365679"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Deklarieren von Cmdlet-Parametern

In diesen Beispielen wird gezeigt, wie benannte, positionelle, erforderliche, optionale und Switch-Parameter deklariert werden. Diese Beispiele zeigen auch, wie ein parameteralias definiert wird.

## <a name="how-to-declare-a-named-parameter"></a>Deklarieren eines benannten Parameters

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, lassen Sie das-Schlüsselwort `Position` aus dem-Attribut.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen zum Parameter Attribut finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Deklarieren eines Positions Parameters

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, legen Sie das-Schlüsselwort `Position` auf die Argument Position fest. Der Wert 0 gibt die erste Position an.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen zum Parameter Attribut finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Deklarieren eines obligatorischen Parameters

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, legen Sie das `Mandatory`-Schlüsselwort auf `true` fest.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen zum Parameter Attribut finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>So deklarieren Sie einen optionalen Parameter

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, lassen Sie das-Schlüsselwort `Mandatory` aus.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Deklarieren eines Switch-Parameters

- Definieren Sie eine öffentliche Eigenschaft als Typ " [System. Management. Automation. Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)", und deklarieren Sie dann das Parameter Attribut.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Weitere Informationen zum Parameter Attribut finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Deklarieren eines Parameters mit Aliasen

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Fügen Sie ein Alias Attribut hinzu, das die Aliase für den Parameter auflistet. In diesem Beispiel werden drei Aliase für denselben Parameter definiert. Der erste Alias stellt eine Verknüpfung bereit. Die zweite und dritte Aliase stellen Namen bereit, die Sie für verschiedene Szenarien verwenden können.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen zum Alias Attribut finden Sie unter [Alias Attribut Deklaration](./alias-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Parameter Attribut Deklaration](./parameter-attribute-declaration.md)

[Alias Attribut Deklaration](./alias-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
