---
title: Hinzufügen von Benutzernachrichten zu Ihr Cmdlet | Microsoft-Dokumentation
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
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068775"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Hinzufügen von Benutzermeldungen zum Cmdlet

Cmdlets können mehrere Arten von Meldungen zu schreiben, die von der Windows PowerShell-Laufzeit, die dem Benutzer angezeigt werden können. Diese Nachrichten enthalten die folgenden Typen:

- Ausführliche Meldungen, die allgemeine Benutzerinformationen enthalten.

- Debuggen von Nachrichten, die Informationen zur Problembehandlung enthalten.

- Warnmeldungen, die eine Benachrichtigung zu enthalten, die das Cmdlet einen Vorgang auszuführen, die verfügen, können unerwartete Ergebnisse.

- Statusbericht, dass Nachrichten mit Informationen dazu, wie lange das-Cmdlet funktioniert wurde abgeschlossen, beim Durchführen eines Vorgangs, das sehr lange dauert.

Es gibt keine Beschränkungen auf die Anzahl der Nachrichten, die Ihr Cmdlet schreiben kann, oder den Typ der Meldungen, die Ihr Cmdlet schreibt. Jede Nachricht wird von einem bestimmten Aufruf von innerhalb der Eingabe Verarbeitungsmethode Ihres Cmdlets geschrieben.

## <a name="the-stopproc-cmdlet"></a>Das StopProc Cmdlet

Die folgenden: Themen in diesem Abschnitt

- [Definieren das Cmdlet](#Defining-the-Cmdlet)

- [Definieren von Parametern für die System-Änderung](#Defining-Parameters-for-System-Modification)

- [Überschreiben einer Eingabeverarbeitungsmethode](#Overriding-an-Input-Processing-Method)

- [Eine ausführliche Meldung schreiben](#Writing-a-Verbose-Message)

- [Schreiben Sie eine Debugmeldung](#Writing-a-Debug-Message)

- [Schreiben Sie eine Warnung angezeigt](#Writing-a-Warning-Message)

- [Schreiben Sie eine Statusmeldung](#Writing-a-Progress-Message)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#Define-Object-Types-and-Formatting)

- [Erstellen das Cmdlet](#Building-the-Cmdlet)

- [Testen das Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definieren das Cmdlet

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren. Ein beliebiges Cmdlet kann die eingabeverarbeitungsmethoden benutzerbenachrichtigungen schreiben; Daher können im Allgemeinen Sie Namen mit diesem Cmdlet verwenden alle Verben, die welche systemmodifizierungen gibt an, das-Cmdlet führt. Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Die Stop-Proc-Cmdlet wurde entwickelt, das System ändern; aus diesem Grund die [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Deklaration für die .NET-Klasse muss enthalten der `SupportsShouldProcess` Attribut Schlüsselwort und festgelegt werden, `true`.

Der folgende Code ist die Definition für dieses Cmdlet Stop-Proc-Klasse. Weitere Informationen zu dieser Definition, finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definieren von Parametern für die System-Änderung

Das Cmdlet "Stop-Proc" definiert drei Parameter: `Name`, `Force`, und `PassThru`. Weitere Informationen zum Definieren von diesen Parametern finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).

Hier ist die Parameterdeklaration für das Stop-Proc-Cmdlet.

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

## <a name="overriding-an-input-processing-method"></a>Überschreiben einer Eingabeverarbeitungsmethode

Ihr Cmdlet ein eingabeverarbeitungsmethode muss überschrieben werden, am häufigsten wird [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Dieses Cmdlet Stop-Proc überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Geben Sie die Verarbeitungsmethode aus. In dieser Implementierung des Stop-Proc-Cmdlets sind Aufrufe durchgeführt, um ausführliche Meldungen, Warnmeldungen und Debugmeldungen zu schreiben.

> [!NOTE]
> Weitere Informationen, wie diese Methode ruft die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden finden Sie unter [Ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Eine ausführliche Meldung schreiben

Die [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode wird verwendet, um allgemeine auf Benutzerebene Informationen zu schreiben, die unabhängig von bestimmten fehlerbedingungen ist. Der Systemadministrator kann dann diese Informationen verwenden, und weiter verarbeitet, andere Befehle. Darüber hinaus sollte alle Informationen geschrieben, mit dieser Methode lokalisiert werden, je nach Bedarf.

Der folgende Code aus diesem Stop-Proc-Cmdlet zeigt die beiden Aufrufe von der [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) die Überschreibung der Methode die [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Schreiben Sie eine Debugmeldung

Die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Methode wird verwendet, um Debugmeldungen zu schreiben, die verwendet werden kann, um den Vorgang des-Cmdlets beheben. Der Aufruf von einem eingabeverarbeitungsmethode erfolgt.

> [!NOTE]
> Windows PowerShell definiert auch eine `Debug` Parameter, die stellt sowohl ausführliche Informationen zum Debuggen. Wenn Ihr Cmdlet dieser Parameter unterstützt, muss es nicht rufen [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in den gleichen Code, aufruft [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

Die folgenden beiden Abschnitte des Codes aus dem Beispiel beenden-Proc-Cmdlet anzeigen, Aufrufe an die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) die Überschreibung der Methode die [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.

Diese Debugmeldung wird unmittelbar vor geschrieben [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aufgerufen wird.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Diese Debugmeldung wird unmittelbar vor geschrieben [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) aufgerufen wird.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell automatisch alle weiterleitet [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Aufrufe an die Infrastruktur für ereignisablaufverfolgung und -Cmdlets. Dadurch werden die Methodenaufrufe zum in der hostanwendung, einer Datei oder einen Debugger nachverfolgt werden, ohne dass zusätzliche Entwicklungsarbeiten in das-Cmdlet auszuführen. Die folgende Befehlszeile Eintrag implementiert einen Vorgang für die Ablaufverfolgung.

**PS > Trace-Ausdruck Stop-Proc-Datei proc.log-Befehl Beenden-Proc-Editor**

## <a name="writing-a-warning-message"></a>Schreiben Sie eine Warnung angezeigt

Die [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) Methode dient zum Schreiben einer Warnung, wenn das Cmdlet einen Vorgang ausführen, die möglicherweise ein unerwartetes Ergebnis, z. B. das Überschreiben einer schreibgeschützten Datei ist.

Der folgende Code aus der Beispiel-Stop-Proc-Cmdlet wird der Aufruf der [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) die Überschreibung der Methode die [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Schreiben Sie eine Statusmeldung

Die [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wird verwendet, um statusmeldungen zu schreiben, wenn der Cmdlet-Vorgänge für einige Zeit in Anspruch in Anspruch nehmen. Ein Aufruf von [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) übergibt eine [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -Objekt, das an die hostanwendung für das Rendering für den Benutzer gesendet wird.

> [!NOTE]
> Diese Stop-Proc-Cmdlet enthält keinen Aufruf der [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) Methode.

Der folgende Code ist ein Beispiel für eine Statusmeldung geschrieben, die von einem Cmdlet an, der versucht, ein Element zu kopieren.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample02 Beispiel](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen. Testen Sie nun das Beispiel beenden-Proc-Cmdlet. Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Die folgende Befehlszeile-Eintrag verwendet Stop-Proc Namen "NOTEPAD" Prozess beenden, geben ausführliche Benachrichtigungen und Drucken von Debuginformationen.

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

## <a name="see-also"></a>Weitere Informationen

[Erstellen Sie ein Cmdlet, das das System geändert wird](./creating-a-cmdlet-that-modifies-the-system.md)

[Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
