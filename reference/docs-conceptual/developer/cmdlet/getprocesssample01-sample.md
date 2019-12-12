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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369729"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="0a00d-102">GetProcessSample01-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0a00d-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="0a00d-103">In diesem Beispiel wird gezeigt, wie ein Cmdlet implementiert wird, das die Prozesse auf dem lokalen Computer abruft.</span><span class="sxs-lookup"><span data-stu-id="0a00d-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0a00d-104">Dieses Cmdlet ist eine vereinfachte Version des `Get-Process` Cmdlets, das von Windows PowerShell 2,0 bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0a00d-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="0a00d-105">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a00d-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="0a00d-106">Navigieren Sie mit installiertem Windows PowerShell 2,0 SDK zum Ordner GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="0a00d-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="0a00d-107">Der Standard Speicherort ist "c:\Programme (x86) \Microsoft SDKs\Windows\v7.0\samples\sysmgmt\windowspowershell\csharp\getprocesssample01.".</span><span class="sxs-lookup"><span data-stu-id="0a00d-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="0a00d-108">Doppelklicken Sie auf das Symbol für die Projektmappendatei (. sln).</span><span class="sxs-lookup"><span data-stu-id="0a00d-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="0a00d-109">Dadurch wird das Beispiel Projekt in Microsoft Visual Studio geöffnet.</span><span class="sxs-lookup"><span data-stu-id="0a00d-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="0a00d-110">Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="0a00d-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="0a00d-111">Die Bibliothek für das Beispiel wird im Standardordner \bin oder \bin\Debug erstellt.</span><span class="sxs-lookup"><span data-stu-id="0a00d-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="0a00d-112">Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="0a00d-112">How to run the sample</span></span>

1. <span data-ttu-id="0a00d-113">Öffnen Sie ein Eingabeaufforderungsfenster.</span><span class="sxs-lookup"><span data-stu-id="0a00d-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="0a00d-114">Navigieren Sie zu dem Verzeichnis, das die Datei "Sample. dll" enthält.</span><span class="sxs-lookup"><span data-stu-id="0a00d-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="0a00d-115">Führen Sie "installutil" GetProcessSample01. dll aus.</span><span class="sxs-lookup"><span data-stu-id="0a00d-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="0a00d-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a00d-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="0a00d-117">Führen Sie den folgenden Befehl aus, um das Snap-in zur Shell hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0a00d-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="0a00d-118">Geben Sie den folgenden Befehl ein, um das Cmdlet auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0a00d-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="0a00d-119">Dies ist eine Beispielausgabe, die sich aus den folgenden Schritten ergibt.</span><span class="sxs-lookup"><span data-stu-id="0a00d-119">This is a sample output that results from following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="0a00d-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0a00d-120">Requirements</span></span>

<span data-ttu-id="0a00d-121">Für dieses Beispiel ist Windows PowerShell 1,0 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0a00d-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0a00d-122">Gegenstand</span><span class="sxs-lookup"><span data-stu-id="0a00d-122">Demonstrates</span></span>

<span data-ttu-id="0a00d-123">In diesem Beispiel wird Folgendes veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="0a00d-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="0a00d-124">Erstellen eines einfachen-Beispiel-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0a00d-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="0a00d-125">Definieren einer Cmdlet-Klasse mithilfe des Cmdlet-Attributs.</span><span class="sxs-lookup"><span data-stu-id="0a00d-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="0a00d-126">Erstellen eines Snap-Ins, das sowohl mit Windows PowerShell 1,0 als auch mit Windows PowerShell 2,0 funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0a00d-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="0a00d-127">In den nachfolgenden Beispielen werden Module anstelle von Snap-Ins verwendet, damit Sie Windows PowerShell 2,0 benötigen.</span><span class="sxs-lookup"><span data-stu-id="0a00d-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="0a00d-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0a00d-128">Example</span></span>

<span data-ttu-id="0a00d-129">Dieses Beispiel zeigt, wie ein einfaches Cmdlet und sein Snap-in erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="0a00d-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0a00d-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0a00d-130">See Also</span></span>

[<span data-ttu-id="0a00d-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0a00d-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)