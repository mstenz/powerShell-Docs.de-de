---
title: Hinzufügen von Parameter Sätzen zu einem Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416310"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Hinzufügen von Parametersätzen zu einem Cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Dinge, die Sie über Parameter Sätze wissen müssen

Windows PowerShell definiert einen Parametersatz als eine Gruppe von Parametern, die zusammenarbeiten. Indem Sie die Parameter eines Cmdlets gruppieren, können Sie ein einzelnes Cmdlet erstellen, das seine Funktionalität basierend auf der vom Benutzer festgelegten Gruppe von Parametern ändern kann.

Ein Beispiel für ein Cmdlet, das zwei Parametersätze verwendet, um verschiedene Funktionen zu definieren, ist das Cmdlet "`Get-EventLog`", das von Windows PowerShell bereitgestellt wird. Dieses Cmdlet gibt andere Informationen zurück, wenn der Benutzer den `List` oder `LogName` Parameter angibt. Wenn der `LogName`-Parameter angegeben wird, gibt das Cmdlet Informationen zu den Ereignissen in einem bestimmten Ereignisprotokoll zurück. Wenn der `List`-Parameter angegeben wird, gibt das Cmdlet Informationen zu den Protokolldateien selbst zurück (nicht zu den darin enthaltenen Ereignis Informationen). In diesem Fall identifizieren die Parameter "`List`" und "`LogName`" zwei separate Parametersätze.

Zwei wichtige Punkte, die bei Parametersätzen beachtet werden sollten, besteht darin, dass die Windows PowerShell-Runtime nur einen Parametersatz für eine bestimmte Eingabe verwendet und jeder Parametersatz mindestens einen Parameter aufweisen muss, der für diesen Parametersatz eindeutig ist.

Um den letzten Punkt zu veranschaulichen, verwendet dieses Cmdlet "Break-proc" drei Parametersätze: `ProcessName`, `ProcessId`und `InputObject`. Jeder dieser Parametersätze verfügt über einen Parameter, der nicht in den anderen Parametersätzen liegt. Die Parametersätze können andere Parameter gemeinsam verwenden, aber das Cmdlet verwendet die eindeutigen Parameter `ProcessName`, `ProcessId`und `InputObject`, um zu ermitteln, welche Parametergruppe von der Windows PowerShell-Laufzeit verwendet werden soll.

## <a name="declaring-the-cmdlet-class"></a>Deklarieren der Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert. Für dieses Cmdlet wird das Lebenszyklus Verb "Stopp" verwendet, da das Cmdlet System Prozesse stoppt. Der Nomen Name "proc" wird verwendet, da das Cmdlet an Prozessen arbeitet. Beachten Sie in der folgenden Deklaration, dass das Cmdlet-Verb und der nominale Name in den Namen der Cmdlet-Klasse reflektiert werden.

> [!NOTE]
> Weitere Informationen zu genehmigten Cmdlet-Verb Namen finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

Der folgende Code stellt die Klassendefinition für dieses Cmdlet "Pause-proc" dar.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Deklarieren der Parameter des Cmdlets

Dieses Cmdlet definiert drei Parameter, die als Eingabe für das Cmdlet erforderlich sind (diese Parameter definieren auch die Parametersätze), sowie einen `Force` Parameter, der das Cmdlet verwaltet, und einen `PassThru` Parameter, der bestimmt, ob das Cmdlet ein Ausgabe Objekt über die Pipeline sendet. Standardmäßig übergibt dieses Cmdlet ein Objekt nicht über die Pipeline. Weitere Informationen zu diesen beiden letzten Parametern finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Deklarieren des Name-Parameters

Dieser Eingabeparameter ermöglicht es dem Benutzer, die Namen der zu beendenden Prozesse anzugeben. Beachten Sie, dass das `ParameterSetName` Attribute-Schlüsselwort des [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributs den für diesen Parameter festgelegten `ProcessName` Parameter angibt.

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Beachten Sie auch, dass der Alias "ProcessName" an diesen Parameter übergeben wird.

### <a name="declaring-the-id-parameter"></a>Deklarieren des ID-Parameters

Dieser Eingabeparameter ermöglicht es dem Benutzer, die Bezeichner der zu beendenden Prozesse anzugeben. Beachten Sie, dass das `ParameterSetName` Attribute-Schlüsselwort des [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributs den `ProcessId` Parametersatz angibt.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Beachten Sie auch, dass der Alias "ProcessId" an diesen Parameter übergeben wird.

### <a name="declaring-the-inputobject-parameter"></a>Deklarieren des Inputobject-Parameters

Dieser Eingabeparameter ermöglicht es dem Benutzer, ein Eingabe Objekt anzugeben, das Informationen über die zu beendenden Prozesse enthält. Beachten Sie, dass das `ParameterSetName` Attribute-Schlüsselwort des [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributs den für diesen Parameter festgelegten `InputObject` Parameter angibt.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Beachten Sie auch, dass dieser Parameter über keinen Alias verfügt.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Deklarieren von Parametern in mehreren Parameter Sätzen

Obwohl für jeden Parametersatz ein eindeutiger Parameter vorhanden sein muss, können Parameter zu mehr als einem Parametersatz gehören. In diesen Fällen muss der Shared-Parameter für jeden Satz, zu dem der Parameter gehört, eine [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut Deklaration angeben. Wenn ein Parameter in allen Parametersätzen enthalten ist, müssen Sie das Parameter Attribut nur einmal deklarieren und müssen nicht den Namen des Parameter Satzes angeben.

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabe Verarbeitungsmethode

Jedes Cmdlet muss eine Eingabe Verarbeitungsmethode überschreiben, meistens handelt es sich hierbei um die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode. In diesem Cmdlet wird die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode überschrieben, sodass das Cmdlet eine beliebige Anzahl von Prozessen verarbeiten kann. Sie enthält eine SELECT-Anweisung, die eine andere Methode aufruft, je nachdem, welchen Parametersatz der Benutzer angegeben hat.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

Die Hilfsmethoden, die von der SELECT-Anweisung aufgerufen werden, werden hier nicht beschrieben, aber Sie können Ihre Implementierung im gesamten Codebeispiel im nächsten Abschnitt sehen.

## <a name="code-sample"></a>Codebeispiel

Den gesamten C# Beispielcode finden Sie unter [StopProcessSample04 Sample](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es über ein Windows PowerShell-Snap-in bei Windows PowerShell registrieren. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet bei Windows PowerShell registriert wurde, testen Sie es, indem Sie es in der Befehlszeile ausführen. Im folgenden finden Sie einige Tests, die zeigen, wie die Parameter `ProcessId` und `InputObject` verwendet werden können, um Ihre Parametersätze zu testen, um einen Prozess zu verhindern.

- Führen Sie in Windows PowerShell das Cmdlet "Break-proc" mit dem `ProcessId`-Parameter aus, um einen Prozess auf der Grundlage des Bezeichners zu unterbinden. In diesem Fall verwendet das Cmdlet den `ProcessId` Parametersatz, um den Prozess zu verhindern.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Führen Sie in Windows PowerShell das Cmdlet "Break-proc" mit dem `InputObject`-Parameter aus, um Prozesse für das vom `Get-Process`-Befehl abgerufene Notepad-Objekt zu verhindern.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md)

[Erstellen eines Windows PowerShell-Cmdlets](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
