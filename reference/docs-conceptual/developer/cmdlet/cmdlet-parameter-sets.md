---
title: Cmdlet-Parameter Sätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: dfe747893b4aef6376ea3b12dd79b7c144455ed0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415684"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet-Parametersätze

PowerShell verwendet Parametersätze, damit Sie ein einzelnes Cmdlet schreiben können, das verschiedene Aktionen für verschiedene Szenarien ausführen kann. Parametersätze ermöglichen es Ihnen, dem Benutzer verschiedene Parameter verfügbar zu machen. Und, um basierend auf den vom Benutzer angegebenen Parametern unterschiedliche Informationen zurückzugeben.

## <a name="examples-of-parameter-sets"></a>Beispiele für Parametersätze

Das PowerShell-Cmdlet "`Get-EventLog`" gibt beispielsweise unterschiedliche Informationen zurück, je nachdem, ob der Benutzer den **List** -oder **logName** -Parameter angibt. Wenn der **List** -Parameter angegeben wird, gibt das Cmdlet Informationen zu den Protokolldateien selbst zurück, jedoch nicht zu den darin enthaltenen Ereignis Informationen. Wenn der **logName** -Parameter angegeben wird, gibt das Cmdlet Informationen zu den Ereignissen in einem bestimmten Ereignisprotokoll zurück. Mit den Parametern **List** und **logName** werden zwei separate Parametersätze identifiziert.

## <a name="unique-parameter"></a>Unique-Parameter

Jeder Parametersatz muss über einen eindeutigen Parameter verfügen, der von der PowerShell-Laufzeit verwendet wird, um den entsprechenden Parametersatz verfügbar zu machen. Wenn möglich, sollte der Unique-Parameter ein obligatorischer Parameter sein. Wenn ein Parameter obligatorisch ist, muss der Benutzer den-Parameter angeben, und die PowerShell-Laufzeit verwendet diesen Parameter, um den Parametersatz zu identifizieren. Der Unique-Parameter kann nicht obligatorisch sein, wenn das Cmdlet ohne Angabe von Parametern ausgeführt werden soll.

## <a name="multiple-parameter-sets"></a>Mehrere Parametersätze

In der folgenden Abbildung werden in der linken Spalte drei gültige Parametersätze angezeigt. Der **Parameter a** ist eindeutig für den ersten Parametersatz, der **Parameter B** ist für den zweiten Parametersatz eindeutig, und der **Parameter C** ist für den dritten Parametersatz eindeutig. In der rechten Spalte haben die Parametersätze keinen eindeutigen Parameter.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Parameter Satz Anforderungen

Die folgenden Anforderungen gelten für alle Parametersätze.

- Jeder Parametersatz muss mindestens einen eindeutigen Parameter aufweisen. Wenn möglich, machen Sie diesen Parameter zu einem obligatorischen Parameter.

- Ein Parametersatz, der mehrere Positions Parameter enthält, muss eindeutige Positionen für jeden Parameter definieren. Es können nicht zwei Positions Parameter dieselbe Position angeben.

- Nur ein Parameter in einer Menge kann das `ValueFromPipeline`-Schlüsselwort mit dem Wert `true`deklarieren.
  Mehrere Parameter können das `ValueFromPipelineByPropertyName`-Schlüsselwort mit dem Wert `true`definieren.

- Wenn für einen Parameter kein Parametersatz angegeben ist, gehört der Parameter zu allen Parametersätzen.

> [!NOTE]
> Für ein Cmdlet oder eine Funktion gibt es ein Limit von 32-Parametersätzen.

## <a name="default-parameter-sets"></a>Standardparameter Sätze

Wenn mehrere Parametersätze definiert sind, können Sie das `DefaultParameterSetName`-Schlüsselwort des **Cmdlet** -Attributs verwenden, um den Standardparameter Satz anzugeben. PowerShell verwendet den Standardparameter Satz, wenn der festgelegte Parameter auf der Grundlage der vom Befehl bereitgestellten Informationen nicht bestimmt werden kann. Weitere Informationen zum **Cmdlet** -Attribut finden Sie unter [Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Deklarieren von Parametersätzen

Um einen Parametersatz zu erstellen, müssen Sie das `ParameterSetName`-Schlüsselwort angeben, wenn Sie das **Parameter** Attribut für jeden Parameter im Parametersatz deklarieren. Fügen Sie für Parameter, die mehreren Parametersätzen angehören, ein **Parameter** Attribut für jeden Parametersatz hinzu. Mit diesem Attribut können Sie den Parameter für jeden Parametersatz anders definieren. Beispielsweise können Sie einen Parameter in einem Satz als obligatorisch definieren und optional in einem anderen. Jeder Parametersatz muss jedoch einen eindeutigen Parameter enthalten. Weitere Informationen finden Sie unter [Parameter Attribut Deklaration](parameter-attribute-declaration.md).

Im folgenden Beispiel ist der **username** -Parameter der eindeutige Parameter des `Test01` Parameter Satzes, und der **Computername** -Parameter ist der eindeutige Parameter des `Test02` Parameter Satzes. Der **sharedparam** -Parameter gehört zu beiden Sätzen und ist für den `Test01` Parametersatz obligatorisch, aber für den `Test02` Parametersatz optional.

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
