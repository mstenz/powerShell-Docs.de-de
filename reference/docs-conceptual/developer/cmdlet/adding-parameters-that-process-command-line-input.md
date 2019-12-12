---
title: Hinzufügen von Parametern, die Befehlszeilen Eingaben verarbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364629"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Hinzufügen von Parametern, die Befehlszeileneingaben verarbeiten

Eine Eingabe Quelle für ein Cmdlet ist die Befehlszeile. In diesem Thema wird beschrieben, wie Sie dem **Get-proc-** Cmdlet (das unter Erstellen des [ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)beschrieben wird) einen Parameter hinzufügen, damit das Cmdlet Eingaben vom lokalen Computer auf der Grundlage von expliziten Objekten verarbeiten kann, die an das Cmdlet übergeben werden. Das hier beschriebene **Get-proc-** Cmdlet ruft Prozesse auf Grundlage ihrer Namen ab und zeigt dann Informationen zu den Prozessen an einer Eingabeaufforderung an.

## <a name="defining-the-cmdlet-class"></a>Definieren der Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist die Cmdlet-Benennung und die Deklaration der .NET Framework Klasse, die das Cmdlet implementiert. Dieses Cmdlet ruft Prozessinformationen ab, sodass der hier gewählte Verb Name "Get" lautet. (Fast jede Art von Cmdlet, das Informationen abrufen kann, kann die Befehlszeilen Eingabe verarbeiten.) Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

Hier ist die Klassen Deklaration für das **Get-proc-** Cmdlet. Details zu dieser Definition finden Sie unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Deklarieren der Parameter

Mit einem Cmdlet-Parameter kann der Benutzereingaben für das Cmdlet bereitstellen. Im folgenden Beispiel sind **Get-proc** und `Get-Member` die Namen von Pipeline-Cmdlets, und `MemberType` ist ein Parameter für das `Get-Member`-Cmdlet. Der-Parameter hat das Argument "Property".

**PS > Get-proc; `get-member` Mitgliedschafts Eigenschaft**

Um Parameter für ein Cmdlet zu deklarieren, müssen Sie zunächst die Eigenschaften definieren, die die Parameter darstellen. Im **Get-proc-** Cmdlet ist der einzige Parameter `Name`, der in diesem Fall den Namen des abzurufenden .NET Framework Prozess Objekts darstellt. Daher definiert die Cmdlet-Klasse eine Eigenschaft vom Typ "String", um ein Array von Namen zu akzeptieren.

Hier ist die Parameter Deklaration für den `Name`-Parameter des **Get-proc-** Cmdlets.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Um die Windows PowerShell-Laufzeit darüber zu informieren, dass diese Eigenschaft der `Name`-Parameter ist, wird der Eigenschafts Definition ein [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribut hinzugefügt. Die grundlegende Syntax zum Deklarieren dieses Attributs ist `[Parameter()]`.

> [!NOTE]
> Ein Parameter muss explizit als public gekennzeichnet werden. Parameter, die nicht als öffentlich gekennzeichnet sind, sind standardmäßig intern und werden von der Windows PowerShell-Laufzeit nicht gefunden.

Dieses Cmdlet verwendet ein Array von Zeichen folgen für den `Name`-Parameter. Wenn möglich, sollte Ihr Cmdlet auch einen Parameter als Array definieren, da das Cmdlet somit mehr als ein Element annehmen kann.

#### <a name="things-to-remember-about-parameter-definitions"></a>Dinge, die Sie über Parameter Definitionen merken müssen

- Vordefinierte Windows PowerShell-Parameternamen und-Datentypen sollten so weit wie möglich wieder verwendet werden, um sicherzustellen, dass Ihr Cmdlet mit Windows PowerShell-Cmdlets kompatibel ist. Wenn beispielsweise alle Cmdlets den vordefinierten `Id` Parameternamen verwenden, um eine Ressource zu identifizieren, kann der Benutzer leicht die Bedeutung des Parameters erkennen, unabhängig davon, welches Cmdlet verwendet wird. Im Grunde folgen Parameternamen denselben Regeln wie die, die für Variablennamen im Common Language Runtime (CLR) verwendet werden. Weitere Informationen zum Benennen von Parametern finden [Sie unter Cmdlet-Parameternamen](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell reserviert einige Parameternamen, um eine konsistente Benutzer Leistung zu gewährleisten. Verwenden Sie diese Parameternamen nicht: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`und `OutBuffer`. Außerdem sind die folgenden Aliase für diese Parameternamen reserviert: `vb`, `db`, `ea`, `ev`, `ov`und `ob`.

- `Name` ist ein einfacher und allgemeiner Parameter Name, der für die Verwendung in ihren Cmdlets empfohlen wird. Es empfiehlt sich, einen Parameternamen wie diesen als einen komplexen Namen auszuwählen, der für ein bestimmtes Cmdlet eindeutig ist und schwer zu merken ist.

- Bei Parametern wird in Windows PowerShell die Groß-/Kleinschreibung nicht beachtet, obwohl die Shell standardmäßig die groß- Die Groß-/Kleinschreibung der Argumente hängt von der Operation des Cmdlets ab. Argumente werden an einen Parameter übergeben, wie in der Befehlszeile angegeben.

- Beispiele für andere Parameter Deklarationen finden Sie unter [Cmdlet-Parameter](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Deklarieren von Parametern als Positions-oder benannte Parameter

Ein Cmdlet muss jeden Parameter entweder als Positions Parameter oder als benannten Parameter festlegen. Beide Arten von Parametern akzeptieren einzelne Argumente, mehrere durch Kommas getrennte Argumente und boolesche Einstellungen. Bei einem booleschen Parameter, der auch als *Switch*bezeichnet wird, werden nur boolesche Einstellungen behandelt. Der-Schalter wird verwendet, um das vorhanden sein des-Parameters zu bestimmen. Der empfohlene Standardwert ist `false`.

Das **Get-proc-** Beispiel Cmdlet definiert den `Name`-Parameter als Positions Parameter mit der Position 0. Dies bedeutet, dass das erste Argument, das der Benutzer in der Befehlszeile eingibt, automatisch für diesen Parameter eingefügt wird. Wenn Sie einen benannten Parameter definieren möchten, für den der Benutzer den Parameternamen in der Befehlszeile angeben muss, belassen Sie das `Position` Schlüsselwort aus der Attribut Deklaration heraus.

> [!NOTE]
> Wenn Parameter nicht benannt werden müssen, empfiehlt es sich, die am häufigsten verwendeten Parameter positionell zu machen, damit Benutzer den Parameternamen nicht eingeben müssen.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Deklarieren von Parametern als obligatorisch oder optional

Ein Cmdlet muss jeden Parameter entweder als optionalen oder als obligatorischen Parameter festlegen. Im Beispiel **-Get-proc-** Cmdlet wird der `Name`-Parameter als optional definiert, da das `Mandatory`-Schlüsselwort nicht in der Attribut Deklaration festgelegt ist.

## <a name="supporting-parameter-validation"></a>Unterstützende Parameter Validierung

Das **Get-proc-** Beispiel Cmdlet fügt dem `Name`-Parameter ein Eingabe Validierungs Attribut ( [System. Management. Automation. validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)) hinzu, um die Validierung zu aktivieren, dass die Eingabe weder `null` noch leer ist. Dieses Attribut ist eines von mehreren Validierungs Attributen, die von Windows PowerShell bereitgestellt werden. Beispiele für andere Validierungs Attribute finden Sie unter [Validieren von Parameter Eingaben](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabe Verarbeitungsmethode

Wenn das Cmdlet die Befehlszeilen Eingabe verarbeiten soll, müssen die entsprechenden Eingabe Verarbeitungsmethoden überschrieben werden. Die grundlegenden Eingabe Verarbeitungsmethoden werden beim [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)eingeführt.

Das **Get-proc-** Cmdlet überschreibt die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, um die vom Benutzer oder einem Skript bereitgestellten `Name` Parameter Eingaben zu verarbeiten. Diese Methode ruft die Prozesse für die einzelnen angeforderten Prozessnamen ab oder alle für Prozesse, wenn kein Name angegeben wird. Beachten Sie, dass in " [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)" der [System. Management. Automation. Cmdlet. Write-Object% 28system. Object% 2csystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) aufgerufen wird. Dies ist der Ausgabe Mechanismus zum Senden von Ausgabe Objekten an die Pipeline. Der zweite Parameter dieses Aufrufes, `enumerateCollection`, ist auf `true` festgelegt, um die Windows PowerShell-Laufzeit anzuweisen, das Ausgabe Array von Prozess Objekten aufzulisten und jeweils einen Prozess in die Befehlszeile zu schreiben.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Codebeispiel

Den gesamten C# Beispielcode finden Sie unter [GetProcessSample02 Sample](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt mithilfe .NET Framework-Objekten Informationen zwischen Cmdlets. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder ein Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es mithilfe eines Windows PowerShell-Snap-Ins bei Windows PowerShell registrieren. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn Ihr Cmdlet bei Windows PowerShell registriert ist, können Sie es in der Befehlszeile testen. Im folgenden finden Sie zwei Möglichkeiten, den Code für das-Beispiel-Cmdlet zu testen. Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Führen Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl aus, um den Internet Explorer-Prozess mit dem Namen "Iexplore" aufzulisten.

    ```powershell
    PS> get-proc -name iexplore
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Verwenden Sie den folgenden Befehl, um die Internet Explorer-, Outlook-und Notepad-Prozesse mit dem Namen "Iexplore", "Outlook" und "Notepad" aufzulisten. Wenn mehrere Prozesse vorhanden sind, werden alle angezeigt.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Weitere Informationen

[Hinzufügen von Parametern, die Pipeline Eingaben verarbeiten](./adding-parameters-that-process-pipeline-input.md)

[Erstellen Ihres ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erweitern von Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)
