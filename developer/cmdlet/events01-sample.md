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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068129"
---
# <a name="events01-sample"></a>Events01-Beispiel

Dieses Beispiel zeigt, wie Sie ein Cmdlet zu erstellen, die den Benutzer zum Registrieren für Ereignisse ermöglicht, die vom ausgelöst werden [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Mit diesem Cmdlet können Benutzer eine Aktion, die ausgeführt werden, wenn eine Datei unter einem bestimmten Verzeichnis erstellt wird, registrieren. In diesem Beispiel leitet sich von der [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) Basisklasse.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie zum Ordner Events01, mit dem Windows PowerShell 2.0 SDK installiert. Der standardmäßige Speicherort ist C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (.sln). Daraufhin wird das Beispielprojekt in Microsoft Visual Studio.

3. In der **erstellen** , wählen Sie im Menü **Projektmappe**.

    Die Bibliothek für das Beispiel wird in die Standardordner \bin oder \bin\debug erstellt werden.

### <a name="how-to-run-the-sample"></a>Gewusst wie: Ausführen des Beispiels

1. Erstellen Sie die folgenden Ordner "Module":

    `[user]/documents/windowspowershell/modules/events01`

2. Kopieren Sie die Bibliotheksdatei für das Beispiel zum Ordner "Module".

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl aus, um das-Cmdlet in Windows PowerShell zu laden:

    ```powershell
    import-module events01
    ```

5. Verwenden Sie das Cmdlet "Register-FileSystemEvent", um einer Aktion registrieren, die eine Meldung schreibt, wenn eine Datei im TEMP-Verzeichnis erstellt wird.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Erstellen Sie eine Datei im TEMP-Verzeichnis, und beachten Sie, dass die Aktion ausgeführt wird (die Nachricht wird angezeigt).

Dies ist eine Beispielausgabe, die sich ergibt, die folgenden Schritte aus.

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

Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.

## <a name="demonstrates"></a>Zeigt

Dieses Beispiel veranschaulicht die folgenden.

- Wie Sie ein Cmdlet für die ereignisregistrierung zu schreiben. Das Cmdlet leitet sich von der [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) -Klasse, die Unterstützung für die gemeinsame Parameter von Register-bietet * Event-Cmdlets. Cmdlets, die abgeleitet sind [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) müssen Sie nur für die einzelnen Parameter definieren, und überschreiben die `GetSourceObject` und `GetSourceObjectEventName` abstrakte Methoden.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie für die von ausgelösten Ereignisse registrieren [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).

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

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)