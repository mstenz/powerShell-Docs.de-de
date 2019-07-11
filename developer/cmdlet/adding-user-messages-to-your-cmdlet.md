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
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733753"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="c5859-102">Hinzufügen von Benutzermeldungen zum Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c5859-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="c5859-103">Cmdlets können mehrere Arten von Meldungen zu schreiben, die von der Windows PowerShell-Laufzeit, die dem Benutzer angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="c5859-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="c5859-104">Diese Nachrichten enthalten die folgenden Typen:</span><span class="sxs-lookup"><span data-stu-id="c5859-104">These messages include the following types:</span></span>

- <span data-ttu-id="c5859-105">Ausführliche Meldungen, die allgemeine Benutzerinformationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="c5859-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="c5859-106">Debuggen von Nachrichten, die Informationen zur Problembehandlung enthalten.</span><span class="sxs-lookup"><span data-stu-id="c5859-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="c5859-107">Warnmeldungen, die eine Benachrichtigung zu enthalten, die das Cmdlet einen Vorgang auszuführen, die verfügen, können unerwartete Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="c5859-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="c5859-108">Statusbericht, dass Nachrichten mit Informationen dazu, wie lange das-Cmdlet funktioniert wurde abgeschlossen, beim Durchführen eines Vorgangs, das sehr lange dauert.</span><span class="sxs-lookup"><span data-stu-id="c5859-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="c5859-109">Es gibt keine Beschränkungen auf die Anzahl der Nachrichten, die Ihr Cmdlet schreiben kann, oder den Typ der Meldungen, die Ihr Cmdlet schreibt.</span><span class="sxs-lookup"><span data-stu-id="c5859-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="c5859-110">Jede Nachricht wird von einem bestimmten Aufruf von innerhalb der Eingabe Verarbeitungsmethode Ihres Cmdlets geschrieben.</span><span class="sxs-lookup"><span data-stu-id="c5859-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="c5859-111">Definieren das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c5859-111">Defining the Cmdlet</span></span>

<span data-ttu-id="c5859-112">Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren.</span><span class="sxs-lookup"><span data-stu-id="c5859-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c5859-113">Ein beliebiges Cmdlet kann die eingabeverarbeitungsmethoden benutzerbenachrichtigungen schreiben; Daher können im Allgemeinen Sie Namen mit diesem Cmdlet verwenden alle Verben, die welche systemmodifizierungen gibt an, das-Cmdlet führt.</span><span class="sxs-lookup"><span data-stu-id="c5859-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="c5859-114">Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c5859-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c5859-115">Die Stop-Proc-Cmdlet wurde entwickelt, das System ändern; aus diesem Grund die [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Deklaration für die .NET-Klasse muss enthalten der `SupportsShouldProcess` Attribut Schlüsselwort und festgelegt werden, `true`.</span><span class="sxs-lookup"><span data-stu-id="c5859-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="c5859-116">Der folgende Code ist die Definition für dieses Cmdlet Stop-Proc-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c5859-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="c5859-117">Weitere Informationen zu dieser Definition, finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="c5859-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="c5859-118">Definieren von Parametern für die System-Änderung</span><span class="sxs-lookup"><span data-stu-id="c5859-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="c5859-119">Das Cmdlet "Stop-Proc" definiert drei Parameter: `Name`, `Force`, und `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="c5859-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="c5859-120">Weitere Informationen zum Definieren von diesen Parametern finden Sie unter [ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="c5859-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="c5859-121">Hier ist die Parameterdeklaration für das Stop-Proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5859-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c5859-122">Überschreiben einer Eingabeverarbeitungsmethode</span><span class="sxs-lookup"><span data-stu-id="c5859-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c5859-123">Ihr Cmdlet ein eingabeverarbeitungsmethode muss überschrieben werden, am häufigsten wird [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="c5859-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="c5859-124">Dieses Cmdlet Stop-Proc überschreibt die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Geben Sie die Verarbeitungsmethode aus.</span><span class="sxs-lookup"><span data-stu-id="c5859-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="c5859-125">In dieser Implementierung des Stop-Proc-Cmdlets sind Aufrufe durchgeführt, um ausführliche Meldungen, Warnmeldungen und Debugmeldungen zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="c5859-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="c5859-126">Weitere Informationen, wie diese Methode ruft die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden finden Sie unter [Ein Cmdlets zu erstellen, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="c5859-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="c5859-127">Eine ausführliche Meldung schreiben</span><span class="sxs-lookup"><span data-stu-id="c5859-127">Writing a Verbose Message</span></span>

<span data-ttu-id="c5859-128">Die [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode wird verwendet, um allgemeine auf Benutzerebene Informationen zu schreiben, die unabhängig von bestimmten fehlerbedingungen ist.</span><span class="sxs-lookup"><span data-stu-id="c5859-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="c5859-129">Der Systemadministrator kann dann diese Informationen verwenden, und weiter verarbeitet, andere Befehle.</span><span class="sxs-lookup"><span data-stu-id="c5859-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="c5859-130">Darüber hinaus sollte alle Informationen geschrieben, mit dieser Methode lokalisiert werden, je nach Bedarf.</span><span class="sxs-lookup"><span data-stu-id="c5859-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="c5859-131">Der folgende Code aus diesem Stop-Proc-Cmdlet zeigt die beiden Aufrufe von der [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) die Überschreibung der Methode die [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="c5859-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="c5859-132">Schreiben Sie eine Debugmeldung</span><span class="sxs-lookup"><span data-stu-id="c5859-132">Writing a Debug Message</span></span>

<span data-ttu-id="c5859-133">Die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Methode wird verwendet, um Debugmeldungen zu schreiben, die verwendet werden kann, um den Vorgang des-Cmdlets beheben.</span><span class="sxs-lookup"><span data-stu-id="c5859-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="c5859-134">Der Aufruf von einem eingabeverarbeitungsmethode erfolgt.</span><span class="sxs-lookup"><span data-stu-id="c5859-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="c5859-135">Windows PowerShell definiert auch eine `Debug` Parameter, die stellt sowohl ausführliche Informationen zum Debuggen.</span><span class="sxs-lookup"><span data-stu-id="c5859-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="c5859-136">Wenn Ihr Cmdlet dieser Parameter unterstützt, muss es nicht rufen [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in den gleichen Code, aufruft [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="c5859-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="c5859-137">Die folgenden beiden Abschnitte des Codes aus dem Beispiel beenden-Proc-Cmdlet anzeigen, Aufrufe an die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) die Überschreibung der Methode die [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="c5859-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="c5859-138">Diese Debugmeldung wird unmittelbar vor geschrieben [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="c5859-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="c5859-139">Diese Debugmeldung wird unmittelbar vor geschrieben [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="c5859-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="c5859-140">Windows PowerShell automatisch alle weiterleitet [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Aufrufe an die Infrastruktur für ereignisablaufverfolgung und -Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c5859-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="c5859-141">Dadurch werden die Methodenaufrufe zum in der hostanwendung, einer Datei oder einen Debugger nachverfolgt werden, ohne dass zusätzliche Entwicklungsarbeiten in das-Cmdlet auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c5859-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="c5859-142">Die folgende Befehlszeile Eintrag implementiert einen Vorgang für die Ablaufverfolgung.</span><span class="sxs-lookup"><span data-stu-id="c5859-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="c5859-143">**PS > Trace-Ausdruck Stop-Proc-Datei proc.log-Befehl Beenden-Proc-Editor**</span><span class="sxs-lookup"><span data-stu-id="c5859-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="c5859-144">Schreiben Sie eine Warnung angezeigt</span><span class="sxs-lookup"><span data-stu-id="c5859-144">Writing a Warning Message</span></span>

<span data-ttu-id="c5859-145">Die [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) Methode dient zum Schreiben einer Warnung, wenn das Cmdlet einen Vorgang ausführen, die möglicherweise ein unerwartetes Ergebnis, z. B. das Überschreiben einer schreibgeschützten Datei ist.</span><span class="sxs-lookup"><span data-stu-id="c5859-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="c5859-146">Der folgende Code aus der Beispiel-Stop-Proc-Cmdlet wird der Aufruf der [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) die Überschreibung der Methode die [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="c5859-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="c5859-147">Schreiben Sie eine Statusmeldung</span><span class="sxs-lookup"><span data-stu-id="c5859-147">Writing a Progress Message</span></span>

<span data-ttu-id="c5859-148">Die [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) wird verwendet, um statusmeldungen zu schreiben, wenn der Cmdlet-Vorgänge für einige Zeit in Anspruch in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="c5859-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="c5859-149">Ein Aufruf von [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) übergibt eine [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) -Objekt, das an die hostanwendung für das Rendering für den Benutzer gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="c5859-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="c5859-150">Diese Stop-Proc-Cmdlet enthält keinen Aufruf der [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) Methode.</span><span class="sxs-lookup"><span data-stu-id="c5859-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="c5859-151">Der folgende Code ist ein Beispiel für eine Statusmeldung geschrieben, die von einem Cmdlet an, der versucht, ein Element zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="c5859-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="c5859-152">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="c5859-152">Code Sample</span></span>

<span data-ttu-id="c5859-153">Für die vollständige C# Beispielcode, finden Sie unter [StopProcessSample02 Beispiel](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c5859-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="c5859-154">Definieren von Objekttypen und Formatierung</span><span class="sxs-lookup"><span data-stu-id="c5859-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="c5859-155">Windows PowerShell übergibt Informationen zwischen Cmdlets, die mithilfe von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="c5859-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="c5859-156">Daher müssen möglicherweise ein Cmdlet seinen eigenen Typ definieren, oder das-Cmdlet zum Erweitern eines vorhandenen Typs, der durch ein anderes Cmdlet angegeben müssen.</span><span class="sxs-lookup"><span data-stu-id="c5859-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c5859-157">Weitere Informationen zum Definieren neuer Typen, oder erweitern vorhandene Typen finden Sie unter [Objekttypen erweitern und Formatierung](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="c5859-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c5859-158">Erstellen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c5859-158">Building the Cmdlet</span></span>

<span data-ttu-id="c5859-159">Nach der Implementierung eines Cmdlets, müssen sie über ein Windows PowerShell-Snap-in mit Windows PowerShell registriert werden.</span><span class="sxs-lookup"><span data-stu-id="c5859-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c5859-160">Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="c5859-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c5859-161">Testen das Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c5859-161">Testing the Cmdlet</span></span>

<span data-ttu-id="c5859-162">Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="c5859-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="c5859-163">Testen Sie nun das Beispiel beenden-Proc-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5859-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="c5859-164">Weitere Informationen zur Verwendung von Cmdlets, über die Befehlszeile finden Sie unter den [erste Schritte mit Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c5859-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="c5859-165">Die folgende Befehlszeile-Eintrag verwendet Stop-Proc Namen "NOTEPAD" Prozess beenden, geben ausführliche Benachrichtigungen und Drucken von Debuginformationen.</span><span class="sxs-lookup"><span data-stu-id="c5859-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="c5859-166">Die folgende Ausgabe wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c5859-166">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c5859-167">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c5859-167">See Also</span></span>

[<span data-ttu-id="c5859-168">Erstellen Sie ein Cmdlet, das das System geändert wird</span><span class="sxs-lookup"><span data-stu-id="c5859-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="c5859-169">Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c5859-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="c5859-170">[Erweitern die Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c5859-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="c5859-171">[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c5859-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="c5859-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c5859-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
