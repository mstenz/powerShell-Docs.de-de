---
title: Beispiel für GetProcessSample04 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861876"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04-Beispiel

Dieses Beispiel zeigt, wie Sie ein Cmdlet zu implementieren, die die Prozesse auf dem lokalen Computer abruft. Es generiert einen Fehler ohne Abbruch, wenn es sich bei Auftreten eines Fehlers beim Abrufen von einem Prozess. Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` Cmdlet von Windows PowerShell 2.0 bereitgestellt werden.

## <a name="how-to-build-the-sample-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie zum Ordner GetProcessSample04, mit dem Windows PowerShell 2.0 SDK installiert. Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln). Daraufhin wird das Beispielprojekt in Visual Studio.

3. In der **erstellen** , wählen Sie im Menü **Projektmappe**.

    Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.

### <a name="how-to-run-the-sample"></a>Gewusst wie: Ausführen des Beispiels

1. Erstellen Sie die folgenden Ordner "Module":

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Kopieren Sie die Beispielassembly, auf den Ordner "Module".

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl zum Laden der Assembly in Windows PowerShell:

    `Import-module getprossessample04`

5. Führen Sie den folgenden Befehl das Cmdlet ausführen:

    `get-proc`

## <a name="requirements"></a>Anforderungen

Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.

## <a name="demonstrates"></a>Veranschaulicht

Dieses Beispiel veranschaulicht die folgenden.

- Deklarieren Sie eine Cmdlet-Klasse, die mit dem Cmdlet-Attribut.

- Deklarieren einen Cmdlet-Parameter, die mit dem Parameter-Attribut.

- Die Position des Parameters angeben.

- Gibt an, dass der Parameter Eingaben über die Pipeline verwendet. Die Eingabe kann verwendet werden, anhand eines Objekts oder einen Wert aus einer Eigenschaft eines Objekts, dessen Eigenschaftenname den Namen des Parameters übereinstimmt.

- Deklarieren ein Validierungsattribut, für den Parameter eingeben.

- Einen Fehler ohne Abbruch abfangen und eine Fehlermeldung in den fehlerdatenstrom geschrieben.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie ein Cmdlet zu erstellen, die Fehler ohne Abbruch behandelt und Fehlermeldungen in den fehlerdatenstrom geschrieben wird.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
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
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
