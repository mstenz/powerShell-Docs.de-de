---
title: Hinzufügen von Parametern, die Verarbeiten der Befehlszeileneingabe | Microsoft-Dokumentation
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
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068809"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Hinzufügen von Parametern, die Befehlszeileneingaben verarbeiten

Eine Ursache für die Eingabe für ein Cmdlet ist die Befehlszeile an. In diesem Thema wird beschrieben, wie zum Hinzufügen eines Parameters, der **Get-Proc** Cmdlet (die beschrieben wird, im [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)), damit das Cmdlet die Eingabe aus dem lokalen Computer, die basierend auf explizite verarbeiten kann Objekte, die an das Cmdlet übergeben werden. Die **Get-Proc** beschriebenen Cmdlets Ruft die Prozesse, die basierend auf ihren Namen hier ab und zeigt anschließend Informationen über die Prozesse, an der Eingabeaufforderung.

In diesem Thema sind die folgenden Abschnitte:

- [Definieren die Cmdlet-Klasse](#Defining-the-Cmdlet-Class)

- [Deklarieren von Parametern](#Declaring-Parameters)

- [Unterstützung von Parametervalidierung](#Supporting-Parameter-Validation)

- [Überschreiben einer Eingabeverarbeitungsmethode](#Overriding-an-Input-Processing-Method)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#Defining-Object-Types-and-Formatting)

- [Erstellen das Cmdlet](#Building-the-Cmdlet)

- [Testen das Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definieren die Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist die Cmdlet-Namen und die Deklaration von .NET Framework-Klasse, die die Cmdlets implementiert. Dieses Cmdlet Ruft die Prozessinformationen, ab, die hier ausgewählte Verbnamen also "Get". (Nahezu jede Art von Cmdlets, mit dem Informationen abgerufen werden, kann die Befehlszeileneingabe verarbeiten.) Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Hier ist die Klassendeklaration für die **Get-Proc** Cmdlet. Informationen zu dieser Definition finden Sie in [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Deklarieren von Parametern

Cmdlet-Parameter ermöglicht den Benutzer als Eingabe für das-Cmdlet. Im folgenden Beispiel **Get-Proc** und `Get-Member` sind die Namen der Pipeline-Cmdlets und `MemberType` ist ein Parameter für die `Get-Member` Cmdlet. Der Parameter hat das Argument "-Eigenschaft."

**PS > Get-Proc; `get-member` Membertype - Eigenschaft**

Um Parameter für ein Cmdlet zu deklarieren, müssen Sie zunächst die Eigenschaften definieren, die die Parameter darstellen. In der **Get-Proc** -Cmdlet, um der einzige Parameter ist `Name`, die in diesem Fall den Namen des abzurufenden Objekts Prozess .NET Framework darstellt. Folglich definiert die Cmdlet-Klasse eine Eigenschaft vom Typzeichenfolge, ein Array von Namen zu akzeptieren.

Hier folgt die Parameterdeklaration für die `Name` Parameter, der die **Get-Proc** Cmdlet.

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

Um die Windows PowerShell-Laufzeit darüber zu informieren, die diese Eigenschaft ist die `Name` -Parameter ein [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Attribut hinzugefügt wird, auf die Eigenschaftsdefinition. Die grundlegende Syntax zum Deklarieren von dieses Attribut ist `[Parameter()]`.

> [!NOTE]
> Parameter muss explizit als öffentlich markiert werden. Parameter, die nicht als öffentlicher Standard auf interne gekennzeichnet sind und nicht von der Windows PowerShell-Laufzeit gefunden werden.

Dieses Cmdlet verwendet ein Array von Zeichenfolgen für die `Name` Parameter. Wenn möglich, sollte Ihr Cmdlet auch definieren einen Parameter als Array, da dadurch das Cmdlet, um mehr als ein Element zu akzeptieren.

#### <a name="things-to-remember-about-parameter-definitions"></a>Wichtige Fakten über Parameterdefinitionen

- Vordefinierte Windows PowerShell-Parameter und Datentypen sollte so weit wie möglich ist, um sicherzustellen, dass Ihr Cmdlet kompatibel mit Windows PowerShell-Cmdlets ist wiederverwendet werden. Wenn alle Cmdlets, die vordefinierten verwenden z. B. `Id` Parametername, der eine Ressource, die Benutzer schnell die Bedeutung des Parameters, unabhängig davon, welche Cmdlets, die bei Verwendung von verstehen. Im Grunde genommen, Parameternamen gelten dieselben Regeln wie bei Variablennamen in der common Language Runtime (CLR). Weitere Informationen zu Parameternamen finden Sie unter [Cmdlet-Parameternamen](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell sind einige Parameternamen, um eine konsistente benutzererfahrung reserviert. Verwenden Sie nicht diese Parameternamen: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, und `OutBuffer`. Darüber hinaus sind die folgenden Aliase für diese Parameternamen reserviert: `vb`, `db`, `ea`, `ev`, `ov`, und `ob`.

- `Name` ist ein einfache und häufige Parameternamen in Ihre Cmdlets empfohlen. Es ist besser, wählen Sie einen Parameternamen wie folgt als ein komplexer Name, der für ein bestimmtes Cmdlet eindeutig und schwer zu merken ist.

- Parameter sind in Windows PowerShell, Groß-/Kleinschreibung, auch wenn standardmäßig die Shell Fall beibehalten. Kleinschreibung bei den Argumenten, hängt von den Vorgang des-Cmdlets ab. Argumente werden als in der Befehlszeile angegebenen auf einen Parameter übergeben.

- Beispiele für andere Parameterdeklarationen, finden Sie unter [Cmdletparameter](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Deklarieren Sie Parameter als Positionsparameter oder benannte

Ein Cmdlet muss jeder Parameter als Positionsparameter oder benannten Parameter festgelegt. Beide Arten von Parametern akzeptieren einzelne Argumente, die mehrere Argumente, die durch Kommas getrennt, und boolesche Einstellungen. Ein boolescher Parameter, die so genannte eine *wechseln*, nur boolesche Einstellungen behandelt. Der Schalter wird verwendet, um das Vorhandensein des Parameters zu bestimmen. Der empfohlene Standardwert ist `false`.

Das Beispiel **Get-Proc** Cmdlet definiert die `Name` Parameter als Positionsparameter an Position 0. Dies bedeutet, dass das erste Argument, die, das der Benutzer in der Befehlszeile gibt, für diesen Parameter automatisch eingefügt wird. Wenn Sie einen benannten Parameter definieren möchten, für die der Benutzer angeben muss der Parameternamen in der Befehlszeile aus, lassen Sie die `Position` Schlüsselwort aus der Deklaration des Attributs.

> [!NOTE]
> Wenn der Parameter benannt werden müssen, empfehlen wir, dass Sie die am häufigsten verwendeten Parameter mit Feldern fester Breite vornehmen, damit Benutzer nicht den Parameternamen eingeben müssen.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Deklarieren Sie Parameter als obligatorisch oder Optional

Ein Cmdlet muss jeder Parameter als ein optionales oder einen obligatorischen Parameter festgelegt werden. Im Beispiel **Get-Proc** -Cmdlet, das `Name` Parameter als optional definiert werden, da die `Mandatory` Schlüsselwort ist nicht in der Attributdeklaration festgelegt.

## <a name="supporting-parameter-validation"></a>Unterstützung von Parametervalidierung

Im Beispiel **Get-Proc** Fügt ein Attribut eingabeüberprüfung [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), zu der `Name` Parameter, um die Validierung zu aktivieren, die die die Eingabe ist keine `null` noch leer. Dieses Attribut ist eine der mehrere Validierungsattribute, die von Windows PowerShell bereitgestellt. Beispiele für andere Validierungsattribute, finden Sie unter [Überprüfen der Parametereingabe](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabeverarbeitungsmethode

Wenn Ihr Cmdlet zum Verarbeiten der Befehlszeileneingabe wird, muss er die entsprechenden eingabeverarbeitungsmethoden überschreiben. Die grundlegende eingabeverarbeitungsmethoden entstehen in [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).

Die **Get-Proc** Cmdlet überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode zum Behandeln der `Name` Parametereingabe, die durch den Benutzer oder ein Skript bereitgestellt. Diese Methode ruft die Prozesse für jede angeforderte Prozessname oder alle Prozesse an, wenn kein Name angegeben ist. Beachten Sie, dass in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), den Aufruf von [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) ist die Ausgabe Mechanismus zum Senden der Ausgabe Objekte in der Pipeline. Der zweite Parameter des Aufrufs, `enumerateCollection`, nastaven NA hodnotu `true` informieren die Windows PowerShell-Laufzeit zum Aufzählen der Matrix von Prozessobjekten und Schreiben einen Prozess zu einem Zeitpunkt, an die Befehlszeile.

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

Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample02-Beispiel](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET Framework-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren oder ein Cmdlets müssen zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet bereitgestellt. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es mit einem Windows PowerShell-Snap-in mit Windows PowerShell registrieren. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet mit Windows PowerShell registriert ist, können Sie es testen, indem Sie sie in der Befehlszeile ausführen. Hier sind zwei Möglichkeiten, den Code für das beispielcmdlet testen. Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Verwenden Sie an der Windows PowerShell-Eingabeaufforderung den folgenden Befehl zum Auflisten von Internet Explorer-Prozess, mit der Namen "IEXPLORE".

    ```powershell
    PS> get-proc -name iexplore
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Um die Internet Explorer, Outlook und Editor-Prozesse, die mit dem Namen "IEXPLORE" aufzulisten, verwenden Sie "OUTLOOK" und "Editor" den folgenden Befehl aus. Wenn mehrere Prozesse, werden alle von ihnen angezeigt.

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

[Hinzufügen von Parametern, die Eingabe der Prozesspipeline](./adding-parameters-that-process-pipeline-input.md)

[Erstellen eines ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)
