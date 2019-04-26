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
# <a name="getprocesssample02-sample"></a><span data-ttu-id="59a3a-102">GetProcessSample02-Beispiel</span><span class="sxs-lookup"><span data-stu-id="59a3a-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="59a3a-103">Dieses Beispiel zeigt, wie Sie ein Cmdlet schreiben, die die Prozesse auf dem lokalen Computer abruft.</span><span class="sxs-lookup"><span data-stu-id="59a3a-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="59a3a-104">Es bietet eine `Name` Parameter, der verwendet werden kann, an die Prozesse abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="59a3a-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="59a3a-105">Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` Cmdlet von Windows PowerShell 2.0 bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="59a3a-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="59a3a-106">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59a3a-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="59a3a-107">Navigieren Sie zu dem GetProcessSample02-Ordner, mit dem Windows PowerShell 2.0 SDK installiert.</span><span class="sxs-lookup"><span data-stu-id="59a3a-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="59a3a-108">Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="59a3a-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="59a3a-109">Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln).</span><span class="sxs-lookup"><span data-stu-id="59a3a-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="59a3a-110">Daraufhin wird das Beispielprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59a3a-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="59a3a-111">In der **erstellen** , wählen Sie im Menü **Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="59a3a-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="59a3a-112">Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="59a3a-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="59a3a-113">Gewusst wie: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="59a3a-113">How to run the sample</span></span>

1. <span data-ttu-id="59a3a-114">Erstellen Sie die folgenden Ordner "Module":</span><span class="sxs-lookup"><span data-stu-id="59a3a-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="59a3a-115">Kopieren Sie die Beispielassembly, auf den Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="59a3a-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="59a3a-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59a3a-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="59a3a-117">Führen Sie den folgenden Befehl zum Laden der Assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="59a3a-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="59a3a-118">Führen Sie den folgenden Befehl das Cmdlet ausführen:</span><span class="sxs-lookup"><span data-stu-id="59a3a-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="59a3a-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="59a3a-119">Requirements</span></span>

<span data-ttu-id="59a3a-120">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="59a3a-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="59a3a-121">Zeigt</span><span class="sxs-lookup"><span data-stu-id="59a3a-121">Demonstrates</span></span>

<span data-ttu-id="59a3a-122">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="59a3a-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="59a3a-123">Deklarieren Sie eine Cmdlet-Klasse, die mit dem Cmdlet-Attribut.</span><span class="sxs-lookup"><span data-stu-id="59a3a-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="59a3a-124">Deklarieren einen Cmdlet-Parameter, die mit dem Parameter-Attribut.</span><span class="sxs-lookup"><span data-stu-id="59a3a-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="59a3a-125">Die Position des Parameters angeben.</span><span class="sxs-lookup"><span data-stu-id="59a3a-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="59a3a-126">Deklarieren ein Validierungsattribut, für den Parameter eingeben.</span><span class="sxs-lookup"><span data-stu-id="59a3a-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="59a3a-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="59a3a-127">Example</span></span>

<span data-ttu-id="59a3a-128">Dieses Beispiel zeigt eine Implementierung der Get-Proc-Cmdlet, das umfasst eine `Name` Parameter.</span><span class="sxs-lookup"><span data-stu-id="59a3a-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="59a3a-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="59a3a-129">See Also</span></span>

[<span data-ttu-id="59a3a-130">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="59a3a-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
