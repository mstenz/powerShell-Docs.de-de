---
title: GetProcessSample04-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365709"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04-Beispiel

In diesem Beispiel wird gezeigt, wie ein Cmdlet implementiert wird, das die Prozesse auf dem lokalen Computer abruft. Wenn beim Abrufen eines Prozesses ein Fehler auftritt, wird ein Fehler vom Typ "nicht abgebrochen" generiert. Dieses Cmdlet ist eine vereinfachte Version des Cmdlets "`Get-Process`", das von Windows PowerShell 2,0 bereitgestellt wird.

## <a name="how-to-build-the-sample-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie mit installiertem Windows PowerShell 2,0 SDK zum Ordner GetProcessSample04. Der Standard Speicherort ist "c:\Programme (x86) \Microsoft SDKs\Windows\v7.0\samples\sysmgmt\windowspowershell\csharp\getprocesssample04.".

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (. sln). Dadurch wird das Beispiel Projekt in Visual Studio geöffnet.

3. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

    Die Bibliothek für das Beispiel wird im Standardordner \bin oder \bin\Debug erstellt.

### <a name="how-to-run-the-sample"></a>So führen Sie das Beispiel aus

1. Erstellen Sie den folgenden Modul Ordner:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Kopieren Sie die Beispielassembly in den Modul Ordner.

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl aus, um die Assembly in Windows PowerShell zu laden:

    `Import-module getprossessample04`

5. Führen Sie den folgenden Befehl aus, um das Cmdlet auszuführen:

    `get-proc`

## <a name="requirements"></a>Anforderungen

Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Deutlich

In diesem Beispiel wird Folgendes veranschaulicht:

- Deklarieren einer Cmdlet-Klasse mithilfe des Cmdlet-Attributs.

- Deklarieren eines Cmdlet-Parameters mithilfe des Parameter-Attributs.

- Angeben der Position des Parameters.

- Angeben, dass der Parameter Eingaben aus der Pipeline annimmt. Die Eingabe kann aus einem Objekt oder einem Wert aus einer Eigenschaft eines Objekts entnommen werden, dessen Eigenschaftsname mit dem Parameternamen identisch ist.

- Deklarieren eines Validierungs Attributs für die Parameter Eingabe.

- Das Abfangen eines Fehlers ohne Abbruch und das Schreiben einer Fehlermeldung in den Fehler Datenstrom.

## <a name="example"></a>Beispiel

In diesem Beispiel wird gezeigt, wie ein Cmdlet erstellt wird, das nicht abschließende Fehler behandelt und Fehlermeldungen in den Fehler Datenstrom schreibt.

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
