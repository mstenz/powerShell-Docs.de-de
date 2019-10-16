---
title: Erstellen eines Cmdlets ohne Parameter | Microsoft-Dokumentation
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
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369859"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Erstellen eines Cmdlet ohne Parameter

In diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet erstellen, das Informationen vom lokalen Computer abruft, ohne Parameter zu verwenden, und dann die Informationen in die Pipeline schreibt. Das hier beschriebene Cmdlet ist ein Get-proc-Cmdlet, das Informationen zu den Prozessen des lokalen Computers abruft und diese Informationen dann in der Befehlszeile anzeigt.

> [!NOTE]
> Beachten Sie, dass beim Schreiben von Cmdlets die Windows PowerShell-® Verweisassemblys auf den Datenträger heruntergeladen werden (standardmäßig unter "c:\Programme\Reference assemblies\microsoft\windowspowershell\v1.0"). Sie sind nicht im globalen Assemblycache (GAC) installiert.

## <a name="naming-the-cmdlet"></a>Benennen des Cmdlets

Ein Cmdlet-Name besteht aus einem Verb, das die Aktion angibt, die das Cmdlet annimmt, und einem Substantiv, das die Elemente angibt, auf die das Cmdlet angewendet wird. Da das Get-proc-Beispiel-Cmdlet Prozess Objekte abruft, wird das Verb "Get" verwendet, das von der [System. Management. Automation. verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -Enumeration definiert wird, und das Nomen "proc", um anzugeben, dass das Cmdlet für Prozesselemente funktioniert.

Verwenden Sie beim Benennen von Cmdlets keines der folgenden Zeichen: #, () {} [] &-/\ $; : "" < > &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Auswählen eines Substantivs

Sie sollten ein bestimmtes Substantiv auswählen. Es empfiehlt sich, ein Singular-Substantiv zu verwenden, das mit einer verkürzten Version des Produkt namens versehen ist. Ein Beispiel für einen Cmdlet-Namen dieses Typs ist "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Auswählen eines Verbs

Sie sollten ein Verb aus dem Satz genehmigter Cmdlet-Verb Namen verwenden. Weitere Informationen zu den genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definieren der Cmdlet-Klasse

Nachdem Sie einen Cmdlet-Namen ausgewählt haben, definieren Sie eine .NET-Klasse, um das Cmdlet zu implementieren. Hier ist die Klassendefinition für dieses Beispiel-Get-proc-Cmdlet:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Beachten Sie, dass vor der Klassendefinition das [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -Attribut mit der Syntax `[Cmdlet(verb, noun, ...)]` verwendet wird, um diese Klasse als Cmdlet zu identifizieren. Dies ist das einzige erforderliche Attribut für alle Cmdlets und ermöglicht es der Windows PowerShell-Laufzeit, Sie ordnungsgemäß aufzurufen. Sie können Attribut Schlüsselwörter festlegen, um die Klasse bei Bedarf weiter zu deklarieren. Beachten Sie, dass die Attribut Deklaration für die getproccommand-Beispiel Klasse nur die Substantiv-und Verb Namen für das Get-proc-Cmdlet deklariert.

> [!NOTE]
> Für alle Windows PowerShell-Attribut Klassen entsprechen die Schlüsselwörter, die Sie festlegen können, den Eigenschaften der Attribut Klasse.

Wenn Sie die Klasse des Cmdlets benennen, empfiehlt es sich, den Cmdlet-Namen im Klassennamen widerzuspiegeln. Verwenden Sie hierzu das Format "verbnouncommand", und ersetzen Sie "Verb" und "Substantiv" durch das Verb und das Substantiv, das im Cmdlet-Namen verwendet wird. Wie in der vorherigen Klassendefinition gezeigt, definiert das Get-proc-Beispiel Cmdlet eine Klasse mit dem Namen "getproccommand", die von der Basisklasse " [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) " abgeleitet ist.

> [!IMPORTANT]
> Wenn Sie ein Cmdlet definieren möchten, das direkt auf die Windows PowerShell-Laufzeit zugreift, sollte Ihre .NET-Klasse von der Basisklasse " [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) " abgeleitet werden. Weitere Informationen zu dieser Klasse finden Sie unter [Erstellen eines Cmdlets zum Definieren von Parameter Sätzen](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> Die-Klasse für ein Cmdlet muss explizit als public gekennzeichnet werden. Klassen, die nicht als public gekennzeichnet sind, werden standardmäßig intern verwendet und werden von der Windows PowerShell-Laufzeit nicht gefunden.

Windows PowerShell verwendet den [Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) -Namespace für die Cmdlet-Klassen. Es wird empfohlen, die Cmdlet-Klassen in einem Befehle-Namespace ihres API-Namespace zu platzieren, z. b. xxx. PS. Commands.

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabe Verarbeitungsmethode

Die [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse stellt drei Haupt Eingabe-Verarbeitungsmethoden bereit, von denen das Cmdlet überschrieben werden muss. Weitere Informationen zur Verarbeitung von Datensätzen in Windows PowerShell finden Sie unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

Für alle Typen von Eingaben Ruft die Windows PowerShell-Runtime [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) auf, um die Verarbeitung zu ermöglichen. Wenn das Cmdlet einige Vorverarbeitungs-oder Setup Vorgänge ausführen muss, kann dies durch Überschreiben dieser Methode durchgeführt werden.

> [!NOTE]
> Windows PowerShell verwendet den Begriff "Datensatz", um den Satz von Parameterwerten zu beschreiben, die beim Aufrufen eines Cmdlets bereitgestellt werden.

Wenn das Cmdlet Pipeline Eingaben annimmt, muss es die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode und optional die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode überschreiben. Beispielsweise kann ein Cmdlet beide Methoden überschreiben, wenn es die gesamte Eingabe mithilfe von [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) sammelt und dann die Eingabe als Ganzes anstelle eines Elements, wie das `Sort-Object`-Cmdlet, bearbeitet.

Wenn das Cmdlet keine Pipeline Eingaben annimmt, sollte es die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode überschreiben. Beachten Sie, dass diese Methode häufig anstelle von [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) verwendet wird, wenn das Cmdlet nicht gleichzeitig auf einem Element agieren kann, wie es bei einem Sortierungs-Cmdlet der Fall ist.

Da dieses Beispiel-Cmdlet "Get-proc" eine Pipeline Eingabe empfangen muss, überschreibt es die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode und verwendet die Standard Implementierungen für " [System. Management. Automation. Cmdlet. BeginProcessing". ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)und [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Überschreibung ruft Prozesse ab und schreibt Sie mithilfe der [System. Management. Automation. Cmdlet. Write-Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode in die Befehlszeile.

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

#### <a name="things-to-remember-about-input-processing"></a>Dinge, die bei der Eingabe Verarbeitung beachtet werden sollten

- Die Standard Quelle für die Eingabe ist ein explizites Objekt (z. b. eine Zeichenfolge), das vom Benutzer in der Befehlszeile bereitgestellt wird. Weitere Informationen finden Sie unter [Erstellen eines Cmdlets zum Verarbeiten von Befehlszeilen Eingaben](./adding-parameters-that-process-command-line-input.md).

- Eine Eingabe Verarbeitungsmethode kann auch Eingaben vom Ausgabe Objekt eines upstreamcmdlets in der Pipeline empfangen. Weitere Informationen finden Sie unter [Erstellen eines Cmdlets für die Verarbeitung von Pipeline Eingaben](./adding-parameters-that-process-pipeline-input.md). Beachten Sie, dass das Cmdlet Eingaben von einer Kombination von Befehlszeilen-und Pipeline Quellen empfangen kann.

- Das downstreamcmdlet gibt möglicherweise für längere Zeit oder gar nicht zurück. Aus diesem Grund sollte die Eingabe Verarbeitungsmethode in Ihrem Cmdlet keine Sperren bei Aufrufen von [System. Management. Automation. Cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)enthalten, insbesondere sperren, für die der Bereich die Cmdlet-Instanz überschreitet.

> [!IMPORTANT]
> Cmdlets sollten niemals [System. Console. Write teline *](/dotnet/api/System.Console.WriteLine) oder die entsprechende-Entsprechung aufzurufen.

- Das Cmdlet kann Objektvariablen zum Bereinigen aufweisen, wenn die Verarbeitung abgeschlossen ist (z. b. Wenn ein Datei Handle in der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode geöffnet wird und das Handle für die Verwendung durch [ System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Beachten Sie, dass die Windows PowerShell-Laufzeit nicht immer die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode aufruft, die die Objekt Bereinigung durchführen soll.

Beispielsweise kann " [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) " nicht aufgerufen werden, wenn das Cmdlet in der Mitte abgebrochen wird oder wenn in einem beliebigen Teil des Cmdlets ein Abbruch Fehler auftritt. Daher sollte ein Cmdlet, das die Objekt Bereinigung erfordert, das gesamte [System. iverwerfbare](/dotnet/api/System.IDisposable) Muster implementieren, einschließlich des Finalizers, damit die Laufzeit sowohl [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) als [auch ausführen kann. System. iverwerf. verwerfen *](/dotnet/api/System.IDisposable.Dispose) am Ende der Verarbeitung.

## <a name="code-sample"></a>Code Beispiel

Den gesamten C# Beispielcode finden Sie unter [GetProcessSample01 Sample](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es über ein Windows PowerShell-Snap-in bei Windows PowerShell registrieren. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet bei Windows PowerShell registriert wurde, können Sie es in der Befehlszeile testen. Der Code für das Beispiel-Cmdlet "Get-proc" ist klein, verwendet jedoch weiterhin die Windows PowerShell-Laufzeit und ein vorhandenes .NET-Objekt, das ausreichend ist, um es zu nutzen. Testen Sie es, um besser zu verstehen, was Get-proc tun kann und wie seine Ausgabe verwendet werden kann. Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Starten Sie Windows PowerShell, und holen Sie sich die aktuellen Prozesse, die auf dem Computer ausgeführt werden.

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

2. Weisen Sie den Cmdlet-Ergebnissen eine Variable zu, um die Bearbeitung zu vereinfachen.

    ```powershell
    $p=get-proc
    ```

3. Gibt die Anzahl der Prozesse an.

    ```powershell
    $p.length
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    63
    ```

4. Ruft einen bestimmten Prozess ab.

    ```powershell
    $p[6]
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Hiermit wird die Startzeit dieses Prozesses angezeigt.

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

6. Holen Sie die Prozesse, für die die Anzahl der Handles größer als 500 ist, und sortieren Sie das Ergebnis.

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

7. Verwenden Sie das Cmdlet "`Get-Member`", um die für die einzelnen Prozesse verfügbaren Eigenschaften aufzulisten.

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

[Erstellen eines Cmdlets zur Verarbeitung der Befehlszeilen Eingabe](./adding-parameters-that-process-command-line-input.md)

[Erstellen eines Cmdlets zum Verarbeiten von Pipeline Eingaben](./adding-parameters-that-process-pipeline-input.md)

[Erstellen eines Windows PowerShell-Cmdlets](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)