---
title: Erstellen ein Cmdlet ohne Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860646"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Erstellen eines Cmdlet ohne Parameter

In diesem Abschnitt wird beschrieben, wie ein Cmdlet zu erstellen, die Ruft Informationen aus dem lokalen Computer, ohne die Verwendung von Parametern ab, und klicken Sie dann die Informationen in die Pipeline geschrieben wird. Das hier beschriebene Cmdlet ist ein Get-Proc-Cmdlet, das Informationen über die Prozesse des lokalen Computers abgerufen, und klicken Sie dann in der Befehlszeile angezeigt.

Die folgenden: Themen in diesem Abschnitt

- [Benennen das Cmdlet](#Naming-the-Cmdlet)

- [Definieren die Cmdlet-Klasse](#Defining-the-Cmdlet-Class)

- [Überschreiben einer Eingabeverarbeitungsmethode](#Overriding-an-Input-Processing-Method)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#Defining-Object-Types-and-Formatting)

- [Erstellen das Cmdlet](#Building-the-Cmdlet)

- [Testen das Cmdlet](#Testing-the-Cmdlet)

> [!NOTE]
> Denken Sie daran, dass beim Schreiben von Cmdlets, die Verweisassemblys Windows PowerShell® auf der Festplatte (standardmäßig unter C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0) heruntergeladen werden. Sie sind nicht in den globalen Assemblycache (GAC) installiert.

## <a name="naming-the-cmdlet"></a>Benennen das Cmdlet

Ein Cmdlet-Name besteht aus ein Verb an, der angibt, dass das Cmdlet die Aktion und ein Substantiv, der die Elemente angibt, denen mit dem-Cmdlet verarbeitet. Da dieses Beispiel-Cmdlet "Get-Proc" Prozessobjekte abgerufen wird, verwendet es das Verb "Get", definiert durch die [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) Enumeration und das Nomen "Proc", um anzugeben, dass das Cmdlet auf dem Verarbeiten von Elementen funktioniert.

Bei der Benennung von Cmdlets verwenden Sie nicht die folgenden Zeichen: #, () {} [] & - / \ $;: "' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Ein Nomen auswählen

Sie sollten ein Substantiv auswählen, die spezifisch sind. Es wird empfohlen, ein Nomen im singular eine verkürzte Version der Name des Produkts mit dem Präfix verwenden. Ein Beispiel-Cmdlet-Namen dieses Typs ist "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Ein Verb auswählen

Sie sollten ein Verb in der Menge von genehmigten Verb cmdletnamen verwenden. Weitere Informationen zu den genehmigten Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definieren die Cmdlet-Klasse

Nachdem Sie einen Cmdlet-Namen ausgewählt haben, definieren Sie eine .NET-Klasse, um das-Cmdlet zu implementieren. So sieht die Definition der Klasse für dieses Beispiel Get-Proc-Cmdlet aus:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Beachten Sie, dass vor der Klassendefinition den [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut, mit der Syntax `[Cmdlet(verb, noun, ...)]`, dient zum Identifizieren dieser Klasse als Cmdlet verwendet. Dies ist das einzige erforderliche Attribut für alle Cmdlets, und es ermöglicht, dass die Windows PowerShell-Laufzeit sie richtig aufgerufen. Sie können die Attribut-Stichworte, um weitere Deklarieren der Klasse bei Bedarf festlegen. Denken Sie daran, dass die Attributdeklaration für unser Beispiel GetProcCommand-Klasse nur die Nomen und Verb-Namen für das Cmdlet "Get-Proc" deklariert.

> [!NOTE]
> Für alle Klassen in einer Windows PowerShell-Attribut entsprechen die Schlüsselwörter, die Sie festlegen können, die Eigenschaften der Attributklasse.

Bei der Benennung von der Klasse des-Cmdlets ist es empfiehlt sich, den Cmdlet-Namen in den Namen der Klasse entsprechen. Klicken Sie zu diesem Zweck verwenden Sie das Formular "VerbNounCommand", und Ersetzen Sie "Verb" und "Nomen", mit dem Verb und Substantiv im Cmdlet-Namen verwendet. Wie in der vorherigen Klassendefinition angezeigt wird, wird die Beispiel-Cmdlet "Get-Proc" definiert eine Klasse namens GetProcCommand, abgeleitet von der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Basisklasse.

> [!IMPORTANT]
> Wenn Sie möchten ein Cmdlet definieren, der die Windows PowerShell-Laufzeit direkt zugreift, sollte die Klasse .NET leiten Sie von der [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse. Weitere Informationen zu dieser Klasse finden Sie unter [erstellen ein Cmdlet, Parametersätze definiert](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> Die Klasse für ein Cmdlet muss explizit als öffentlich markiert werden. Klassen, die nicht als öffentlich markiert werden werden standardmäßig auf interne und werden von der Windows PowerShell-Laufzeit nicht gefunden werden.

Windows PowerShell verwendet die [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) Namespace-URI für die Cmdlet-Klassen. Es wird empfohlen, um die Cmdlet-Klassen in einem Namespace Befehle für Ihren API-Namespace, z. B. xxx.PS.Commands zu platzieren.

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabeverarbeitungsmethode

Die [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse enthält drei wichtigsten Eingabeverarbeitung-Methoden, die mindestens eine der Ihr Cmdlet muss außer Kraft setzen. Weitere Informationen zur Verarbeitung von Datensätzen in Windows PowerShell finden Sie unter [Funktionsweise von Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Für alle Arten von Eingaben, die Windows PowerShell-Laufzeit ruft [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) um Verarbeitung zu ermöglichen. Wenn Ihr Cmdlet einige vorverarbeitung oder Setup durchführen muss, können sie dazu diese Methode überschreiben.

> [!NOTE]
> Windows PowerShell verwendet den Begriff "Datensatz", beschreiben den Satz von Parameterwerten, die bereitgestellt werden, wenn ein Cmdlet aufgerufen wird.

Wenn Ihr Cmdlet Pipelineeingabe akzeptiert, müssen sie überschreiben die [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, und optional die [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)Methode. Beispielsweise kann ein Cmdlet beide Methoden überschreiben, wenn Sie dieses Tool sammelt alle Benutzereingabe mit [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) und klicken Sie dann auf die Eingabe als Ganzes und nicht als ein Element zu einem Zeitpunkt, als die `Sort-Object` Cmdlet bewirkt.

Wenn Ihr Cmdlet keine Pipelineeingabe akzeptiert, sollte sie überschreiben die [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode. Beachten Sie, dass diese Methode häufig, anstelle von verwendet wird [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Wenn das-Cmdlet kann nicht für ein Element zu einem Zeitpunkt wie der Fall für ein Cmdlet sortiert ist.

Da dieses Beispiel-Cmdlet "Get-Proc" Pipelineeingabe empfangen muss, überschreibt es die [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode und verwendet die standardimplementierungen für [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) und [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Die [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) "Override" Ruft die Prozesse ab und schreibt sie in der Befehlszeile mithilfe der [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Wichtige Fakten über Verarbeitung von Benutzereingaben

- Die standardmäßige Quelle für die Eingabe ist ein expliziter Objekt (z. B. eine Zeichenfolge), die vom Benutzer in der Befehlszeile angegeben. Weitere Informationen finden Sie unter [erstellen ein Cmdlet, um die Eingabe über die Befehlszeile](./adding-parameters-that-process-command-line-input.md).

- Ein eingabeverarbeitungsmethode kann Eingabe auch die Ausgabe-Objekt von einem upstream-Cmdlet für die Pipeline empfangen werden. Weitere Informationen finden Sie unter [erstellen ein Cmdlet zum Prozess Pipelineeingabe](./adding-parameters-that-process-pipeline-input.md). Beachten Sie, dass Ihr Cmdlet empfangen von Eingaben aus einer Kombination von Befehlszeilen und pipeline kann Datenquellen.

- Das Cmdlet "downstream" möglicherweise kein lange oder überhaupt nicht zurück. Aus diesem Grund die eingabeverarbeitungsmethode in Ihrem Cmdlet sollte nicht richten Sperren während des Aufrufs [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), insbesondere Sperren, die für die der Bereich reicht hinter der Cmdlet-Instanz bis.

> [!IMPORTANT]
> Cmdlets sollten niemals Aufrufen [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) oder dessen Entsprechung.

- Ihr Cmdlet möglicherweise Objektvariablen bereinigt werden, wenn sie abgeschlossen ist verarbeiten (z. B. wenn ein Dateihandle in geöffnet der [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode und behält das Handle öffnen für die Verwendung von [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Es ist wichtig zu beachten, dass die Windows PowerShell-Laufzeit nicht immer rufen die [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode, die Bereinigung Objekte ausführen soll.

Z. B. [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kann nicht aufgerufen werden, wenn das Cmdlet Zielpfads abgebrochen wird oder wenn ein Abbruch tritt Fehler in einem beliebigen Teil des Cmdlets auf. Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.Idisposable](/dotnet/api/System.IDisposable) Muster, einschließlich des Finalizers, sodass beide von die Laufzeit aufgerufen werden kann [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) und [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) am Ende der Verarbeitung.

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample01-Beispiel](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen. Der Code für unsere Beispiel-Get-Proc-Cmdlet ist klein, aber es verwendet weiterhin die Windows PowerShell-Laufzeit und eine vorhandene .NET-Objekt, das ausreichend, um es zu nutzen ist. Wir testen, um besser zu verstehen, was mit Get-Proc möglich ist und wie die Ausgabe verwendet werden kann. Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Starten Sie Windows PowerShell, und erhalten Sie die aktuellen Prozessen auf dem Computer ausgeführt.

    ```powershell
    get-proc
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Weisen Sie eine Variable, auf die Cmdlet-Ergebnisse für eine einfachere Bearbeitung.

    ```powershell
    $p=get-proc
    ```

3. Ruft die Anzahl von Prozessen.

    ```powershell
    $p.length
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    63
    ```

4. Rufen Sie einen bestimmten Prozess.

    ```powershell
    $p[6]
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Die Startzeit für diesen Prozess zu erhalten.

    ```powershell
    $p[6].starttime
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Rufen Sie die Prozesse, die für die Anzahl der Handles größer als 500 ist, und sortieren Sie des Ergebnisses.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Verwenden der `Get-Member` -Cmdlet zum Auflisten der Eigenschaften, die für jeden Prozess zur Verfügung.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Weitere Informationen

[Erstellen ein Cmdlet aus, um über die Befehlszeile verarbeiten](./adding-parameters-that-process-command-line-input.md)

[Erstellen ein Cmdlet aus, um die Pipelineeingabe zu verarbeiten](./adding-parameters-that-process-pipeline-input.md)

[Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Erweitern die Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Funktionsweise von Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)