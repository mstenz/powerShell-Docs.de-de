---
title: Typen von Cmdlet-Parametern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369309"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet-Parametertypen

In diesem Thema werden die verschiedenen Parametertypen beschrieben, die Sie in Cmdlets deklarieren können. Cmdlet-Parameter können Positions-, benannte, erforderliche, optionale oder Switch-Parameter sein.

## <a name="positional-and-named-parameters"></a>Positions Parameter und benannte Parameter

Alle Cmdlet-Parameter sind entweder benannte oder positionelle Parameter. Ein benannter Parameter erfordert, dass Sie den Parameternamen und das Argument eingeben, wenn Sie das Cmdlet aufrufen. Ein Positions Parameter erfordert nur, dass Sie die Argumente in relativer Reihenfolge eingeben. Das System ordnet dann das erste unbenannte Argument dem ersten Positions Parameter zu. Das System ordnet das zweite unbenannte Argument dem zweiten unbenannten Parameter zu usw. Standardmäßig sind alle Cmdlet-Parameter benannte Parameter.

Um einen benannten Parameter zu definieren, lassen Sie das `Position`-Schlüsselwort in der Deklaration des **Parameter** Attributs aus, wie in der folgenden Parameter Deklaration gezeigt.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Um einen Positions Parameter zu definieren, fügen Sie das Schlüsselwort `Position` in der Deklaration des Parameter Attributs hinzu, und geben Sie dann eine Position an. Im folgenden Beispiel wird der Parameter "`UserName`" als Positions Parameter mit der Position 0 deklariert. Dies bedeutet, dass das erste Argument des Aufrufes automatisch an diesen Parameter gebunden wird.

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
> Ein gutes Cmdlet-Design empfiehlt, dass die am häufigsten verwendeten Parameter als Positions Parameter deklariert werden, damit der Benutzer den Parameternamen nicht eingeben muss, wenn das Cmdlet ausgeführt wird.

Positions Parameter und benannte Parameter akzeptieren einzelne Argumente oder mehrere Argumente, die durch Kommas getrennt sind. Mehrere Argumente sind nur zulässig, wenn der Parameter eine Auflistung, z. b. ein Array von Zeichen folgen, akzeptiert. Sie können positionelle und benannte Parameter im gleichen Cmdlet kombinieren. In diesem Fall ruft das System zuerst die benannten Argumente ab und versucht dann, die verbleibenden unbenannten Argumente den Positions Parametern zuzuordnen.

Die folgenden Befehle zeigen die verschiedenen Methoden, mit denen Sie einzelne und mehrere Argumente für die Parameter des Cmdlets "`Get-Command`" angeben können. Beachten Sie, dass in den letzten beiden Beispielen " **-Name** " nicht angegeben werden muss, da der Parameter "`Name`" als Positions Parameter definiert ist.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Obligatorische und optionale Parameter

Sie können auch Cmdlet-Parameter als obligatorische oder optionale Parameter definieren. (Ein obligatorischer Parameter muss angegeben werden, bevor das Cmdlet von der Windows PowerShell-Laufzeit aufgerufen wird.)  Standardmäßig werden Parameter als optional definiert.

Um einen obligatorischen Parameter zu definieren, fügen Sie das Schlüsselwort `Mandatory` in der Deklaration des Parameter Attributs hinzu, und legen Sie es auf `true` fest, wie in der folgenden Parameter Deklaration gezeigt.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Um einen optionalen Parameter zu definieren, lassen Sie das Schlüsselwort "`Mandatory`" in der Deklaration des **Parameter** Attributs aus, wie in der folgenden Parameter Deklaration gezeigt.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parameter wechseln

Windows PowerShell stellt einen [System. Management. Automation. Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) -Typ bereit, mit dem Sie einen Parameter definieren können, dessen Wert automatisch auf `false` festgelegt wird, wenn der Parameter nicht angegeben wird, wenn das Cmdlet aufgerufen wird. Verwenden Sie nach Möglichkeit anstelle von booleschen Parametern Switchparameter.

Sehen Sie sich das folgende Beispiel an. Standardmäßig übergeben mehrere Windows PowerShell-Cmdlets kein Ausgabe Objekt in der Pipeline. Diese Cmdlets verfügen jedoch über einen `PassThru`-Schalter Parameter, der das Standardverhalten überschreibt. Wenn der Parameter "`PassThru`" angegeben wird, wenn diese Cmdlets aufgerufen werden, gibt das Cmdlet ein Ausgabe Objekt an die Pipeline zurück.

Wenn Sie möchten, dass der-Parameter den Standardwert `true` hat, wenn der-Parameter nicht im-Befehl angegeben ist, sollten Sie den Sinn des Parameters umkehren. Anstatt das Parameter Attribut Beispiels mäßig auf einen booleschen Wert `true` festzulegen, deklarieren Sie die Eigenschaft als [System. Management. Automation. Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) -Typ, und legen Sie dann den Standardwert des Parameters auf `false` fest.

Um einen Switch-Parameter zu definieren, deklarieren Sie die Eigenschaft als [System. Management. Automation. Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) -Typ, wie im folgenden Beispiel gezeigt.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Um das Cmdlet für den Parameter zu verwenden, wenn es angegeben ist, verwenden Sie die folgende Struktur in einer der Eingabe Verarbeitungsmethoden.

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
