---
title: 'Gewusst wie: Deklarieren von Cmdlet-Parameter | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067914"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Deklarieren von Cmdlet-Parametern

Diese Beispiele zeigen, wie Sie benannte, mit Feldern fester Breite, erforderlich, optional zu deklarieren und switch-Parameter. Diese Beispiele zeigen auch einen parameteralias definieren.

## <a name="how-to-declare-a-named-parameter"></a>Beschreibt, wie einen benannten Parameter deklariert

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, weglassen der `Position` Schlüsselwort aus dem Attribut.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Gewusst wie: Deklarieren eines Parameters mit Feldern fester Breite

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, setzen die `Position` Schlüsselwort, um die Position des formatlistenarguments. Der Wert 0 gibt an, die erste Position.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Wie Sie einen obligatorischen Parameter deklarieren

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, setzen die `Mandatory` Schlüsselwort `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Wie Sie einen optionalen Parameter deklarieren

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Wenn Sie das Parameter-Attribut hinzufügen, weglassen der `Mandatory` Schlüsselwort.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Gewusst wie: deklarieren einen Switch-Parameter

- Definieren Sie eine öffentliche Eigenschaft als Typ [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), und klicken Sie dann das Parameter-Attribut zu deklarieren.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Gewusst wie: Deklarieren eines Parameters mit Aliasen

- Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt. Fügen Sie ein Alias-Attribut, das die Aliase für den Parameter enthält. In diesem Beispiel werden drei Aliase für den gleichen Parameter definiert. Der erste Alias stellt eine Verknüpfung. Die zweite und dritte Aliase Geben Sie den Namen, die Sie für verschiedene Szenarien verwenden können.

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

Weitere Informationen zu den Alias-Attribut, finden Sie unter [Alias Attributdeklaration](./alias-attribute-declaration.md).

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Parameterdeklaration-Attribut](./parameter-attribute-declaration.md)

[Alias-Attributdeklaration](./alias-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
