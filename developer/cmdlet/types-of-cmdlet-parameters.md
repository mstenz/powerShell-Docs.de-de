---
title: Typen von Cmdlet-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859866"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet-Parametertypen

Dieses Thema beschreibt die verschiedenen Typen von Parametern, die Sie in Cmdlets deklarieren können. Cmdlet-Parameter können mit Feldern fester Breite, benannte, erforderlich, optional oder switch-Parameter.

## <a name="positional-and-named-parameters"></a>Positionelle und benannte Parameter

Alle Cmdlet-Parameter sind entweder die benannten oder positionellen Parameter. Ein benannter Parameter erfordert, dass Sie den Parameternamen und -Argument beim Aufrufen von des-Cmdlets. Ein Positionsparameter erfordert nur, dass Sie in der entsprechenden Reihenfolge die Argumente eingeben. Das System wird dann das erste unbenannte Argument der erste positionelle Parameter zugeordnet. Das System ordnet das zweite unbenannte Argument an den zweiten unbenannten Parameter und So weiter. Standardmäßig werden alle Cmdlet-Parameter Parameter benannt.

Um einen benannten Parameter definieren, lassen die `Position` -Schlüsselwort in der **Parameter** -Attributdeklaration, wie in der folgenden Parameterdeklaration dargestellt.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Um einen Positionsparameter zu definieren, fügen die `Position` Schlüsselwort im Parameter-Attributdeklaration, und geben Sie eine Position. Im folgenden Beispiel wird die `UserName` Parameter als Positionsparameter an Position 0 deklariert ist. Dies bedeutet, dass das erste Argument für den Aufruf automatisch an diesen Parameter gebunden wird.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Gute Cmdlet-Entwurf empfiehlt, dass die am häufigsten verwendeten Parameter als Positionsparameter deklariert werden, sodass der Benutzer nicht den Parameternamen eingeben, wenn das Cmdlet ausgeführt wird.

Positionelle und benannte Parameter akzeptieren, einzelne Argumente oder mehrere Argumente, die durch Kommas getrennt. Mehrere Argumente sind nur zulässig, wenn der Parameter eine Auflistung wie z. B. ein Array von Zeichenfolgen akzeptiert. Sie können positionelle und benannte Parameter in einem Cmdlet kombinieren. In diesem Fall ruft das System zuerst die benannten Argumente ab, und klicken Sie dann versuchen, die verbleibenden zuordnen unbenannte Argumente für die Positionsparameter.

Die folgenden Befehle demonstrieren die verschiedenen Möglichkeiten, in dem Sie, für einzelne und mehrere Argumente für die Parameter von angeben können, der `Get-Command` Cmdlet. Beachten Sie, dass in den letzten zwei Beispielen **-Namen** muss nicht angegeben werden, da die `Name` Parameter als Positionsparameter definiert ist.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Obligatorischen und optionalen Parametern

Sie können auch die Cmdlet-Parameter als obligatorisch oder optional Parameter definieren. (Ein obligatorischen Parameter muss angegeben werden, bevor die Windows PowerShell-Laufzeit das Cmdlet aufruft.)  Standardmäßig werden Parameter als optional definiert.

Um einen obligatorischen Parameter zu definieren, fügen die `Mandatory` Schlüsselwort im Parameter-Attributdeklaration, und legen Sie ihn auf `true`, wie in der folgenden Parameterdeklaration dargestellt.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Um einen optionalen Parameter zu definieren, lassen die `Mandatory` -Schlüsselwort in der **Parameter** -Attributdeklaration, wie in der folgenden Parameterdeklaration dargestellt.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Switch-Parameter

Windows PowerShell bietet eine [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) Typ, der können Sie einen Parameter definieren, deren Wert wird automatisch festgelegt, um `false` , wenn der Parameter nicht angegeben wird, wenn das Cmdlet wird aufgerufen. Verwenden Sie nach Möglichkeit anstelle von booleschen Parametern Switch-Parameter.

Betrachten Sie das folgende Beispiel aus. Mehrere Windows PowerShell-Cmdlets übergeben werden standardmäßig kein Ausgabeobjekt entlang der Pipeline. Diese Cmdlets haben jedoch eine `PassThru` switch-Parameter, die das Standardverhalten überschrieben. Wenn die `PassThru` Parameter angegeben ist, wenn diese Cmdlets aufgerufen werden, das Cmdlet gibt ein Ausgabeobjekt an die Pipeline zurück.

Bei Bedarf den Parameter, um einen Standardwert besitzen `true` der Parameter im Aufruf nicht angegeben ist, berücksichtigen Sie die Bedeutung von der Parameter umkehren. Beispiel, statt das Parameter-Attribut in einen booleschen Wert der `true`, deklarieren Sie die Eigenschaft als die [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) geben, und legen Sie dann auf den Standardwert des Parameters, der `false`.

Um einen Switch-Parameter zu definieren, deklarieren Sie die Eigenschaft als die [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) eingeben, wie im folgenden Beispiel gezeigt.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Damit wird das Cmdlet für den Parameter zu reagieren, wenn es angegeben ist, verwenden Sie die folgende Struktur in einem der eingabeverarbeitungsmethoden.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
