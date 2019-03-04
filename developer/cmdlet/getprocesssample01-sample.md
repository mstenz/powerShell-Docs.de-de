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
# <a name="getprocesssample01-sample"></a><span data-ttu-id="177e3-102">GetProcessSample01-Beispiel</span><span class="sxs-lookup"><span data-stu-id="177e3-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="177e3-103">Dieses Beispiel zeigt, wie Sie ein Cmdlet zu implementieren, die die Prozesse auf dem lokalen Computer abruft.</span><span class="sxs-lookup"><span data-stu-id="177e3-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="177e3-104">Dieses Cmdlet ist eine vereinfachte Version der `Get-Process` -Cmdlet, das von Windows PowerShell 2.0 bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="177e3-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="177e3-105">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="177e3-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="177e3-106">Navigieren Sie zu dem GetProcessSample01-Ordner, mit dem Windows PowerShell 2.0 SDK installiert.</span><span class="sxs-lookup"><span data-stu-id="177e3-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="177e3-107">Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="177e3-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="177e3-108">Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln).</span><span class="sxs-lookup"><span data-stu-id="177e3-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="177e3-109">Daraufhin wird das Beispielprojekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="177e3-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="177e3-110">In der **erstellen** , wählen Sie im Menü **Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="177e3-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="177e3-111">Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="177e3-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="177e3-112">Gewusst wie: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="177e3-112">How to run the sample</span></span>

1. <span data-ttu-id="177e3-113">Öffnen Sie ein Eingabeaufforderungsfenster.</span><span class="sxs-lookup"><span data-stu-id="177e3-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="177e3-114">Navigieren Sie zu dem Verzeichnis, die die Beispiel-DLL-Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="177e3-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="177e3-115">Führen Sie Installutil "GetProcessSample01.dll".</span><span class="sxs-lookup"><span data-stu-id="177e3-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="177e3-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="177e3-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="177e3-117">Führen Sie den folgenden Befehl an die Shell das Snap-in hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="177e3-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="177e3-118">Geben Sie den folgenden Befehl zum Ausführen des Cmdlets ein.</span><span class="sxs-lookup"><span data-stu-id="177e3-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="177e3-119">Dies ist eine Beispielausgabe, die aus folgenden Schritten.</span><span class="sxs-lookup"><span data-stu-id="177e3-119">This is a sample output that results from following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="177e3-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="177e3-120">Requirements</span></span>

<span data-ttu-id="177e3-121">Dieses Beispiel ist die Windows PowerShell 1.0 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="177e3-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="177e3-122">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="177e3-122">Demonstrates</span></span>

<span data-ttu-id="177e3-123">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="177e3-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="177e3-124">Erstellen ein einfaches Beispiel-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="177e3-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="177e3-125">Definieren eine Cmdlet-Klasse, mit dem Cmdlet-Attribut.</span><span class="sxs-lookup"><span data-stu-id="177e3-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="177e3-126">Erstellen eines Snap-Ins, die mit Windows PowerShell 1.0 und Windows PowerShell 2.0 funktioniert.</span><span class="sxs-lookup"><span data-stu-id="177e3-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="177e3-127">Nachfolgende Beispiele verwenden Module statt-Snap-ins, damit sie Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="177e3-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="177e3-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="177e3-128">Example</span></span>

<span data-ttu-id="177e3-129">Dieses Beispiel zeigt, wie Sie ein einfaches Cmdlet und die-Snap-in erstellen.</span><span class="sxs-lookup"><span data-stu-id="177e3-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="177e3-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="177e3-130">See Also</span></span>

[<span data-ttu-id="177e3-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="177e3-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)