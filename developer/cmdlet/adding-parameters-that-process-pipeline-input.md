---
title: Hinzufügen von Parametern, die Pipelineeingabe verarbeiten | Microsoft-Dokumentation
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
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054755"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Hinzufügen von Parametern, die Pipelineeingaben verarbeiten

Eine Ursache für die Eingabe für ein Cmdlet handelt es sich um ein Objekt für die Pipeline, die von einem upstream-Cmdlet stammt. In diesem Abschnitt wird beschrieben, wie zum Hinzufügen eines Parameters an das Get-Proc-Cmdlet (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)), damit das Cmdlet Pipelineobjekte verarbeitet werden kann.

Das Get-Proc-Cmdlet verwendet einen `Name` Parameter, die Eingaben von einem Pipelineobjekt akzeptiert Prozess auf dem lokalen Computer, die basierend auf den angegebenen Namen abruft und anschließend Informationen über die Prozesse in der Befehlszeile angezeigt.

Die folgenden: Themen in diesem Abschnitt

- [Definieren die Cmdlet-Klasse](#Defining-the-Cmdlet-Class)

- [Definieren von Eingaben aus der Pipeline](#Defining-Input-from-the-Pipeline)

- [Überschreiben einer Eingabeverarbeitungsmethode](#Overriding-an-Input-Processing-Method)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#Defining-Object-Types-and-Formatting)

- [Erstellen das Cmdlet](#Building-the-Cmdlet)

- [Testen das Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definieren die Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren. Dieses Cmdlet Ruft die Prozessinformationen, ab, der Namen des Verbs hier ausgewählten also "Get". (Nahezu jede Art von Cmdlets, mit dem Informationen abgerufen werden, kann die Befehlszeileneingabe verarbeiten.) Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Im folgenden finden die Definition für dieses Cmdlet "Get-Proc". Details zu dieser Definition werden in angegebenen [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).

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

Dieser Abschnitt beschreibt, wie Sie Eingaben aus der Pipeline für ein Cmdlet definieren. Dieses Cmdlet "Get-Proc" definiert eine Eigenschaft, steht die `Name` Parameter wie in beschrieben [Hinzufügen von Parametern, die Eingabe über die Befehlszeile](./adding-parameters-that-process-command-line-input.md). (Siehe das Thema allgemeine Informationen zum Deklarieren von Parametern.)

Wenn ein Cmdlet Pipelineeingabe verarbeiten muss, muss es jedoch seine Parameter an die Eingabe von Werten durch die Windows PowerShell-Laufzeit gebunden haben. Zu diesem Zweck fügen Sie der `ValueFromPipeline` Schlüsselwort oder Hinzufügen der `ValueFromPipelineByProperty` Schlüsselwort, um die [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attributdeklaration. Geben Sie die `ValueFromPipeline` Schlüsselwort, wenn das Cmdlet das vollständige Eingabeobjekt greift auf. Geben Sie die `ValueFromPipelineByProperty` , wenn das Cmdlet greift, nur eine Eigenschaft des Objekts auf.

Hier folgt die Parameterdeklaration für die `Name` Parameter des Cmdlets Get-Proc, die Pipelineeingabe akzeptiert.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

Im vorherigen Deklaration wird das `ValueFromPipeline` Schlüsselwort `true` , damit die Windows PowerShell-Laufzeit den Parameter auf das eingehende Objekt gebunden wird, wenn das Objekt den gleichen Typ wie der Parameter ist oder wenn es in den gleichen Typ umgewandelt werden kann. Die `ValueFromPipelineByPropertyName` Schlüsselwort wird ebenfalls für festgelegt `true` , damit die Windows PowerShell-Laufzeit überprüft das eingehende Objekt für eine `Name` Eigenschaft. Wenn das eingehende Objekt um eine solche Eigenschaft verfügt, kann die Laufzeit verbindet die `Name` Parameter, um die `Name` -Eigenschaft des eingehenden Objekts.

> [!NOTE]
> Die Einstellung der `ValueFromPipeline` Attribut Schlüsselwort, für die Einstellung für ein Parameter Vorrang vor hat der `ValueFromPipelineByPropertyName` Schlüsselwort.

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabeverarbeitungsmethode

Ist Ihr Cmdlet Pipelineeingabe behandelt, muss sie die entsprechenden eingabeverarbeitungsmethoden außer Kraft zu setzen. Die grundlegende eingabeverarbeitungsmethoden entstehen in [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).

Dieses Cmdlet "Get-Proc" überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode zum Behandeln der `Name` Parametereingabe, die durch den Benutzer oder ein Skript bereitgestellt. Diese Methode erhalten die Prozesse für jede angeforderte Prozessname oder allen Prozessen, wenn kein Name angegeben ist. Beachten Sie, dass in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), den Aufruf von [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) ist die Ausgabe Mechanismus zum Senden der Ausgabe Objekte in der Pipeline. Der zweite Parameter des Aufrufs, `enumerateCollection`, nastaven NA hodnotu `true` informieren die Windows PowerShell-Laufzeit zum Auflisten von Arrays von Prozessobjekten und Schreiben einen Prozess zu einem Zeitpunkt, an die Befehlszeile.

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

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [Beispiel mit GetProcessSample03](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, testen Sie es in der Befehlszeile aus ausführen. Testen Sie z. B. den Code für die Beispiel-Cmdlet. Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Geben Sie an der Windows PowerShell-Eingabeaufforderung die folgenden Befehle zum Abrufen der Namen der entsprechenden Prozesse über die Pipeline aus.

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

- Geben Sie die folgenden Zeilen rufen die Prozessobjekte, die eine `Name` Eigenschaft von den Prozessen, die Namen "IEXPLORE". Dieses Beispiel verwendet die `Get-Process` Cmdlet (bereitgestellt vom Windows PowerShell) als upstream-Befehl zum Abrufen der Prozesse "IEXPLORE".

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

[Hinzufügen von Parametern, die über die Befehlszeileneingabe verarbeiten.](./adding-parameters-that-process-command-line-input.md)

[Erstellen eines ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)
