---
title: Beispiel mit GetProcessSample03 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856476"
---
# <a name="getprocesssample03-sample"></a>GetProcessSample03-Beispiel

Dieses Beispiel zeigt, wie Sie ein Cmdlet zu implementieren, die die Prozesse auf dem lokalen Computer abruft. Es bietet eine `Name` Parameter, der ein Objekt aus der Pipeline oder einen Wert aus einer Eigenschaft eines Objekts, dessen Eigenschaftenname der Name des Parameters entspricht, annehmen kann. Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` Cmdlet von Windows PowerShell 2.0 bereitgestellt werden.

## <a name="how-to-build-the-sample-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie zum Ordner GetProcessSample03, mit dem Windows PowerShell 2.0 SDK installiert. Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln). Daraufhin wird das Beispielprojekt in Visual Studio.

3. In der **erstellen** , wählen Sie im Menü **Projektmappe**.

    Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.

### <a name="how-to-run-the-sample"></a>Gewusst wie: Ausführen des Beispiels

1. Erstellen Sie die folgenden Ordner "Module":

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. Kopieren Sie die Beispielassembly, auf den Ordner "Module".

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl zum Laden der Assembly in Windows PowerShell:

    `Import-module getprossessample03`

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

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine Implementierung der Get-Proc-Cmdlet, das umfasst eine `Name` Parameter, die Eingaben aus der Pipeline akzeptiert.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
