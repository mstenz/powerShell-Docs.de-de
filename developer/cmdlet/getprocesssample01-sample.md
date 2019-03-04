---
title: GetProcessSample01-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859836"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01-Beispiel

Dieses Beispiel zeigt, wie Sie ein Cmdlet zu implementieren, die die Prozesse auf dem lokalen Computer abruft. Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` -Cmdlet, das von Windows PowerShell 2.0 bereitgestellt wird.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie zu dem GetProcessSample01-Ordner, mit dem Windows PowerShell 2.0 SDK installiert. Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln). Daraufhin wird das Beispielprojekt in Microsoft Visual Studio.

3. In der **erstellen** , wählen Sie im Menü **Projektmappe**.

  Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.

### <a name="how-to-run-the-sample"></a>Gewusst wie: Ausführen des Beispiels

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Navigieren Sie zu dem Verzeichnis, die die Beispiel-DLL-Datei enthält.

3. Führen Sie Installutil "GetProcessSample01.dll".

4. Starten Sie Windows PowerShell.

5. Führen Sie den folgenden Befehl an die Shell das Snap-in hinzufügen.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Geben Sie den folgenden Befehl zum Ausführen des Cmdlets ein. `get-proc`

   `get-proc`

   Dies ist eine Beispielausgabe, die aus folgenden Schritten.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Anforderungen

Dieses Beispiel ist die Windows PowerShell 1.0 oder höher erforderlich.

## <a name="demonstrates"></a>Veranschaulicht

Dieses Beispiel veranschaulicht die folgenden.

- Erstellen ein einfaches Beispiel-Cmdlet.

- Definieren eine Cmdlet-Klasse, mit dem Cmdlet-Attribut.

- Erstellen eines Snap-Ins, die mit Windows PowerShell 1.0 und Windows PowerShell 2.0 funktioniert. Nachfolgende Beispiele verwenden Module statt-Snap-ins, damit sie Windows PowerShell 2.0 erforderlich.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie ein einfaches Cmdlet und die-Snap-in erstellen.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)