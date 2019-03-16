---
title: Wie Sie ein Cmdlet in einem Cmdlet aufrufen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055902"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Aufrufen eines Cmdlet in einem Cmdlet

Dieses Beispiel zeigt, wie Sie ein Cmdlet in ein anderes Cmdlet aufrufen, können Sie die Funktionalität des aufgerufenen-Cmdlets zum Cmdlet hinzugefügt, die Sie entwickeln. In diesem Beispiel die `Get-Process` Cmdlet wird aufgerufen, um die Prozesse abzurufen, die auf dem lokalen Computer ausgeführt werden. Der Aufruf der `Get-Process` Cmdlet entspricht den folgenden Befehl aus. Dieser Befehl ruft alle Prozesse, deren Namen mit den Zeichen "a" bis "t" beginnen.

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> Sie können nur die Cmdlets, die direkt vom abgeleitet sind Aufrufen der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse. Sie können nicht aufgerufen werden ein Cmdlet, das von abgeleitet ist die [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse.

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a>Um ein Cmdlet in einem Cmdlet aufzurufen.

1. Stellen Sie sicher, dass die Assembly, definiert das-Cmdlet aufgerufen werden, verwiesen wird und dass die entsprechenden `using` -Anweisung wird hinzugefügt. In diesem Beispiel werden die folgenden Namespaces hinzugefügt.

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. Erstellen Sie eine neue Instanz des-Cmdlets aufgerufen werden, in der Eingabe Verarbeitungsmethode des-Cmdlets. In diesem Beispiel ist ein Objekt des Typs [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) wird erstellt, zusammen mit der Zeichenfolge, die die Argumente enthält, die verwendet werden, wenn das-Cmdlet aufgerufen wird.

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. Rufen Sie die [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) aufzurufende Methode der `Get-Process` Cmdlet.

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a>Beispiel

In diesem Beispiel die `Get-Process` Cmdlet wird aufgerufen, innerhalb der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode eines Cmdlets.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
