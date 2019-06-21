---
title: Erstellen ein Cmdlet, ändert das System | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301400"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Erstellen eines Cmdlet, das das System ändert

Manchmal muss ein Cmdlet den Ausführungsstatus des Systems, nicht nur den Status der Windows PowerShell-Laufzeit ändern. In diesen Fällen sollte mit dem Cmdlet der Benutzer bestätigen, ob die Änderung vorgenommen werden kann.

Zur Unterstützung der Bestätigung muss ein Cmdlet zwei Dinge tun.

- Deklarieren Sie, dass das Cmdlet eine Bestätigung unterstützt, bei der Angabe der [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut, indem Sie das SupportsShouldProcess-Schlüsselwort auf `true`.

- Rufen Sie [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) während der Ausführung des Cmdlets (wie im folgenden Beispiel gezeigt).

Durch die Unterstützung von Bestätigung, einem Cmdlet stellt die `Confirm` und `WhatIf` Parameter, die von Windows PowerShell bereitgestellt werden, und erfüllt die Richtlinien für die Entwicklung für Cmdlets (Weitere Informationen zu Richtlinien für die Entwicklung von Cmdlets, finden Sie unter [ Richtlinien für die Entwicklung von Cmdlets](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Das System ändern

Der Vorgang "das System ändern" bezieht sich auf alle Cmdlets, die den Zustand des Systems außerhalb von Windows PowerShell möglicherweise ändert. Beenden beispielsweise einen Prozess, aktivieren oder Deaktivieren eines Benutzerkontos oder hinzufügen eine Zeile in einer Datenbanktabelle werden alle Änderungen an das System, das bestätigt werden soll. Im Gegensatz dazu Vorgänge, die Daten lesen oder vorübergehenden Verbindungen wirken sich nicht auf das System und in der Regel ist die Bestätigung nicht erforderlich. Bestätigung ist auch nicht erforderlich für Aktionen, dessen Effekt auf in die Windows PowerShell-Laufzeit, wie z. B. beschränkt ist `set-variable`. Cmdlets, die möglicherweise keine dauerhafte Änderung vornehmen sollten deklarieren `SupportsShouldProcess` , und rufen Sie [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) nur dann, wenn sie sind im Begriff, eine dauerhafte Änderung vornehmen.

> [!NOTE]
> ShouldProcess-Bestätigung gilt nur für Cmdlets. Wenn ein Befehl oder ein Skript den Ausführungsstatus eines Systems durch den direkten Aufruf .NET Methoden oder Eigenschaften oder aufrufende Anwendungen außerhalb von Windows PowerShell geändert werden, wird diese Form der Bestätigung nicht verfügbar.

## <a name="the-stopproc-cmdlet"></a>Das StopProc Cmdlet

In diesem Thema wird beschrieben, einem Stop-Proc-Cmdlet, das versucht, Prozesse zu beenden, die mit dem Get-Proc-Cmdlet abgerufen werden (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definieren das Cmdlet

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren. Da Sie ein Cmdlet aus, um das System ändern, schreiben, sollten sie entsprechend benannt werden. Dieses Cmdlet beendet Systemprozesse, also der Namen des Verbs hier ausgewählten "Stop", definiert durch die [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) Klasse, mit dem Namen "Proc", um anzugeben, dass das Cmdlet die Prozesse beendet. Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Folgendes ist die Definition der Klasse für dieses Cmdlet Stop-Prozessor.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Beachten Sie, dass in der [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Deklaration der `SupportsShouldProcess` Schlüsselwort nastaven NA hodnotu `true` So aktivieren Sie das Cmdlet Aufrufe an [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Ohne dieses Schlüsselwort wird die `Confirm` und `WhatIf` Parameter werden nicht für den Benutzer verfügbar sein.

### <a name="extremely-destructive-actions"></a>Sehr weitreichend Aktionen

Einige Vorgänge sind sehr weitreichend sein, z. B. neu formatieren einer Festplattenpartition aktiv. In diesen Fällen sollte das-Cmdlet festgelegt `ConfirmImpact`  =  `ConfirmImpact.High` beim Deklarieren der [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut. Diese Einstellung erzwingt, dass das Cmdlet auf Anforderung Bestätigung durch den Benutzer sogar, wenn der Benutzer nicht angegeben die `Confirm` Parameter. Allerdings Cmdlet-Entwickler sollten eine übermäßige Verwendung `ConfirmImpact` für Vorgänge, die nur potenziell schädlicher, wie z. B. das Löschen eines Benutzerkontos sind. Denken Sie daran, dass bei `ConfirmImpact` nastaven NA hodnotu [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **hohe**.

Ebenso sind einige Vorgänge wahrscheinlich nicht zerstörerische, obwohl sie in der Theorie den Ausführungsstatus eines Systems außerhalb von Windows PowerShell ändern. Legen Sie diese Cmdlets können `ConfirmImpact` zu [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Diese Bestätigung Anforderungen, umgehen die, in denen der Benutzer aufgefordert wurde, um nur die mittlere Auswirkungen und mit schwerwiegenden Auswirkungen Vorgänge zu bestätigen.

## <a name="defining-parameters-for-system-modification"></a>Definieren von Parametern für die System-Änderung

Dieser Abschnitt beschreibt, wie Sie definieren die Cmdlet-Parameter, einschließlich derjenigen, die sich für Unterstützung von Änderungen erforderlich sind. Finden Sie unter [Hinzufügen von Parametern, Eingabe CommandLine](./adding-parameters-that-process-command-line-input.md) , wenn Sie allgemeine Informationen zum Definieren von Parametern benötigen.

Das Cmdlet "Stop-Proc" definiert drei Parameter: `Name`, `Force`, und `PassThru`.

Die `Name` Parameter entspricht der `Name` Eigenschaft des Eingabeobjekts Prozess. Beachten Sie, die die `Name` Parameter in diesem Beispiel ist zwingend erforderlich ist, wie das Cmdlet fehl, wenn sie nicht über einen benannten Prozess beenden verfügt.

Die `Force` Parameter ermöglicht den Benutzer, überschreiben Aufrufe von [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). In der Tat ein Cmdlet aufruft, [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) sollte eine `Force` Parameter, damit beim `Force` angegeben ist, wird das-Cmdlet wird übersprungen, den Aufruf von [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) und der Vorgang wird fortgesetzt. Beachten Sie, dass dadurch nicht, dass Aufrufe von beeinträchtigt [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Die `PassThru` Parameter ermöglicht dem Benutzer an, ob das Cmdlet ein Ausgabeobjekt über die Pipeline in diesem Fall übergibt, nachdem ein Prozess beendet wird. Denken Sie daran, dass dieser Parameter an das Cmdlet selbst und nicht auf eine Eigenschaft des Eingabeobjekts gebunden ist.

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

Das Cmdlet muss ein eingabeverarbeitungsmethode überschrieben werden. Der folgende Code zeigt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) außer Kraft setzen, die in der Beispiel-Stop-Proc-Cmdlet verwendet. Für jede Name des Prozesses angefordert, von dieser Methode wird sichergestellt, dass der Prozess keinen besonderen Prozess, versucht, den Prozess zu beenden, und klicken Sie dann ein Ausgabeobjekt sendet, wenn die `PassThru` Parameter angegeben ist.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>Aufrufen der ShouldProcess-Methode

Eingabeverarbeitungsmethode Ihre Cmdlets aufrufen sollten die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode, um die Ausführung eines Vorgangs zu bestätigen, bevor eine Änderung (z. B. das Löschen von Dateien) in den Ausführungsstatus vorgenommen wird des Systems. Dadurch wird die Windows PowerShell-Laufzeit das richtige "WhatIf" und "Bestätigen" Verhalten innerhalb der Shell bereitstellen.

> [!NOTE]
> Wenn ein Cmdlet gibt an, dass er unterstützt verarbeitet werden soll, und ein Fehler auftritt, stellen die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aufrufen, kann der Benutzer des Systems unerwartet ändern.

Der Aufruf von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sendet den Namen der Ressource, die für den Benutzer geändert werden, mit der Windows PowerShell-Laufzeit berücksichtigt alle befehlszeileneinstellungen oder der Preference-Variablen Bei der Bestimmung, was dem Benutzer angezeigt werden soll.

Das folgende Beispiel zeigt den Aufruf von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aus überschreiben die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode im Beispiel Stop-Proc-Cmdlet.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Aufrufen der Methode "shouldcontinue"

Der Aufruf der [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode sendet eine sekundäre Nachricht an den Benutzer. Dieser Aufruf erfolgt, nach dem Aufruf von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) gibt `true` und, wenn die `Force` Parameter wurde nicht festgelegt, um `true`. Der Benutzer kann dann bereitstellen, Feedback, um festzustellen, ob der Vorgang fortgesetzt werden soll. Ihr Cmdlet ruft [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) als eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen oder wenn Sie allgemeingültige Ja und Nein-zu-alle Optionen für den Benutzer bereitstellen möchten.

Das folgende Beispiel zeigt den Aufruf von [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aus überschreiben die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode im Beispiel Stop-Proc-Cmdlet.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Beenden des Eingabeverarbeitung

Eingabeverarbeitungsmethode von einem Cmdlet, das System Änderungen vornimmt, muss eine Möglichkeit zum Beenden der Verarbeitung der Eingabe angeben. Im Fall von diesem Cmdlet Stop-Proc erfolgt ein Aufruf von der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode, um die [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) Methode. Da die `PassThru` Parametersatz zu `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ruft auch [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) senden Das Prozessobjekt an die Pipeline.

## <a name="code-sample"></a>Codebeispiel

Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample01 Beispiel](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten. Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen. Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen. Hier sind mehrere Tests, die die Stop-Proc-Cmdlet testen. Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starten Sie Windows PowerShell, und verwenden Sie das Stop-Proc-Cmdlet nicht mehr verarbeitet werden, wie unten dargestellt. Da das Cmdlet gibt die `Name` Parameter als obligatorisch, die Cmdlet-Abfragen für den Parameter.

    ```powershell
    PS> stop-proc
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Jetzt verwenden wir das Cmdlet den namens "NOTEPAD" Prozess beenden. Das Cmdlet fordert Sie auf die Aktion zu bestätigen.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Die folgende Ausgabe wird angezeigt.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Verwenden Sie zum Beenden der kritischen Prozess mit dem Namen "Windows-Anmeldung" Stop-Proc wie gezeigt. Sie werden dazu aufgefordert werden und zum Ausführen dieser Aktion aus, da sie das Betriebssystem neu starten, hervorrufen würde eine Warnung.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Die folgende Ausgabe wird angezeigt.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Lassen Sie uns nun versuchen, den WINLOGON-Prozess zu beenden, ohne dass eine Warnung. Beachten Sie, dass dieser Befehlseintrag verwendet den `Force` Parameter, um die Warnung außer Kraft zu setzen.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Die folgende Ausgabe wird angezeigt.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Weitere Informationen

[Hinzufügen von Parametern, die Befehlszeileneingabe verarbeiten](./adding-parameters-that-process-command-line-input.md)

[Erweitern die Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet-Beispiele](./cmdlet-samples.md)