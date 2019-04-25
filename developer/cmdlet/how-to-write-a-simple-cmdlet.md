---
title: Wie Sie ein einfaches Cmdlet schreiben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067738"
---
# <a name="how-to-write-a-cmdlet"></a>Wie Sie ein Cmdlet schreiben

In diesem Artikel wird gezeigt, wie ein Cmdlet schreiben. Die `Send-Greeting` Cmdlet nimmt einen einzelnen Benutzernamen als Eingabe und schreibt dann eine Begrüßung für diesen Benutzer. Obwohl das-Cmdlet nicht viel Arbeit ausgeführt wird, in diesem Beispiel die Hauptabschnitte eines Cmdlets veranschaulicht.

## <a name="steps-to-write-a-cmdlet"></a>Schritte zum Schreiben von einem cmdlet

1. Um die Klasse als ein Cmdlet zu deklarieren, verwenden die **Cmdlet** Attribut. Die **Cmdlet** Attribut gibt an, die Verb- und die für die Cmdlet-Namen.

   Weitere Informationen zu den **Cmdlet** Attribut, finden Sie unter [CmdletAttribute-Deklaration](cmdlet-attribute-declaration.md).

2. Geben Sie den Namen der Klasse.

3. Geben Sie, dass das Cmdlet von einem der folgenden Klassen abgeleitet wird:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Verwenden Sie zum Definieren der Parameter für das Cmdlet die **Parameter** Attribut. In diesem Fall erforderlichen nur eine Parameter angegeben wird.

   Weitere Informationen zu den **Parameter** Attribut, finden Sie unter [ParameterAttribute Deklaration](parameter-attribute-declaration.md).

5. Überschreiben Sie die Eingabe, die Verarbeitungsmethode aus, die die Eingabe verarbeitet. In diesem Fall die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode überschrieben wird.

6. Um die Begrüßung schreiben möchten, verwenden Sie die Methode [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   Die Begrüßung wird im folgenden Format angezeigt:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Beispiel

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

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

## <a name="see-also"></a>Siehe auch

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute-Deklaration](cmdlet-attribute-declaration.md)

[ParameterAttribute-Deklaration](parameter-attribute-declaration.md)

[Schreiben eines Windows PowerShell-Cmdlets](writing-a-windows-powershell-cmdlet.md)