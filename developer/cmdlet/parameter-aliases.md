---
title: Parameteraliase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853316"
---
# <a name="parameter-aliases"></a>Parameteraliase

Cmdlet-Parameter können auch Aliase aufweisen. Sie können die Aliase anstatt den Parameternamen verwenden, eingeben oder geben Sie den Parameter in einem Befehl.

## <a name="benefits-of-using-aliases"></a>Vorteile der Verwendung von Aliasen

Hinzufügen von Aliasen zu Parameter bietet die folgenden Vorteile.

- Sie können eine Verknüpfung bereitstellen, sodass der Benutzer nicht der vollständige Parametername verwendet wird, wenn das-Cmdlet aufgerufen wird. Beispielsweise können Sie den Alias "CN" statt des Parameternamens "ComputerName".

- Sie können mehrere Aliasnamen definieren, sollten Sie andere Namen für den gleichen Parameter bereitzustellen. Sie möchten mehrere Aliase zu definieren, wenn man arbeiten mit mehreren Benutzergruppen, die auf dieselben Daten auf unterschiedliche Weise zu verweisen.

- Sie können die Kompatibilität Abwärtskompatibilität für vorhandene Skripts angeben, wenn ändert sich der Name eines Parameters.

- Verwenden Sie die Alias-Attribut zusammen mit dem Attribut ValueFromPipelineByName, können Sie einen Parameter definieren, der Ihr Cmdlet zum Binden an verschiedene Objekttypen ermöglicht. Angenommen Sie, Sie haben zwei Objekte unterschiedlicher Typen und das erste Objekt eine Eigenschaft Writer und das zweite Objekt hatten eine editoreigenschaft. Hätte Ihr Cmdlet Parameter, die Autor und Editor-Aliase und mit dem Cmdlet akzeptiert Pipelineeingabe basierend auf den Eigenschaftennamen, Ihr Cmdlet konnte auf beide Objekte, die mit den zwei Parameter Aliasen binden.

Weitere Informationen zu Aliasen, die mit bestimmten Parametern verwendet werden können, finden Sie unter [allgemeine Parameternamen](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definieren Parameteraliase

Deklarieren Sie die Alias-Attribut, um einen Alias für einen Parameter zu definieren, wie in der folgenden Parameterdeklaration dargestellt. In diesem Beispiel werden mehrere Aliase für den gleichen Parameter definiert. (Weitere Informationen finden Sie unter[wie Cmdlet-Parametern deklarieren](./how-to-declare-cmdlet-parameters.md).)

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

## <a name="see-also"></a>Weitere Informationen

[Allgemeine Parameternamen](./common-parameter-names.md)

[Gewusst wie: Deklarieren von Cmdlet-Parameter](./how-to-declare-cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
