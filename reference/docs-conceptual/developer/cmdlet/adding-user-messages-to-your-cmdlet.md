---
title: Hinzufügen von Benutzer Nachrichten zum Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416028"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Hinzufügen von Benutzermeldungen zum Cmdlet

Cmdlets können verschiedene Arten von Nachrichten schreiben, die dem Benutzer von der Windows PowerShell-Laufzeit angezeigt werden können. Diese Meldungen enthalten die folgenden Typen:

- Ausführliche Meldungen, die allgemeine Benutzerinformationen enthalten.

- Debugmeldungen, die Informationen zur Problembehandlung enthalten.

- Warnmeldungen, die eine Benachrichtigung enthalten, dass das Cmdlet einen Vorgang ausführt, der unerwartete Ergebnisse aufweisen kann.

- Fortschrittsberichts Meldungen mit Informationen darüber, wie viel Arbeit das Cmdlet beim Ausführen eines Vorgangs abgeschlossen hat, der lange dauert.

Es gibt keine Beschränkung für die Anzahl der Nachrichten, die das Cmdlet schreiben kann, oder den Typ der Nachrichten, die vom Cmdlet geschrieben werden. Jede Nachricht wird durch einen bestimmten-Rückruf aus der Eingabe Verarbeitungsmethode des Cmdlets geschrieben.

## <a name="defining-the-cmdlet"></a>Definieren des Cmdlets

Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert. Jede Art von Cmdlet kann Benutzer Benachrichtigungen von den Eingabe Verarbeitungsmethoden schreiben. im Allgemeinen können Sie dieses Cmdlet mit einem beliebigen Verb benennen, das angibt, welche Systemänderungen das Cmdlet ausführt. Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

Das Cmdlet "halte-proc" wurde entwickelt, um das System zu ändern. Daher muss die [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -Deklaration für die .NET-Klasse das `SupportsShouldProcess` Attribute-Schlüsselwort einschließen und auf `true`festgelegt werden.

Der folgende Code ist die Definition für diese Cmdlet-Klasse "". Weitere Informationen zu dieser Definition finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definieren von Parametern für die System Änderung

Das Cmdlet "Break-proc" definiert drei Parameter: `Name`, `Force`und `PassThru`. Weitere Informationen zum Definieren dieser Parameter finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).

Hier ist die Parameter Deklaration für das Cmdlet "halte-proc".

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabe Verarbeitungsmethode

Ihr Cmdlet muss eine Eingabe Verarbeitungsmethode überschreiben, meistens handelt es sich um [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Dieses Cmdlet "Pause-proc" überschreibt die Eingabe Verarbeitungsmethode " [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ". In dieser Implementierung des Cmdlets "halte-proc" werden Aufrufe zum Schreiben ausführlicher Nachrichten, Debugmeldungen und Warnmeldungen durchgeführt.

> [!NOTE]
> Weitere Informationen dazu, wie diese Methode die Methoden " [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. dendcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " aufruft, finden Sie unter [Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Schreiben einer ausführlichen Nachricht

Die [System. Management. Automation. Cmdlet. Write-Verbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) -Methode wird verwendet, um allgemeine Informationen auf Benutzerebene zu schreiben, die mit bestimmten Fehlerbedingungen nicht verknüpft sind. Der Systemadministrator kann diese Informationen dann verwenden, um mit der Verarbeitung anderer Befehle fortzufahren. Außerdem sollten alle Informationen, die mit dieser Methode geschrieben wurden, nach Bedarf lokalisiert werden.

Der folgende Code aus diesem Cmdlet "Pause-proc" zeigt zwei Aufrufe der [System. Management. Automation. Cmdlet. Write](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Items-Methode aus der außer Kraft setzung der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Schreiben einer Debugmeldung

Die [System. Management. Automation. Cmdlet. Write-Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode wird verwendet, um Debugmeldungen zu schreiben, die für die Problembehandlung des Cmdlets verwendet werden können. Der-Befehl wird von einer Eingabe Verarbeitungsmethode aufgerufen.

> [!NOTE]
> Windows PowerShell definiert auch einen `Debug` Parameter, der sowohl ausführliche als auch Debuginformationen darstellt. Wenn das Cmdlet diesen Parameter unterstützt, muss das [System. Management. Automation. Cmdlet. Write-Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) nicht im gleichen Code aufgerufen werden, der [System. Management. Automation. Cmdlet. Write-Verbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)aufruft.

Die folgenden beiden Code Abschnitte aus dem Beispiel-Cmdlet "Pause-proc" zeigen Aufrufe der [System. Management. Automation. Cmdlet. Write Team Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode aus der Überschreibung der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode an.

Diese Debugmeldung wird unmittelbar vor dem Aufruf von [System. Management. Automation. Cmdlet. Schulter Process](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) geschrieben.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Diese Debugmeldung wird unmittelbar vor dem Aufruf von [System. Management. Automation. Cmdlet. Write-Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) geschrieben.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell leitet automatisch alle [System. Management. Automation. Cmdlet. Write-Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Aufrufe an die Ablauf Verfolgungs Infrastruktur und-Cmdlets weiter. Dies ermöglicht es, dass die Methodenaufrufe auf die Host Anwendung, eine Datei oder einen Debugger nachverfolgt werden, ohne dass Sie zusätzliche Entwicklungsaufgaben innerhalb des Cmdlets ausführen müssen. Der folgende Befehlszeilen Eintrag implementiert einen Ablauf Verfolgungs Vorgang.

**PS > Trace-Expression-Vorgang zum Abbrechen der Prozedur "-proc-File proc. log-Command".**

## <a name="writing-a-warning-message"></a>Schreiben einer Warnmeldung

Die [System. Management. Automation. Cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) -Methode wird verwendet, um eine Warnung zu schreiben, wenn das Cmdlet einen Vorgang ausführt, der möglicherweise ein unerwartetes Ergebnis hat, z. b. eine schreibgeschützte Datei.

Der folgende Code aus dem Beispiel Ende-proc-Cmdlet zeigt den aufzurufenden Befehl der [System. Management. Automation. Cmdlet. Write-Warning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) -Methode aus der außer Kraft setzung der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Schreiben einer Fortschrittsmeldung

Der [System. Management. Automation. Cmdlet. Write Progress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wird zum Schreiben von Statusmeldungen verwendet, wenn die Ausführung von Cmdlet-Vorgängen eine längere Zeit in Anspruch nimmt. Ein System [. Management. Automation. Cmdlet. Write](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) -Vorgang übergibt ein [System. Management. Automation. progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -Objekt, das zum Rendern an den Benutzer an die Host Anwendung gesendet wird.

> [!NOTE]
> Dieses Cmdlet "Pause-proc" enthält keinen aufrufsvorgang der [System. Management. Automation. Cmdlet. Write Progress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) -Methode.

Der folgende Code ist ein Beispiel für eine Fortschrittsmeldung, die von einem Cmdlet geschrieben wird, das versucht, ein Element zu kopieren.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Code Beispiel

Den gesamten C# Beispielcode finden Sie unter [StopProcessSample02 Sample](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets mithilfe von .NET-Objekten. Folglich muss ein Cmdlet möglicherweise seinen eigenen Typ definieren, oder das Cmdlet muss möglicherweise einen vorhandenen Typ erweitern, der von einem anderen Cmdlet bereitgestellt wird. Weitere Informationen zum Definieren neuer Typen oder zum Erweitern vorhandener Typen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem ein Cmdlet implementiert wurde, muss es über ein Windows PowerShell-Snap-in in Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet bei Windows PowerShell registriert wurde, können Sie es in der Befehlszeile testen. Testen Sie das Beispiel-Cmdlet "Stopp-proc". Weitere Informationen zur Verwendung von Cmdlets über die Befehlszeile finden Sie unter [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Der folgende Befehlszeilen Eintrag verwendet "Ende-proc", um den Prozess mit dem Namen "Notepad" anzuhalten, ausführliche Benachrichtigungen bereitzustellen und Debuginformationen zu drucken.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Siehe auch

[Erstellen Sie ein Cmdlet, das das System ändert.](./creating-a-cmdlet-that-modifies-the-system.md)

[Erstellen eines Windows PowerShell-Cmdlets](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
