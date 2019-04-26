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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068027"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="27810-102">GetProcessSample04-Beispiel</span><span class="sxs-lookup"><span data-stu-id="27810-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="27810-103">Dieses Beispiel zeigt, wie Sie ein Cmdlet zu implementieren, die die Prozesse auf dem lokalen Computer abruft.</span><span class="sxs-lookup"><span data-stu-id="27810-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="27810-104">Es generiert einen Fehler ohne Abbruch, wenn es sich bei Auftreten eines Fehlers beim Abrufen von einem Prozess.</span><span class="sxs-lookup"><span data-stu-id="27810-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="27810-105">Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` Cmdlet von Windows PowerShell 2.0 bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="27810-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="27810-106">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27810-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="27810-107">Navigieren Sie zum Ordner GetProcessSample04, mit dem Windows PowerShell 2.0 SDK installiert.</span><span class="sxs-lookup"><span data-stu-id="27810-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="27810-108">Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="27810-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="27810-109">Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln).</span><span class="sxs-lookup"><span data-stu-id="27810-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="27810-110">Daraufhin wird das Beispielprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="27810-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="27810-111">In der **erstellen** , wählen Sie im Menü **Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="27810-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="27810-112">Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="27810-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="27810-113">Gewusst wie: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="27810-113">How to run the sample</span></span>

1. <span data-ttu-id="27810-114">Erstellen Sie die folgenden Ordner "Module":</span><span class="sxs-lookup"><span data-stu-id="27810-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="27810-115">Kopieren Sie die Beispielassembly, auf den Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="27810-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="27810-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27810-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="27810-117">Führen Sie den folgenden Befehl zum Laden der Assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="27810-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="27810-118">Führen Sie den folgenden Befehl das Cmdlet ausführen:</span><span class="sxs-lookup"><span data-stu-id="27810-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="27810-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="27810-119">Requirements</span></span>

<span data-ttu-id="27810-120">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="27810-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="27810-121">Zeigt</span><span class="sxs-lookup"><span data-stu-id="27810-121">Demonstrates</span></span>

<span data-ttu-id="27810-122">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="27810-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="27810-123">Deklarieren Sie eine Cmdlet-Klasse, die mit dem Cmdlet-Attribut.</span><span class="sxs-lookup"><span data-stu-id="27810-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="27810-124">Deklarieren einen Cmdlet-Parameter, die mit dem Parameter-Attribut.</span><span class="sxs-lookup"><span data-stu-id="27810-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="27810-125">Die Position des Parameters angeben.</span><span class="sxs-lookup"><span data-stu-id="27810-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="27810-126">Gibt an, dass der Parameter Eingaben über die Pipeline verwendet.</span><span class="sxs-lookup"><span data-stu-id="27810-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="27810-127">Die Eingabe kann verwendet werden, anhand eines Objekts oder einen Wert aus einer Eigenschaft eines Objekts, dessen Eigenschaftenname den Namen des Parameters übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="27810-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="27810-128">Deklarieren ein Validierungsattribut, für den Parameter eingeben.</span><span class="sxs-lookup"><span data-stu-id="27810-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="27810-129">Einen Fehler ohne Abbruch abfangen und eine Fehlermeldung in den fehlerdatenstrom geschrieben.</span><span class="sxs-lookup"><span data-stu-id="27810-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="27810-130">Beispiel</span><span class="sxs-lookup"><span data-stu-id="27810-130">Example</span></span>

<span data-ttu-id="27810-131">Dieses Beispiel zeigt, wie Sie ein Cmdlet zu erstellen, die Fehler ohne Abbruch behandelt und Fehlermeldungen in den fehlerdatenstrom geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="27810-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="27810-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="27810-132">See Also</span></span>

[<span data-ttu-id="27810-133">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="27810-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
