---
title: Hinzufügen von Fehlerberichten ohne Abbruch zum Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: ec29d1cffa083e4cce667d3e1efbd4eeecbffb51
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870114"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Hinzufügen von Berichten für Fehler ohne Abbruch zu Cmdlet

Cmdlets können nicht abschließende Fehler melden, indem Sie die [System. Management. Automation. Cmdlet. Write error][] -Methode aufrufen und weiterhin auf dem aktuellen Eingabe Objekt oder in weiteren eingehenden Pipeline Objekten arbeiten. In diesem Abschnitt wird erläutert, wie ein Cmdlet erstellt wird, das nicht abschließende Fehler von seinen Eingabe Verarbeitungsmethoden meldet.

Bei nicht beendenden Fehlern (sowie beim Beenden von Fehlern) muss das Cmdlet ein [System. Management. Automation. ErrorRecord][] -Objekt übergeben, das den Fehler identifiziert. Jeder Fehler Daten Satz wird durch eine eindeutige Zeichenfolge identifiziert, die als "Fehler Bezeichner" bezeichnet wird. Zusätzlich zum Bezeichner wird die Kategorie jedes Fehlers durch Konstanten angegeben, die durch eine [System. Management. Automation. ErrorCategory][] -Enumeration definiert werden. Der Benutzer kann Fehler basierend auf der Kategorie anzeigen, indem er die `$ErrorView` Variable auf "categoryview" festlegt.

Weitere Informationen zu Fehler Datensätzen finden Sie unter [Windows PowerShell-Fehler Datensätze](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definieren des Cmdlets

Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert. Dieses Cmdlet ruft Prozessinformationen ab, daher lautet der hier gewählte Verb Name "Get". (Fast jede Art von Cmdlet, das Informationen abrufen kann, kann die Befehlszeilen Eingabe verarbeiten.) Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](approved-verbs-for-windows-powershell-commands.md).

Im folgenden finden Sie die Definition für dieses `Get-Proc` Cmdlet. Einzelheiten zu dieser Definition finden Sie unter [Erstellen des ersten Cmdlets](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definieren von Parametern

Bei Bedarf muss das Cmdlet Parameter für die Verarbeitung von Eingaben definieren. Dieses Cmdlet "Get-proc" definiert einen **namens** Parameter, wie unter [Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](adding-parameters-that-process-command-line-input.md)beschrieben.

Hier ist die Parameter Deklaration für den **Name** -Parameter dieses Get-proc-Cmdlets.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a>Überschreiben von Eingabe Verarbeitungsmethoden

Alle Cmdlets müssen mindestens eine der Eingabe Verarbeitungsmethoden überschreiben, die von der [System. Management. Automation. Cmdlet][] -Klasse bereitgestellt werden. Diese Methoden werden unter [Erstellen des ersten Cmdlets](creating-a-cmdlet-without-parameters.md)erläutert.

> [!NOTE]
> Ihr Cmdlet sollte jeden Datensatz so unabhängig wie möglich verarbeiten.

Dieses Get-proc-Cmdlet überschreibt die [System. Management. Automation. Cmdlet. ProcessRecord][] -Methode, um den **namens** Parameter für die vom Benutzer oder einem Skript bereitgestellte Eingabe zu verarbeiten. Diese Methode erhält die Prozesse für die einzelnen angeforderten Prozessnamen oder alle Prozesse, wenn kein Name angegeben wird. Details dieser außer Kraft Setzung werden bei [der Erstellung des ersten Cmdlets](creating-a-cmdlet-without-parameters.md)angegeben.

### <a name="things-to-remember-when-reporting-errors"></a>Dinge, die beim Melden von Fehlern beachtet werden sollten

Das [System. Management. Automation. ErrorRecord][] -Objekt, das das Cmdlet beim Schreiben eines Fehlers übergibt, erfordert im Kern eine Ausnahme. Befolgen Sie die .NET-Richtlinien bei der Bestimmung der zu verwendenden Ausnahme.
Wenn der Fehler in der Semantik identisch mit einer vorhandenen Ausnahme ist, sollte das Cmdlet diese Ausnahme verwenden oder davon ableiten. Andernfalls sollte eine neue Ausnahme-oder eine Ausnahme Hierarchie direkt von der [System. Exception][] -Klasse abgeleitet werden.

Beachten Sie beim Erstellen von Fehler bezeichgern (auf die über die fullyqualifiederrorid-Eigenschaft der ErrorRecord-Klasse zugegriffen wird) Folgendes:

- Verwenden Sie Zeichen folgen, die zu Diagnose Zwecken dienen, damit Sie bei der Überprüfung des voll qualifizierten Bezeichners ermitteln können, welcher Fehler vorliegt und wo der Fehler aufgetreten ist.

- Ein wohlgeformter voll qualifizierter Fehler Bezeichner kann wie folgt lauten.

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Beachten Sie, dass im vorherigen Beispiel der Fehler Bezeichner (das erste Token) angibt, was der Fehler ist, und der verbleibende Teil gibt an, wo der Fehler aufgetreten ist.

- Bei komplexeren Szenarios kann der Fehler Bezeichner ein Punkt getrenntes Token sein, das bei der Überprüfung analysiert werden kann. Dies ermöglicht es Ihnen, die Teile des Fehler Bezeichners sowie den Fehler Bezeichner und die Fehler Kategorie zu verzweigen.

Mit dem-Cmdlet sollten bestimmte Fehler Bezeichner verschiedenen Codepfade zugewiesen werden. Beachten Sie bei der Zuweisung von Fehler bezeichmern die folgenden Informationen:

- Ein Fehler Bezeichner sollte während des gesamten Lebenszyklus des Cmdlets konstant bleiben. Ändern Sie nicht die Semantik eines Fehler Bezeichners zwischen den Cmdlet-Versionen.
- Verwenden Sie Text für einen Fehler Bezeichner, der dem gemeldeten Fehler entspricht. Verwenden Sie keine Leerzeichen oder Interpunktions Zeichen.
- Verwenden Sie das Cmdlet, um nur Fehler Bezeichner zu generieren, die reproduzierbar sind. Beispielsweise sollte kein Bezeichner generiert werden, der einen Prozess Bezeichner enthält. Fehler Bezeichner sind nur dann für einen Benutzer nützlich, wenn Sie bezeichmern entsprechen, die von anderen Benutzern erkannt werden, die das gleiche Problem aufweisen.

Nicht behandelte Ausnahmen werden von PowerShell unter den folgenden Bedingungen nicht abgefangen:

- Wenn ein Cmdlet einen neuen Thread erstellt und Code, der in diesem Thread ausgeführt wird, eine nicht behandelte Ausnahme auslöst, wird der Fehler von PowerShell nicht abgefangen, und der Prozess wird beendet.
- Wenn ein Objekt über Code im Debuggen verfügt oder Methoden verwerfen, die zu einer nicht behandelten Ausnahme geführt haben, wird der Fehler von PowerShell nicht abgefangen, und der Prozess wird beendet.

## <a name="reporting-nonterminating-errors"></a>Melden von nicht abschließenden Fehlern

Jede der Eingabe Verarbeitungsmethoden kann mithilfe der [System. Management. Automation. Cmdlet. Write error][] -Methode einen Fehler ohne Abbruch an den Ausgabestream melden.

Im folgenden finden Sie ein Codebeispiel aus diesem Get-proc-Cmdlet, das den [System. Management. Automation. Cmdlet. Write error][] -Befehl in der Überschreibung der [System. Management. Automation. Cmdlet. ProcessRecord][] -Methode veranschaulicht. In diesem Fall wird der-Befehl durchgeführt, wenn das Cmdlet keinen Prozess für einen angegebenen Prozess Bezeichner finden kann.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Dinge, die Sie beim Schreiben von Fehlern bei der nicht Beendigung

Bei einem Fehler ohne Abbruch muss das Cmdlet einen bestimmten Fehler Bezeichner für jedes bestimmte Eingabe Objekt generieren.

Ein Cmdlet muss häufig die PowerShell-Aktion ändern, die von einem Fehler ohne Abbruch erzeugt wird. Hierzu können Sie die Parameter "`ErrorAction`" und "`ErrorVariable`" definieren. Wenn Sie den `ErrorAction` Parameter definieren, zeigt das Cmdlet die Benutzeroptionen [System. Management. Automation. Action Preference][]an. Sie können die Aktion auch direkt beeinflussen, indem Sie die `$ErrorActionPreference` Variable festlegen.

Mit dem-Cmdlet können nicht abschließende Fehler in einer Variablen gespeichert werden. dabei wird der `ErrorVariable`-Parameter verwendet, der von der-Einstellung `ErrorAction`nicht betroffen ist. Fehler können an eine vorhandene Fehler Variable angehängt werden, indem ein Pluszeichen (+) am Anfang des Variablen namens hinzugefügt wird.

## <a name="code-sample"></a>Codebeispiel

Den gesamten C# Beispielcode finden Sie unter [GetProcessSample04 Sample](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es über ein Windows PowerShell-Snap-in bei Windows PowerShell registrieren. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet in PowerShell registriert wurde, können Sie es in der Befehlszeile testen. Testen Sie das Get-proc-Beispiel Cmdlet, um zu sehen, ob es einen Fehler meldet:

- Starten Sie PowerShell, und verwenden Sie das Get-proc-Cmdlet zum Abrufen der Prozesse mit dem Namen "Test".

  ```powershell
  get-proc -name test
  ```

  Die folgende Ausgabe wird angezeigt.

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a>Siehe auch

[Hinzufügen von Parametern, die Pipeline Eingaben verarbeiten](./adding-parameters-that-process-pipeline-input.md)

[Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](./adding-parameters-that-process-command-line-input.md)

[Erstellen Ihres ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erweitern von Objekttypen und Formatierung](/previous-versions/ms714665(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System. Management. Automation. Action Preference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. Cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. Cmdlet. Write error]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
