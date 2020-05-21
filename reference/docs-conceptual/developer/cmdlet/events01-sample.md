---
title: Events01-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 772f73793449856651ab6b03e1ccc14faed941fc
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561446"
---
# <a name="events01-sample"></a><span data-ttu-id="fb8a4-102">Events01-Beispiel</span><span class="sxs-lookup"><span data-stu-id="fb8a4-102">Events01 Sample</span></span>

<span data-ttu-id="fb8a4-103">In diesem Beispiel wird gezeigt, wie ein Cmdlet erstellt wird, das es dem Benutzer ermöglicht, sich für Ereignisse zu registrieren, die von [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="fb8a4-104">Mit diesem Cmdlet können Benutzer eine Aktion registrieren, die ausgeführt wird, wenn eine Datei unter einem bestimmten Verzeichnis erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="fb8a4-105">Dieses Beispiel wird von der [Microsoft. PowerShell. Commands. objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) -Basisklasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="fb8a4-106">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="fb8a4-107">Navigieren Sie mit installiertem Windows PowerShell 2,0 SDK zum Ordner Events01.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="fb8a4-108">Der Standardspeicherort ist `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="fb8a4-109">Doppelklicken Sie auf das Symbol für die Projektmappendatei (. sln).</span><span class="sxs-lookup"><span data-stu-id="fb8a4-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="fb8a4-110">Dadurch wird das Beispiel Projekt in Microsoft Visual Studio geöffnet.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="fb8a4-111">Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="fb8a4-112">Die Bibliothek für das Beispiel wird in den Standard- `\bin` oder- `\bin\debug` Ordnern erstellt.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="fb8a4-113">Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="fb8a4-113">How to run the sample</span></span>

1. <span data-ttu-id="fb8a4-114">Erstellen Sie den folgenden Modul Ordner:</span><span class="sxs-lookup"><span data-stu-id="fb8a4-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="fb8a4-115">Kopieren Sie die Bibliotheksdatei für das Beispiel in den Modul Ordner.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="fb8a4-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="fb8a4-117">Führen Sie den folgenden Befehl aus, um das Cmdlet in Windows PowerShell zu laden:</span><span class="sxs-lookup"><span data-stu-id="fb8a4-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="fb8a4-118">Verwenden Sie das Register-FileSystemEvent-Cmdlet, um eine Aktion zu registrieren, die eine Meldung schreibt, wenn eine Datei unter dem Verzeichnis "Temp" erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="fb8a4-119">Erstellen Sie eine Datei im Verzeichnis "Temp", und beachten Sie, dass die Aktion ausgeführt wird (die Meldung wird angezeigt).</span><span class="sxs-lookup"><span data-stu-id="fb8a4-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="fb8a4-120">Dies ist eine Beispielausgabe, die ergibt, indem Sie die folgenden Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="fb8a4-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="fb8a4-121">Requirements</span></span>

<span data-ttu-id="fb8a4-122">Dieses Beispiel erfordert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fb8a4-123">Zeigt</span><span class="sxs-lookup"><span data-stu-id="fb8a4-123">Demonstrates</span></span>

<span data-ttu-id="fb8a4-124">In diesem Beispiel wird Folgendes veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="fb8a4-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="fb8a4-125">Schreiben eines Cmdlets für die Ereignis Registrierung</span><span class="sxs-lookup"><span data-stu-id="fb8a4-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="fb8a4-126">Das-Cmdlet wird von der [Microsoft. PowerShell. Commands. objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) -Klasse abgeleitet, die Unterstützung für Parameter bereitstellt, die von den `Register-*Event` Cmdlets gemeinsam sind.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="fb8a4-127">Cmdlets, die von [Microsoft. PowerShell. Commands. objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) abgeleitet werden, müssen nur die jeweiligen Parameter definieren und die `GetSourceObject` abstrakten Methoden und überschreiben `GetSourceObjectEventName` .</span><span class="sxs-lookup"><span data-stu-id="fb8a4-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="fb8a4-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fb8a4-128">Example</span></span>

<span data-ttu-id="fb8a4-129">Dieses Beispiel zeigt, wie Sie sich für Ereignisse registrieren, die von [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="fb8a4-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="fb8a4-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fb8a4-130">See Also</span></span>

[<span data-ttu-id="fb8a4-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fb8a4-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
