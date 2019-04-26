---
title: GetProcessSample02-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068078"
---
# <a name="getprocesssample02-sample"></a>GetProcessSample02-Beispiel

Dieses Beispiel zeigt, wie Sie ein Cmdlet schreiben, die die Prozesse auf dem lokalen Computer abruft. Es bietet eine `Name` Parameter, der verwendet werden kann, an die Prozesse abgerufen werden sollen. Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` Cmdlet von Windows PowerShell 2.0 bereitgestellt werden.

## <a name="how-to-build-the-sample-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie zu dem GetProcessSample02-Ordner, mit dem Windows PowerShell 2.0 SDK installiert. Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln). Daraufhin wird das Beispielprojekt in Visual Studio.

3. In der **erstellen** , wählen Sie im Menü **Projektmappe**.

    Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.

### <a name="how-to-run-the-sample"></a>Gewusst wie: Ausführen des Beispiels

1. Erstellen Sie die folgenden Ordner "Module":

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Kopieren Sie die Beispielassembly, auf den Ordner "Module".

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl zum Laden der Assembly in Windows PowerShell:

    `import-module getprossessample02`

5. Führen Sie den folgenden Befehl das Cmdlet ausführen:

    `get-proc`

## <a name="requirements"></a>Anforderungen

Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.

## <a name="demonstrates"></a>Zeigt

Dieses Beispiel veranschaulicht die folgenden.

- Deklarieren Sie eine Cmdlet-Klasse, die mit dem Cmdlet-Attribut.

- Deklarieren einen Cmdlet-Parameter, die mit dem Parameter-Attribut.

- Die Position des Parameters angeben.

- Deklarieren ein Validierungsattribut, für den Parameter eingeben.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine Implementierung der Get-Proc-Cmdlet, das umfasst eine `Name` Parameter.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

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
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
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
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
