---
title: Beispiel für Runspace04 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 3cb370cd1bfe9ce7198980cc1c26fafb126d00a3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054899"
---
# <a name="runspace04-sample"></a><span data-ttu-id="4b4f0-102">Runspace04-Beispiel</span><span class="sxs-lookup"><span data-stu-id="4b4f0-102">Runspace04 Sample</span></span>

<span data-ttu-id="4b4f0-103">Dieses Beispiel zeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Klasse zum Ausführen von Befehlen, und wie Sie Fehler mit Abbruch abgefangen, die beim Ausführen der Befehle ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="4b4f0-104">Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="4b4f0-105">Daher werden keine Objekte zurückgegeben, und ein Fehler mit Abbruch wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b4f0-106">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4b4f0-106">Requirements</span></span>

<span data-ttu-id="4b4f0-107">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4b4f0-108">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="4b4f0-108">Demonstrates</span></span>

<span data-ttu-id="4b4f0-109">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="4b4f0-110">Erstellen einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="4b4f0-111">Hinzufügen von Befehlen der Pipeline die [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="4b4f0-112">Hinzufügen von Parameterargumente an die Pipeline aus.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="4b4f0-113">Die Befehle aufrufen synchron.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="4b4f0-114">Mithilfe von [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) zu extrahieren und Anzeigen von Eigenschaften aus den Objekten, die von den Befehlen zurückgegebenen Objekte.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="4b4f0-115">Abrufen und Anzeigen von Datensätzen, die während der Ausführung der Befehle generiert wurden.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="4b4f0-116">Abfangen und abschließende Ausnahmen von den Befehlen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="4b4f0-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4b4f0-117">Example</span></span>

<span data-ttu-id="4b4f0-118">In diesem Beispiel führt Befehle synchron, in dem standardmäßigen Runspace von Windows PowerShell bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="4b4f0-119">Mit dem letzte Befehl wird ein Abbruchfehler ausgegeben, da ein Parameterargument, das nicht gültig ist, die an den Befehl übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="4b4f0-120">Der Fehler mit Abbruch wird abgefangen und angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4b4f0-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="4b4f0-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4b4f0-121">See Also</span></span>

[<span data-ttu-id="4b4f0-122">Schreiben Sie eine Windows PowerShell-Hostanwendung</span><span class="sxs-lookup"><span data-stu-id="4b4f0-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)