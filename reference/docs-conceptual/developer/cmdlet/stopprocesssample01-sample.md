---
title: StopProcessSample01-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bed607-369b-4507-87fa-f6011c2f1970
caps.latest.revision: 9
ms.openlocfilehash: 2ce146df05ef876d9c17f560628ebac2c39e57bf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365299"
---
# <a name="stopprocesssample01-sample"></a>StopProcessSample01-Beispiel

In diesem Beispiel wird gezeigt, wie ein Cmdlet geschrieben wird, das Feedback vom Benutzer anfordert, bevor es versucht, einen Prozess zu beenden, und wie ein `PassThru`-Parameter implementiert wird, der angibt, dass das Cmdlet ein Objekt zurückgeben soll. Dieses Cmdlet ähnelt dem Cmdlet "`Stop-Process`", das von Windows PowerShell 2,0 bereitgestellt wird.

### <a name="how-to-build-the-sample-by-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie mit installiertem Windows PowerShell 2,0 SDK zum Ordner StopProcessSample01. Der Standard Speicherort ist "c:\Programme (x86) \Microsoft SDKs\Windows\v7.0\samples\sysmgmt\windowspowershell\csharp\stopprocesssample01.".

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (. sln). Dadurch wird das Beispiel Projekt in Microsoft Visual Studio geöffnet.

3. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

    Die Bibliothek für das Beispiel wird im Standardordner \bin oder \bin\Debug erstellt.

### <a name="how-to-run-the-sample"></a>So führen Sie das Beispiel aus

1. Erstellen Sie den folgenden Modul Ordner:

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. Kopieren Sie die Beispielassembly in den Modul Ordner.

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl aus, um die Assembly in Windows PowerShell zu laden:

    `import-module stopprossessample01`

5. Führen Sie den folgenden Befehl aus, um das Cmdlet auszuführen:

    `stop-proc`

## <a name="requirements"></a>Anforderungen

Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Deutlich

In diesem Beispiel wird Folgendes veranschaulicht:

- Deklarieren einer Cmdlet-Klasse mithilfe des Cmdlet-Attributs.

- Deklarieren eines Cmdlet-Parameters mithilfe des Parameter-Attributs.

- Aufrufen der Methode "tiondprocess", um eine Bestätigung anzufordern.

- Implementieren eines `PassThru`-Parameters, der angibt, ob der Benutzer das Cmdlet zum Zurückgeben eines Objekts wünscht. Standardmäßig gibt dieses Cmdlet kein Objekt an die Pipeline zurück.

## <a name="example"></a>Beispiel

In diesem Beispiel wird gezeigt, wie ein `PassThru`-Parameter implementiert wird, der angibt, dass der Benutzer das Cmdlet zum Zurückgeben eines Objekts und das Anfordern von Benutzer Feedback durch Aufrufe der Methoden `ShouldProcess` und `ShouldContinue` benötigt.

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
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
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
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

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
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
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
