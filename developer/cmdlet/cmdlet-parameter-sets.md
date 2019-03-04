---
title: Cmdlet-Parameter legt fest | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857266"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet-Parametersätze

Windows PowerShell verwendet die Parameter legt fest, sodass Sie ein einzelnes Cmdlet schreiben, das für verschiedene Szenarien verschiedene Aktionen ausführen können. Parametersätze können Sie verschiedene Parameter für den Benutzer verfügbar zu machen und anderen Informationen, die auf Grundlage der vom Benutzer angegebene Parameter zurückgegeben werden sollen.

## <a name="examples-of-parameter-sets"></a>Beispiele für die Parametersätze

Z. B. die `Get-EventLog` Cmdlet (bereitgestellt vom Windows PowerShell) gibt unterschiedliche Informationen, je nachdem, ob der Benutzer gibt die `List` oder `LogName` Parameter. Wenn die `List` -Parameter angegeben wird, mit dem-Cmdlet gibt Informationen zu den Protokolldateien selbst jedoch nicht die darin enthaltenen Informationen. Wenn die `LogName` -Parameter angegeben wird, das Cmdlet gibt Informationen zu den Ereignissen in einem bestimmten Ereignisprotokoll zurück. Die `List` und `LogName` Parameter zu identifizieren, zwei separate Parametersätze.

## <a name="unique-parameter"></a>Unique-Parameter

Jeder Parametersatz muss es sich um einen eindeutigen Parameter aufweisen, den die Windows PowerShell-Laufzeit verwenden können, um den entsprechenden Parametersatz verfügbar zu machen. Wenn möglich, muss die unique-Parameter ein erforderlicher Parameter. Wenn ein Parameter obligatorisch ist, zum Angeben des Parameters wird der Benutzer gezwungen, und die Windows PowerShell-Laufzeit kann diesen Parameter verwenden, um den Parametersatz verwenden identifizieren. Die unique-Parameter ist nicht erforderlich, wenn Sie Ihr Cmdlet ohne Angabe von Parametern ausgeführt werden sollen.

## <a name="multiple-parameter-sets"></a>Mehrere Parametersätze

In der folgenden Abbildung zeigt die linke Spalte drei gültigen Parametersätze an. Ein-Parameter gilt nur für den ersten Parametersatz, B-Parameter gilt nur für den zweiten Parametersatz und C-Parameter gilt nur für den dritten Parametersatz. Allerdings müssen in der rechten Spalte, die Parametersätze einen unique-Parameter keine.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Parametersatz Anforderungen

Die folgenden Anforderungen gelten für alle Parametersätze.

- Jeder Parametersatz müssen mindestens eine unique-Parameter. Wenn möglich, stellen Sie diesen Parameter einen obligatorischen Parameter.

- Ein Parametersatz, der mehrere positionelle Parameter enthält, muss eindeutige Positionen für jeden Parameter definieren. Keine zwei positionelle Parameter können die gleiche Position angeben.

- Kann nur einen Parameter in einem Satz deklarieren die `ValueFromPipeline` Schlüsselwort mit einem Wert von `true`. Es können mehrere Parameter definieren die `ValueFromPipelineByPropertyName` Schlüsselwort mit einem Wert von `true`.

- Wenn kein Parameter festgelegt, die für einen Parameter angegeben wird, gehört der Parameter alle Parametersätze.

## <a name="default-parameter-sets"></a>Standard-Parametersätze

Wenn mehrere Parametersätze definiert sind, können Sie die `DefaultParameterSetName` -Schlüsselwort von der Cmdlet-Attribut, um den Standardsatz der Parameter anzugeben. Windows PowerShell verwendet die Standardparameter festgelegt, wenn sie nicht bestimmen kann, abhängig von den Angaben, die mit dem Befehl der Parametersatz verwenden. Weitere Informationen zu den Cmdlet-Attribut, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Deklarieren von Parametersätzen

Um einen Parametersatz erstellen zu können, müssen Sie geben die `ParameterSetName` -Schlüsselwort, wenn Sie das Parameter-Attribut für jeden Parameter im Parametersatz deklarieren. Für Parameter, die mehrere Parametersätze angehören, fügen Sie ein Parameterattribut für jeden Parameter festgelegt. Dadurch können Sie den Parameter für jeden Parametersatz unterschiedlich definieren. Beispielsweise können Sie einen Parameter als in einem Satz obligatorischen und optionalen, in einer anderen definieren. Allerdings muss jeder Parametersatz eine unique-Parameter enthalten.

Im folgenden Beispiel die `UserName` Parameter ist der eindeutige Parameter die Menge an Test01-Parameter, und die `ComputerName` Parameter ist der unique-Parameter von der Test02 Parameter festgelegt. Die `SharedParam` Parameter gehört zu beiden Sätzen und ist erforderlich, damit der Test01-Parameter, die aber für den Parametersatz Test02 optional festgelegt.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
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
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```