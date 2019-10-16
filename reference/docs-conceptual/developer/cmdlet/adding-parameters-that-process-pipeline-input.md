---
title: Hinzufügen von Parametern, die Pipeline Eingaben verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364599"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Hinzufügen von Parametern, die Pipelineeingaben verarbeiten

Eine Eingabe Quelle für ein Cmdlet ist ein Objekt in der Pipeline, das aus einem Upstream-Cmdlet stammt. In diesem Abschnitt wird beschrieben, wie Sie dem Get-proc-Cmdlet (beschrieben unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)) einen Parameter hinzufügen, damit das Cmdlet Pipeline Objekte verarbeiten kann.

Dieses Get-proc-Cmdlet verwendet einen `Name`-Parameter, der Eingaben von einem Pipeline Objekt akzeptiert, Prozessinformationen von dem lokalen Computer auf der Grundlage der angegebenen Namen abruft und dann Informationen zu den Prozessen in der Befehlszeile anzeigt.

## <a name="defining-the-cmdlet-class"></a>Definieren der Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert. Dieses Cmdlet ruft Prozessinformationen ab, daher lautet der hier gewählte Verb Name "Get". (Fast jede Art von Cmdlet, das Informationen abrufen kann, kann die Befehlszeilen Eingabe verarbeiten.) Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

Im folgenden finden Sie die Definition für dieses Get-proc-Cmdlet. Einzelheiten zu dieser Definition finden Sie unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definieren von Eingaben aus der Pipeline

In diesem Abschnitt wird beschrieben, wie Eingaben aus der Pipeline für ein Cmdlet definiert werden. Dieses Cmdlet "Get-proc" definiert eine Eigenschaft, die den Parameter "`Name`" darstellt, wie unter [Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](./adding-parameters-that-process-command-line-input.md)beschrieben. (In diesem Thema finden Sie allgemeine Informationen zum Deklarieren von Parametern.)

Wenn jedoch ein Cmdlet Pipeline Eingaben verarbeiten muss, muss die Parameter von der Windows PowerShell-Laufzeit an die Eingabewerte gebunden werden. Hierzu müssen Sie das Schlüsselwort "`ValueFromPipeline`" hinzufügen oder das Schlüsselwort "`ValueFromPipelineByProperty`" der [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut Deklaration hinzufügen. Geben Sie das `ValueFromPipeline`-Schlüsselwort an, wenn das Cmdlet auf das gesamte Eingabe Objekt zugreift. Geben Sie den `ValueFromPipelineByProperty` an, wenn das Cmdlet nur auf eine Eigenschaft des Objekts zugreift.

Im folgenden finden Sie die Parameter Deklaration für den `Name`-Parameter dieses Get-proc-Cmdlets, das Pipeline Eingaben annimmt.

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

In der vorherigen Deklaration wird das `ValueFromPipeline`-Schlüsselwort auf `true` festgelegt, damit die Windows PowerShell-Laufzeit den Parameter an das eingehende Objekt bindet, wenn das Objekt dem gleichen Typ wie der Parameter entspricht, oder, wenn es in denselben Typ umgewandelt werden kann. Das Schlüsselwort `ValueFromPipelineByPropertyName` ist auch auf `true` festgelegt, damit die Windows PowerShell-Laufzeit das eingehende Objekt auf eine `Name`-Eigenschaft überprüft. Wenn das eingehende Objekt eine solche Eigenschaft aufweist, bindet die Laufzeit den `Name`-Parameter an die `Name`-Eigenschaft des eingehenden Objekts.

> [!NOTE]
> Die Einstellung des `ValueFromPipeline`-Attribut Schlüsselworts für einen Parameter hat Vorrang vor der Einstellung für das Schlüsselwort `ValueFromPipelineByPropertyName`.

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabe Verarbeitungsmethode

Wenn das Cmdlet Pipeline Eingaben verarbeiten soll, müssen die entsprechenden Eingabe Verarbeitungsmethoden überschrieben werden. Die grundlegenden Eingabe Verarbeitungsmethoden werden beim [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)eingeführt.

Dieses Cmdlet "Get-proc" überschreibt die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, um die vom Benutzer oder einem Skript bereitgestellten `Name`-Parameter Eingaben zu verarbeiten. Diese Methode erhält die Prozesse für die einzelnen angeforderten Prozessnamen oder alle Prozesse, wenn kein Name angegeben wird. Beachten Sie, dass innerhalb von [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)der Aufrufe von [Write Object (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) der Ausgabe Mechanismus zum Senden von Ausgabe Objekten an die Pipeline ist. Der zweite Parameter dieses Aufrufes (`enumerateCollection`) ist auf `true` festgelegt, um der Windows PowerShell-Laufzeit mitzuteilen, dass das Array von Prozess Objekten aufgelistet und jeweils ein Prozess in die Befehlszeile geschrieben werden soll.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Code Beispiel

Den gesamten C# Beispielcode finden Sie unter [GetProcessSample03 Sample](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem Sie ein Cmdlet implementiert haben, muss es über ein Windows PowerShell-Snap-in in Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet bei Windows PowerShell registriert wurde, testen Sie es, indem Sie es in der Befehlszeile ausführen. Testen Sie z. b. den Code für das Beispiel-Cmdlet. Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Geben Sie an der Windows PowerShell-Eingabeaufforderung die folgenden Befehle ein, um die Prozessnamen über die Pipeline abzurufen.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Geben Sie die folgenden Zeilen ein, um die Prozess Objekte zu erhalten, die über eine `Name`-Eigenschaft aus den Prozessen mit dem Namen "Iexplore" verfügen. In diesem Beispiel wird das Cmdlet "`Get-Process`" (bereitgestellt von Windows PowerShell) als upstreambefehl zum Abrufen der iexplore-Prozesse verwendet.

    ```powershell
    PS> get-process iexplore | get-proc
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Weitere Informationen

[Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](./adding-parameters-that-process-command-line-input.md)

[Erstellen Ihres ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)
