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
ms.openlocfilehash: a4fa9ce52855928679a2425f24f2e49a68030c63
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854916"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="e4d6c-102">Erstellen eines Cmdlet, das das System ändert</span><span class="sxs-lookup"><span data-stu-id="e4d6c-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="e4d6c-103">Manchmal muss ein Cmdlet den Ausführungsstatus des Systems, nicht nur den Status der Windows PowerShell-Laufzeit ändern.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="e4d6c-104">In diesen Fällen sollte mit dem Cmdlet der Benutzer bestätigen, ob die Änderung vorgenommen werden kann.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="e4d6c-105">Zur Unterstützung der Bestätigung muss ein Cmdlet zwei Dinge tun.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="e4d6c-106">Deklarieren Sie, dass das Cmdlet eine Bestätigung unterstützt, bei der Angabe der [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut, indem Sie das SupportsShouldProcess-Schlüsselwort auf `true`.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="e4d6c-107">Rufen Sie [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) während der Ausführung des Cmdlets (wie im folgenden Beispiel gezeigt).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="e4d6c-108">Durch die Unterstützung von Bestätigung, einem Cmdlet stellt die `Confirm` und `WhatIf` Parameter, die von Windows PowerShell bereitgestellt werden, und erfüllt die Richtlinien für die Entwicklung für Cmdlets (Weitere Informationen zu Richtlinien für die Entwicklung von Cmdlets, finden Sie unter [ Richtlinien für die Entwicklung von Cmdlets](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="e4d6c-109">Das System ändern</span><span class="sxs-lookup"><span data-stu-id="e4d6c-109">Changing the System</span></span>

<span data-ttu-id="e4d6c-110">Der Vorgang "das System ändern" bezieht sich auf alle Cmdlets, die den Zustand des Systems außerhalb von Windows PowerShell möglicherweise ändert.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="e4d6c-111">Beenden beispielsweise einen Prozess, aktivieren oder Deaktivieren eines Benutzerkontos oder hinzufügen eine Zeile in einer Datenbanktabelle werden alle Änderungen an das System, das bestätigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="e4d6c-112">Im Gegensatz dazu Vorgänge, die Daten lesen oder vorübergehenden Verbindungen wirken sich nicht auf das System und in der Regel ist die Bestätigung nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="e4d6c-113">Bestätigung ist auch nicht erforderlich für Aktionen, dessen Effekt auf in die Windows PowerShell-Laufzeit, wie z. B. beschränkt ist `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="e4d6c-114">Cmdlets, die möglicherweise keine dauerhafte Änderung vornehmen sollten deklarieren `SupportsShouldProcess` , und rufen Sie [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) nur dann, wenn sie sind im Begriff, eine dauerhafte Änderung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="e4d6c-115">ShouldProcess-Bestätigung gilt nur für Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="e4d6c-116">Wenn ein Befehl oder ein Skript den Ausführungsstatus eines Systems durch den direkten Aufruf .NET Methoden oder Eigenschaften oder aufrufende Anwendungen außerhalb von Windows PowerShell geändert werden, wird diese Form der Bestätigung nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="e4d6c-117">Das StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e4d6c-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="e4d6c-118">In diesem Thema wird beschrieben, einem Stop-Proc-Cmdlet, das versucht, Prozesse zu beenden, die mit dem Get-Proc-Cmdlet abgerufen werden (beschrieben [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="e4d6c-119">Definieren das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e4d6c-119">Defining the Cmdlet</span></span>

<span data-ttu-id="e4d6c-120">Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e4d6c-121">Da Sie ein Cmdlet aus, um das System ändern, schreiben, sollten sie entsprechend benannt werden.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="e4d6c-122">Dieses Cmdlet beendet Systemprozesse, also der Namen des Verbs hier ausgewählten "Stop", definiert durch die [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) Klasse, mit dem Namen "Proc", um anzugeben, dass das Cmdlet die Prozesse beendet.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="e4d6c-123">Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e4d6c-124">Folgendes ist die Definition der Klasse für dieses Cmdlet Stop-Prozessor.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="e4d6c-125">Beachten Sie, dass in der [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Deklaration der `SupportsShouldProcess` Schlüsselwort nastaven NA hodnotu `true` So aktivieren Sie das Cmdlet Aufrufe an [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="e4d6c-126">Ohne dieses Schlüsselwort wird die `Confirm` und `WhatIf` Parameter werden nicht für den Benutzer verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="e4d6c-127">Sehr weitreichend Aktionen</span><span class="sxs-lookup"><span data-stu-id="e4d6c-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="e4d6c-128">Einige Vorgänge sind sehr weitreichend sein, z. B. neu formatieren einer Festplattenpartition aktiv.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="e4d6c-129">In diesen Fällen sollte das-Cmdlet festgelegt `ConfirmImpact`  =  `ConfirmImpact.High` beim Deklarieren der [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Attribut.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="e4d6c-130">Diese Einstellung erzwingt, dass das Cmdlet auf Anforderung Bestätigung durch den Benutzer sogar, wenn der Benutzer nicht angegeben die `Confirm` Parameter.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="e4d6c-131">Allerdings Cmdlet-Entwickler sollten eine übermäßige Verwendung `ConfirmImpact` für Vorgänge, die nur potenziell schädlicher, wie z. B. das Löschen eines Benutzerkontos sind.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="e4d6c-132">Denken Sie daran, dass bei `ConfirmImpact` nastaven NA hodnotu [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="e4d6c-133">Ebenso sind einige Vorgänge wahrscheinlich nicht zerstörerische, obwohl sie in der Theorie den Ausführungsstatus eines Systems außerhalb von Windows PowerShell ändern.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="e4d6c-134">Legen Sie diese Cmdlets können `ConfirmImpact` zu [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="e4d6c-135">Diese Bestätigung Anforderungen, umgehen die, in denen der Benutzer aufgefordert wurde, um nur die mittlere Auswirkungen und mit schwerwiegenden Auswirkungen Vorgänge zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="e4d6c-136">Definieren von Parametern für die System-Änderung</span><span class="sxs-lookup"><span data-stu-id="e4d6c-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="e4d6c-137">Dieser Abschnitt beschreibt, wie Sie definieren die Cmdlet-Parameter, einschließlich derjenigen, die sich für Unterstützung von Änderungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="e4d6c-138">Finden Sie unter [Hinzufügen von Parametern, Eingabe CommandLine](./adding-parameters-that-process-command-line-input.md) , wenn Sie allgemeine Informationen zum Definieren von Parametern benötigen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="e4d6c-139">Das Cmdlet "Stop-Proc" definiert drei Parameter: `Name`, `Force`, und `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="e4d6c-140">Die `Name` Parameter entspricht der `Name` Eigenschaft des Eingabeobjekts Prozess.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="e4d6c-141">Beachten Sie, die die `Name` Parameter in diesem Beispiel ist zwingend erforderlich ist, wie das Cmdlet fehl, wenn sie nicht über einen benannten Prozess beenden verfügt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="e4d6c-142">Die `Force` Parameter ermöglicht den Benutzer, überschreiben Aufrufe von [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="e4d6c-143">In der Tat ein Cmdlet aufruft, [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) sollte eine `Force` Parameter, damit beim `Force` angegeben ist, wird das-Cmdlet wird übersprungen, den Aufruf von [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) und der Vorgang wird fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="e4d6c-144">Beachten Sie, dass dadurch nicht, dass Aufrufe von beeinträchtigt [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="e4d6c-145">Die `PassThru` Parameter ermöglicht dem Benutzer an, ob das Cmdlet ein Ausgabeobjekt über die Pipeline in diesem Fall übergibt, nachdem ein Prozess beendet wird.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="e4d6c-146">Denken Sie daran, dass dieser Parameter an das Cmdlet selbst und nicht auf eine Eigenschaft des Eingabeobjekts gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="e4d6c-147">Hier ist die Parameterdeklaration für das Stop-Proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e4d6c-148">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="e4d6c-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e4d6c-149">Das Cmdlet muss ein eingabeverarbeitungsmethode überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="e4d6c-150">Der folgende Code zeigt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) außer Kraft setzen, die in der Beispiel-Stop-Proc-Cmdlet verwendet.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="e4d6c-151">Für jede Name des Prozesses angefordert, von dieser Methode wird sichergestellt, dass der Prozess keinen besonderen Prozess, versucht, den Prozess zu beenden, und klicken Sie dann ein Ausgabeobjekt sendet, wenn die `PassThru` Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="e4d6c-152">Aufrufen der ShouldProcess-Methode</span><span class="sxs-lookup"><span data-stu-id="e4d6c-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="e4d6c-153">Eingabeverarbeitungsmethode Ihre Cmdlets aufrufen sollten die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode, um die Ausführung eines Vorgangs zu bestätigen, bevor eine Änderung (z. B. das Löschen von Dateien) in den Ausführungsstatus vorgenommen wird des Systems.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="e4d6c-154">Dadurch wird die Windows PowerShell-Laufzeit das richtige "WhatIf" und "Bestätigen" Verhalten innerhalb der Shell bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="e4d6c-155">Wenn ein Cmdlet gibt an, dass er unterstützt verarbeitet werden soll, und ein Fehler auftritt, stellen die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aufrufen, kann der Benutzer des Systems unerwartet ändern.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="e4d6c-156">Der Aufruf von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sendet den Namen der Ressource, die für den Benutzer geändert werden, mit der Windows PowerShell-Laufzeit berücksichtigt alle befehlszeileneinstellungen oder der Preference-Variablen Bei der Bestimmung, was dem Benutzer angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="e4d6c-157">Das folgende Beispiel zeigt den Aufruf von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aus überschreiben die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode im Beispiel Stop-Proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="e4d6c-158">Aufrufen der Methode "shouldcontinue"</span><span class="sxs-lookup"><span data-stu-id="e4d6c-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="e4d6c-159">Der Aufruf der [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode sendet eine sekundäre Nachricht an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="e4d6c-160">Dieser Aufruf erfolgt, nach dem Aufruf von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) gibt `true` und, wenn die `Force` Parameter wurde nicht festgelegt, um `true`.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="e4d6c-161">Der Benutzer kann dann bereitstellen, Feedback, um festzustellen, ob der Vorgang fortgesetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="e4d6c-162">Ihr Cmdlet ruft [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) als eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen oder wenn Sie allgemeingültige Ja und Nein-zu-alle Optionen für den Benutzer bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="e4d6c-163">Das folgende Beispiel zeigt den Aufruf von [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aus überschreiben die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode im Beispiel Stop-Proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="e4d6c-164">Beenden des Eingabeverarbeitung</span><span class="sxs-lookup"><span data-stu-id="e4d6c-164">Stopping Input Processing</span></span>

<span data-ttu-id="e4d6c-165">Eingabeverarbeitungsmethode von einem Cmdlet, das System Änderungen vornimmt, muss eine Möglichkeit zum Beenden der Verarbeitung der Eingabe angeben.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="e4d6c-166">Im Fall von diesem Cmdlet Stop-Proc erfolgt ein Aufruf von der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode, um die [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) Methode.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="e4d6c-167">Da die `PassThru` Parametersatz zu `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ruft auch [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) senden Das Prozessobjekt an die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e4d6c-168">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="e4d6c-168">Code Sample</span></span>

<span data-ttu-id="e4d6c-169">Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample01 Beispiel](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="e4d6c-170">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="e4d6c-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="e4d6c-171">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="e4d6c-172">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e4d6c-173">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e4d6c-174">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e4d6c-174">Building the Cmdlet</span></span>

<span data-ttu-id="e4d6c-175">Nach der Implementierung eines Cmdlets, müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e4d6c-176">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e4d6c-177">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e4d6c-177">Testing the Cmdlet</span></span>

<span data-ttu-id="e4d6c-178">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e4d6c-179">Hier sind mehrere Tests, die die Stop-Proc-Cmdlet testen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="e4d6c-180">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e4d6c-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="e4d6c-181">Starten Sie Windows PowerShell, und verwenden Sie das Stop-Proc-Cmdlet nicht mehr verarbeitet werden, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="e4d6c-182">Da das Cmdlet gibt die `Name` Parameter als obligatorisch, die Cmdlet-Abfragen für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="e4d6c-183">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="e4d6c-184">Jetzt verwenden wir das Cmdlet den namens "NOTEPAD" Prozess beenden.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="e4d6c-185">Das Cmdlet fordert Sie auf die Aktion zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="e4d6c-186">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="e4d6c-187">Verwenden Sie zum Beenden der kritischen Prozess mit dem Namen "Windows-Anmeldung" Stop-Proc wie gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="e4d6c-188">Sie werden dazu aufgefordert werden und zum Ausführen dieser Aktion aus, da sie das Betriebssystem neu starten, hervorrufen würde eine Warnung.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="e4d6c-189">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="e4d6c-190">Lassen Sie uns nun versuchen, den WINLOGON-Prozess zu beenden, ohne dass eine Warnung.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="e4d6c-191">Beachten Sie, dass dieser Befehlseintrag verwendet den `Force` Parameter, um die Warnung außer Kraft zu setzen.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="e4d6c-192">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4d6c-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="e4d6c-193">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e4d6c-193">See Also</span></span>

[<span data-ttu-id="e4d6c-194">Hinzufügen von Parametern, die Befehlszeileneingabe verarbeiten</span><span class="sxs-lookup"><span data-stu-id="e4d6c-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="e4d6c-195">Erweitern die Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="e4d6c-195">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="e4d6c-196">So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen</span><span class="sxs-lookup"><span data-stu-id="e4d6c-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e4d6c-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e4d6c-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e4d6c-198">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="e4d6c-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)