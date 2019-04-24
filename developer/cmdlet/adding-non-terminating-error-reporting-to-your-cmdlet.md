---
title: Hinzufügen von nicht endenden Fehlerberichte an Ihr Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984237"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Hinzufügen von Berichten für Fehler ohne Abbruch zu Cmdlet

-Cmdlets können Fehler ohne Abbruch durch den Aufruf melden die [System.Management.Automation.Cmdlet.WriteError][] Methode und weiterhin auf das aktuelle Eingabeobjekt oder weiteren eingehenden verwendet werden Objekte pipeline.
In diesem Abschnitt wird erläutert, wie ein Cmdlet zu erstellen, die Fehler ohne Abbruch aus dessen eingabeverarbeitungsmethoden meldet.

Fehler ohne Abbruch (als auch Fehler mit Abbruch), muss das Cmdlet übergeben eine [System.Management.Automation.ErrorRecord][] Objekt, das den Fehler identifiziert.
Jeden Error-Datensatz wird durch eine eindeutige Zeichenfolge, die Namen "Fehler-ID" gekennzeichnet.
Zusätzlich zu den Bezeichner, die Kategorie der einzelnen Fehler von definierten Konstanten gemäß einem [System.Management.Automation.ErrorCategory][] Enumeration.
Der Benutzer kann basierte auf ihrer Kategorie durch Festlegen von Fehlern anzeigen der `$ErrorView` Variable "CategoryView".

Weitere Informationen zu Datensätzen, finden Sie unter [Windows PowerShell-Fehlerdatensätze](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definieren das Cmdlet

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.
Dieses Cmdlet Ruft die Prozessinformationen, ab, der Namen des Verbs hier ausgewählten also "Get".
(Nahezu jede Art von Cmdlets, mit dem Informationen abgerufen werden, kann die Befehlszeileneingabe verarbeiten.) Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](approved-verbs-for-windows-powershell-commands.md).

Im folgenden finden die Definition für dieses Cmdlet "Get-Proc".
Details zu dieser Definition werden in angegebenen [Erstellen Ihrer ersten Cmdlet](creating-a-cmdlet-without-parameters.md).

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

Falls erforderlich, muss Ihr Cmdlet Parameter für die Verarbeitung von Eingaben definieren.
Dieses Cmdlet "Get-Proc" definiert eine **Namen** Parameter wie beschrieben in [Hinzufügen von Parametern die Prozess-Command-Line-Eingabe](adding-parameters-that-process-command-line-input.md).

Hier folgt die Parameterdeklaration für die **Namen** Parameter des Cmdlets Get-Proc.

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

## <a name="overriding-input-processing-methods"></a>Eingabeverarbeitungsmethoden überschreiben

Alle Cmdlets müssen mindestens eines der Eingabe, die Verarbeitung von bereitgestellten Methoden überschreiben die [System.Management.Automation.Cmdlet][] Klasse.
Diese Methoden finden Sie im [Erstellen Ihrer ersten Cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Jeder Datensatz sollte Ihr Cmdlet so unabhängig wie möglich verarbeiten können.

Dieses Cmdlet "Get-Proc" überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord][] Methode zum Behandeln der **Namen** Parameter für die Eingabe durch den Benutzer oder ein Skript bereitgestellt.
Diese Methode erhalten die Prozesse für jede angeforderte Prozessname oder allen Prozessen, wenn kein Name angegeben ist.
Details der Außerkraftsetzung erhalten [Erstellen Ihrer ersten Cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Wichtige Aspekte beim Melden von Fehlern

Die [System.Management.Automation.ErrorRecord][] Objekt, mit das-Cmdlet übergibt, beim Schreiben eines Fehlers eine Ausnahme im Kern ist erforderlich.
Befolgen Sie die .NET-Richtlinien, wenn bestimmt wird die Ausnahme zu verwenden.
Wenn der Fehler semantisch identisch mit einer vorhandenen Ausnahme ist, sollte das-Cmdlet im Grunde verwenden oder diese Ausnahme abgeleitet.
Es sollte, andernfalls der abgeleitet werden, eine neue Ausnahme oder ausnahmenhierarchie direkt aus der [System.Exception][] Klasse.

Beim Erstellen des Fehler-IDs (Zugriff über die FullyQualifiedErrorId-Eigenschaft der Klasse ErrorRecord) sollten Sie Folgendes bedenken.

- Verwenden von Zeichenfolgen, die für Diagnosezwecke, damit Sie beim Untersuchen des vollqualifizierten Bezeichners Worin den Fehler ermitteln können ist und wo der Fehler stammt vorgesehen sind.

- Eine wohlgeformte vollqualifizierten Fehler-ID könnte folgendermaßen aussehen.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Beachten Sie, dass im vorherigen Beispiel, die Fehler-ID (das erste Token) kennzeichnet den Fehler, und der verbleibende Teil gibt an, in dem der Fehler stammt.

- Für komplexere Szenarien kann der Fehler-ID einen Punkt getrennte Token sein, die mit der Untersuchung analysiert werden können.
  Dadurch, dass Sie auch auf die die Fehler-ID als auch für die Fehlerkategorie für Bezeichner und Fehler verzweigen.

Das Cmdlet sollten unterschiedliche Codepfade Fehler Bezeichner zuweisen.
Bedenken Sie die folgende Informationen für die Zuweisung des Fehler-IDs:

- Ein Bezeichner für den Fehler sollte während des Lebenszyklus des Cmdlet konstant bleibt.
  Die Semantik eines Bezeichners Fehler zwischen den Cmdlet-Versionen werden nicht geändert werden.

- Verwenden Sie Text für eine Fehler-ID, die nur sehr knapp entspricht der Fehler gemeldet wird.
  Verwenden Sie keine leer- oder Interpunktionszeichen.

- Haben Sie Ihr Cmdlet nur die Fehler-IDs zu generieren, die reproduzierbar sind.
  Beispielsweise sollten sie keinen Bezeichner generiert, der Prozess-ID enthält.
  Fehler-IDs eignen sich für einen Benutzer nur dann, wenn diese Bezeichner entsprechen, die von anderen Benutzern, die das gleiche Problem bemerkt werden.

Nicht behandelte Ausnahmen werden nicht von PowerShell unter den folgenden Bedingungen abgefangen:

- Wenn ein Cmdlet erstellt einen neuen Thread und Code, der ausgeführt wird, dass Thread eine nicht behandelte Ausnahme auslöst, ist PowerShell fängt keine Fehler und der Prozess beendet wird.

- Verfügt ein Objekt für Code in seinem Destruktor oder die Dispose-Methoden, die eine nicht behandelte Ausnahme auslöst, ist PowerShell fängt keine Fehler und der Prozess beendet wird.

## <a name="reporting-nonterminating-errors"></a>Melden Sie Fehler ohne Abbruch

Eines der eingabeverarbeitungsmethoden kann einen Fehler ohne Abbruch melden, um die Ausgabe-Stream mit der [System.Management.Automation.Cmdlet.WriteError][] Methode.

Hier ist ein Codebeispiel aus diesem Get-Proc-Cmdlet, das veranschaulicht, den Aufruf von [System.Management.Automation.Cmdlet.WriteError][] von innerhalb der Überschreibung der der [System.Management.Automation.Cmdlet.ProcessRecord][] Methode.
In diesem Fall wird der Aufruf ausgelöst, wenn das Cmdlet einen Prozess für eine angegebene Prozess-ID nicht finden kann.

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Punkte zu beachten, die zum Schreiben von Fehler ohne Abbruch

Für einen Fehler ohne Abbruch muss das Cmdlet einen bestimmten Fehler-ID für jeden bestimmten Eingabeobjekt generiert.

Ein Cmdlet muss häufig die PowerShell-Aktion erzeugt einen Fehler ohne Abbruch ändern.
Hierzu können sie definieren die `ErrorAction` und `ErrorVariable` Parameter.
Definieren der `ErrorAction` -Parameter mit dem-Cmdlet zeigt die Benutzeroptionen [System.Management.Automation.ActionPreference][], können Sie die Aktion auch direkt beeinflussen, indem Sie festlegen der `$ErrorActionPreference` Variable.

Das-Cmdlet kann Fehler ohne Abbruch speichern, um eine Variable mit dem `ErrorVariable` -Parameter, der die Einstellung nicht betroffen ist `ErrorAction`.
Fehler bei der können für eine vorhandene Fehlervariable angefügt werden durch das Hinzufügen ein Pluszeichen (+) am Anfang der Variablenname.

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [GetProcessSample04 Beispiel](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.
Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.
Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren.
Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet mit PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.
Testen Sie nun das Beispiel-Get-Proc-Cmdlet, um festzustellen, ob es sich um ein Fehler gemeldet:

- Starten Sie PowerShell, und verwenden Sie das Get-Proc-Cmdlet zum Abrufen der Prozesse, die mit dem Namen "TEST".

    ```powershell
    PS> get-proc -name test
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Weitere Informationen

[Hinzufügen von Parametern, die Eingabe der Prozesspipeline](./adding-parameters-that-process-pipeline-input.md)

[Hinzufügen von Parametern, die Befehlszeileneingabe verarbeiten](./adding-parameters-that-process-command-line-input.md)

[Erstellen eines ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-Referenz](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
