---
title: Parameter hinzufügen zu einem Cmdlet legt | Microsoft-Dokumentation
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
ms.openlocfilehash: d330b9be1da9fbb36be324e68fd6cf2d874fc06b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733810"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Hinzufügen von Parametersätzen zu einem Cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Wissenswerte Fakten über Parametersätze

Windows PowerShell definiert einen Parameter, die als einer Gruppenstatus von Parametern, die zusammen verwendet werden. Durch Gruppieren von den Parametern eines Cmdlets, können Sie ein einzelnes Cmdlet erstellen, das seine Funktionalität, die basierend auf der gibt an, welche Gruppe von Parametern an der Benutzer geändert werden können.

Ein Beispiel für ein Cmdlet, das zwei Parametersätze verwendet, um Funktionen zu definieren ist die `Get-EventLog` -Cmdlet, das von Windows PowerShell bereitgestellt wird. Dieses Cmdlet gibt unterschiedliche Informationen zurück, wenn der Benutzer gibt die `List` oder `LogName` Parameter. Wenn die `LogName` -Parameter angegeben wird, das Cmdlet gibt Informationen zu den Ereignissen in einem bestimmten Ereignisprotokoll zurück. Wenn die `List` -Parameter angegeben wird, mit dem-Cmdlet gibt Informationen über die Log-Dateien selbst (nicht die Ereignisinformationen, die sie enthalten). In diesem Fall die `List` und `LogName` Parameter zu identifizieren, zwei separate Parametersätze.

Zwei wichtige Punkte zu erinnern Parametersätze ist, dass die Windows PowerShell-Laufzeit verwendet nur einen Parameter für eine bestimmte Eingabe festgelegt, und dass jeder Parametersatz mindestens einen Parameter verfügen muss, die für diese Parametersatz eindeutig.

Um diesen letzten Punkt zu veranschaulichen, das Stop-Proc-Cmdlet verwendet drei Parametersätze: `ProcessName`, `ProcessId`, und `InputObject`. All diese Parameter verfügt über einen Parameter, die nicht in den anderen Parameter vorhanden ist. Die Parametersätze können andere Parameter freigeben, aber das Cmdlet verwendet die eindeutigen Parameter `ProcessName`, `ProcessId`, und `InputObject` , welche Parameter zu identifizieren, die die Windows PowerShell-Laufzeit verwendet werden soll.

## <a name="declaring-the-cmdlet-class"></a>Deklarieren Sie die Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren. Bei diesem Cmdlet ist das Lebenszyklus-Verb "Stop" verwendet, da das Cmdlet Systemprozesse beendet. Der Namen der Nomen "Proc" wird verwendet, da das-Cmdlet für Prozesse verwendet werden kann. Beachten Sie, dass der cmdletnamen Verb- und den Namen der Cmdlet-Klasse übernommen werden, in der folgenden Deklaration.

> [!NOTE]
> Weitere Informationen zu genehmigten Verb cmdletnamen, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Der folgende Code ist die Definition der Klasse für dieses Cmdlet Stop-Prozessor.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Deklarieren Sie die Parameter des Cmdlets

Dieses Cmdlet definiert drei Parameter, die erforderlich sind, als Eingabe an das Cmdlet (dieser Parameter definieren auch die Parametersätze), als auch eine `Force` Parameter, der verwaltet wird, was das Cmdlet durchführt und eine `PassThru` Parameter, der bestimmt, ob das Cmdlet sendet eine Ausgabeobjekt über die Pipeline. Standardmäßig wird mit diesem Cmdlet nicht auf ein Objekt über die Pipeline übergeben. Weitere Informationen zu diesen beiden letzten Parameter, finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Deklarieren Sie den Name-Parameter

Dieser Eingabeparameter ermöglicht den Benutzer die Namen der zu beendenden Prozesse an. Beachten Sie, dass die `ParameterSetName` -Schlüsselwort von Attribut der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut gibt an, die `ProcessName` Parametersatz für diesen Parameter.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

Beachten Sie außerdem, dass der Alias "ProcessName" für diesen Parameter angegeben wird.

### <a name="declaring-the-id-parameter"></a>Deklarieren Sie den Id-Parameter

Dieser Eingabeparameter kann der Benutzer geben die Bezeichner der zu beendenden Prozesse an. Beachten Sie, dass die `ParameterSetName` -Schlüsselwort von Attribut der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut gibt an, die `ProcessId` Parametersatz.

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

Beachten Sie außerdem, dass der Alias "ProcessId" für diesen Parameter angegeben wird.

### <a name="declaring-the-inputobject-parameter"></a>Deklarieren Sie den InputObject-Parameter

Dieser Eingabeparameter ermöglicht die Angabe ein input-Objekt, das Informationen über die Prozesse beendet werden, enthält. Beachten Sie, dass die `ParameterSetName` -Schlüsselwort von Attribut der [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut gibt an, die `InputObject` Parametersatz für diesen Parameter.

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

Beachten Sie, dass dieser Parameter kein Alias hat.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Deklarieren von Parametern in mehrere Parametersätze

Obwohl ein unique-Parameter für jeden Parameter vorhanden sein muss, können Parameter mehr als einem Parametersatz angehören. Geben Sie in diesen Fällen "freigegebenen Parameter" ein [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Attributdeklaration für jeweils den Wert, den Parameter gehört. Wenn ein Parameter in der alle Parametersätze, nur einmal das Parameter-Attribut deklarieren und müssen nicht angeben, dass der Parameter Name festgelegt.

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabeverarbeitungsmethode

Jedes Cmdlet eine eingabeverarbeitungsmethode muss überschrieben werden, den meisten Fällen die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode. In diesem Cmdlet die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode wird überschrieben, sodass das Cmdlet eine beliebige Anzahl von Prozessen verarbeitet werden kann. Sie enthält eine Select-Anweisung, die Aufrufe an, dass eine andere Methode festlegen, für die Parameter der Benutzerbasis wurde angegeben.

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

Die Hilfsmethoden, die von der Select-Anweisung aufgerufen werden hier nicht beschrieben, aber Sie können ihre Implementierung in das vollständige Codebeispiel im nächsten Abschnitt sehen.

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample04 Beispiel](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, testen Sie es in der Befehlszeile aus ausführen. Hier sind einige Tests, die zeigen, wie die `ProcessId` und `InputObject` Parameter können verwendet werden, um ihre Parametersätze beim Beenden eines Prozesses zu testen.

- Mit Windows PowerShell, die gestartet, führen Sie das Stop-Proc-Cmdlet mit dem `ProcessId` Parametersatz beim Beenden eines Prozesses, der auf Grundlage seines Bezeichners. In diesem Fall verwendet das Cmdlet die `ProcessId` Parameter festgelegt wird, um den Vorgang zu beenden.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Mit Windows PowerShell, die gestartet, führen Sie das Stop-Proc-Cmdlet mit dem `InputObject` Parameter festgelegt wird, beenden Sie Prozesse für das Editor-Objekt abgerufen, indem die `Get-Process` Befehl.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Siehe auch

[Erstellen ein Cmdlet, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md)

[Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Erweitern die Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
