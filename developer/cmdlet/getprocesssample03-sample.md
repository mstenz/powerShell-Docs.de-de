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
# <a name="getprocesssample03-sample"></a><span data-ttu-id="110e7-102">GetProcessSample03-Beispiel</span><span class="sxs-lookup"><span data-stu-id="110e7-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="110e7-103">Dieses Beispiel zeigt, wie Sie ein Cmdlet zu implementieren, die die Prozesse auf dem lokalen Computer abruft.</span><span class="sxs-lookup"><span data-stu-id="110e7-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="110e7-104">Es bietet eine `Name` Parameter, der ein Objekt aus der Pipeline oder einen Wert aus einer Eigenschaft eines Objekts, dessen Eigenschaftenname der Name des Parameters entspricht, annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="110e7-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="110e7-105">Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` Cmdlet von Windows PowerShell 2.0 bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="110e7-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="110e7-106">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="110e7-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="110e7-107">Navigieren Sie zum Ordner GetProcessSample03, mit dem Windows PowerShell 2.0 SDK installiert.</span><span class="sxs-lookup"><span data-stu-id="110e7-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="110e7-108">Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="110e7-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="110e7-109">Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln).</span><span class="sxs-lookup"><span data-stu-id="110e7-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="110e7-110">Daraufhin wird das Beispielprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="110e7-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="110e7-111">In der **erstellen** , wählen Sie im Menü **Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="110e7-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="110e7-112">Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="110e7-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="110e7-113">Gewusst wie: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="110e7-113">How to run the sample</span></span>

1. <span data-ttu-id="110e7-114">Erstellen Sie die folgenden Ordner "Module":</span><span class="sxs-lookup"><span data-stu-id="110e7-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="110e7-115">Kopieren Sie die Beispielassembly, auf den Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="110e7-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="110e7-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="110e7-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="110e7-117">Führen Sie den folgenden Befehl zum Laden der Assembly in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="110e7-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="110e7-118">Führen Sie den folgenden Befehl das Cmdlet ausführen:</span><span class="sxs-lookup"><span data-stu-id="110e7-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="110e7-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="110e7-119">Requirements</span></span>

<span data-ttu-id="110e7-120">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="110e7-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="110e7-121">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="110e7-121">Demonstrates</span></span>

<span data-ttu-id="110e7-122">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="110e7-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="110e7-123">Deklarieren Sie eine Cmdlet-Klasse, die mit dem Cmdlet-Attribut.</span><span class="sxs-lookup"><span data-stu-id="110e7-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="110e7-124">Deklarieren einen Cmdlet-Parameter, die mit dem Parameter-Attribut.</span><span class="sxs-lookup"><span data-stu-id="110e7-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="110e7-125">Die Position des Parameters angeben.</span><span class="sxs-lookup"><span data-stu-id="110e7-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="110e7-126">Gibt an, dass der Parameter Eingaben über die Pipeline verwendet.</span><span class="sxs-lookup"><span data-stu-id="110e7-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="110e7-127">Die Eingabe kann verwendet werden, anhand eines Objekts oder einen Wert aus einer Eigenschaft eines Objekts, dessen Eigenschaftenname den Namen des Parameters übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="110e7-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="110e7-128">Deklarieren ein Validierungsattribut, für den Parameter eingeben.</span><span class="sxs-lookup"><span data-stu-id="110e7-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="110e7-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="110e7-129">Example</span></span>

<span data-ttu-id="110e7-130">Dieses Beispiel zeigt eine Implementierung der Get-Proc-Cmdlet, das umfasst eine `Name` Parameter, die Eingaben aus der Pipeline akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="110e7-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="110e7-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="110e7-131">See Also</span></span>

[<span data-ttu-id="110e7-132">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="110e7-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
