---
title: Beispiel für Events01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057160"
---
# <a name="events01-sample"></a><span data-ttu-id="50b77-102">Events01-Beispiel</span><span class="sxs-lookup"><span data-stu-id="50b77-102">Events01 Sample</span></span>

<span data-ttu-id="50b77-103">Dieses Beispiel zeigt, wie Sie ein Cmdlet zu erstellen, die den Benutzer zum Registrieren für Ereignisse ermöglicht, die vom ausgelöst werden [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="50b77-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="50b77-104">Mit diesem Cmdlet können Benutzer eine Aktion, die ausgeführt werden, wenn eine Datei unter einem bestimmten Verzeichnis erstellt wird, registrieren.</span><span class="sxs-lookup"><span data-stu-id="50b77-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="50b77-105">In diesem Beispiel leitet sich von der [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="50b77-105">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="50b77-106">So erstellen Sie das Beispiel mithilfe von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50b77-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="50b77-107">Navigieren Sie zum Ordner Events01, mit dem Windows PowerShell 2.0 SDK installiert.</span><span class="sxs-lookup"><span data-stu-id="50b77-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="50b77-108">Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span><span class="sxs-lookup"><span data-stu-id="50b77-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="50b77-109">Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln).</span><span class="sxs-lookup"><span data-stu-id="50b77-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="50b77-110">Daraufhin wird das Beispielprojekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50b77-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="50b77-111">In der **erstellen** , wählen Sie im Menü **Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="50b77-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="50b77-112">Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="50b77-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="50b77-113">Gewusst wie: Ausführen des Beispiels</span><span class="sxs-lookup"><span data-stu-id="50b77-113">How to run the sample</span></span>

1. <span data-ttu-id="50b77-114">Erstellen Sie die folgenden Ordner "Module":</span><span class="sxs-lookup"><span data-stu-id="50b77-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="50b77-115">Kopieren Sie die Bibliotheksdatei für das Beispiel zum Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="50b77-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="50b77-116">Starten Sie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50b77-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="50b77-117">Führen Sie den folgenden Befehl aus, um das-Cmdlet in Windows PowerShell zu laden:</span><span class="sxs-lookup"><span data-stu-id="50b77-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="50b77-118">Verwenden Sie das Cmdlet "Register-FileSystemEvent", um einer Aktion registrieren, die eine Meldung schreibt, wenn eine Datei im TEMP-Verzeichnis erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="50b77-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="50b77-119">Erstellen Sie eine Datei im TEMP-Verzeichnis, und beachten Sie, dass die Aktion ausgeführt wird (die Nachricht wird angezeigt).</span><span class="sxs-lookup"><span data-stu-id="50b77-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="50b77-120">Dies ist eine Beispielausgabe, die sich ergibt, die folgenden Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="50b77-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="50b77-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="50b77-121">Requirements</span></span>

<span data-ttu-id="50b77-122">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="50b77-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="50b77-123">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="50b77-123">Demonstrates</span></span>

<span data-ttu-id="50b77-124">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="50b77-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="50b77-125">Wie Sie ein Cmdlet für die ereignisregistrierung zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="50b77-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="50b77-126">Das Cmdlet leitet sich von der [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) -Klasse, die Unterstützung für die gemeinsame Parameter von Register-bietet \* Event-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="50b77-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="50b77-127">Cmdlets, die abgeleitet sind [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) müssen Sie nur für die einzelnen Parameter definieren, und überschreiben die `GetSourceObject` und `GetSourceObjectEventName` abstrakte Methoden.</span><span class="sxs-lookup"><span data-stu-id="50b77-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="50b77-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="50b77-128">Example</span></span>

<span data-ttu-id="50b77-129">Dieses Beispiel zeigt, wie für die von ausgelösten Ereignisse registrieren [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="50b77-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="50b77-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50b77-130">See Also</span></span>

[<span data-ttu-id="50b77-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="50b77-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)