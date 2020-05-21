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
# <a name="events01-sample"></a>Events01-Beispiel

In diesem Beispiel wird gezeigt, wie ein Cmdlet erstellt wird, das es dem Benutzer ermöglicht, sich für Ereignisse zu registrieren, die von [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)ausgelöst werden.
Mit diesem Cmdlet können Benutzer eine Aktion registrieren, die ausgeführt wird, wenn eine Datei unter einem bestimmten Verzeichnis erstellt wird.
Dieses Beispiel wird von der [Microsoft. PowerShell. Commands. objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) -Basisklasse abgeleitet.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>So erstellen Sie das Beispiel mithilfe von Visual Studio.

1. Navigieren Sie mit installiertem Windows PowerShell 2,0 SDK zum Ordner Events01.
   Der Standardspeicherort ist `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Doppelklicken Sie auf das Symbol für die Projektmappendatei (. sln).
   Dadurch wird das Beispiel Projekt in Microsoft Visual Studio geöffnet.

3. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.
   Die Bibliothek für das Beispiel wird in den Standard- `\bin` oder- `\bin\debug` Ordnern erstellt.

### <a name="how-to-run-the-sample"></a>Ausführen des Beispiels

1. Erstellen Sie den folgenden Modul Ordner:

    `[user]/documents/windowspowershell/modules/events01`

2. Kopieren Sie die Bibliotheksdatei für das Beispiel in den Modul Ordner.

3. Starten Sie Windows PowerShell.

4. Führen Sie den folgenden Befehl aus, um das Cmdlet in Windows PowerShell zu laden:

    ```powershell
    import-module events01
    ```

5. Verwenden Sie das Register-FileSystemEvent-Cmdlet, um eine Aktion zu registrieren, die eine Meldung schreibt, wenn eine Datei unter dem Verzeichnis "Temp" erstellt wird.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Erstellen Sie eine Datei im Verzeichnis "Temp", und beachten Sie, dass die Aktion ausgeführt wird (die Meldung wird angezeigt).

Dies ist eine Beispielausgabe, die ergibt, indem Sie die folgenden Schritte ausführen.

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

Dieses Beispiel erfordert Windows PowerShell 2,0.

## <a name="demonstrates"></a>Zeigt

In diesem Beispiel wird Folgendes veranschaulicht:

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Schreiben eines Cmdlets für die Ereignis Registrierung

Das-Cmdlet wird von der [Microsoft. PowerShell. Commands. objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) -Klasse abgeleitet, die Unterstützung für Parameter bereitstellt, die von den `Register-*Event` Cmdlets gemeinsam sind.
Cmdlets, die von [Microsoft. PowerShell. Commands. objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) abgeleitet werden, müssen nur die jeweiligen Parameter definieren und die `GetSourceObject` abstrakten Methoden und überschreiben `GetSourceObjectEventName` .

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie sich für Ereignisse registrieren, die von [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher)ausgelöst werden.

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

[Schreiben eines Windows PowerShell-Cmdlets](writing-a-windows-powershell-cmdlet.md)
