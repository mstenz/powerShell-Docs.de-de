---
title: Schreiben eines einfachen Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365469"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="a9b07-102">Schreiben eines Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a9b07-102">How to write a cmdlet</span></span>

<span data-ttu-id="a9b07-103">In diesem Artikel wird gezeigt, wie Sie ein Cmdlet schreiben.</span><span class="sxs-lookup"><span data-stu-id="a9b07-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="a9b07-104">Das `Send-Greeting`-Cmdlet nimmt einen einzelnen Benutzernamen als Eingabe an und schreibt dann eine Begrüßung an diesen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a9b07-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="a9b07-105">Obwohl das Cmdlet nicht viel Arbeit leistet, veranschaulicht dieses Beispiel die Hauptabschnitte eines Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a9b07-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="a9b07-106">Schritte zum Schreiben eines Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a9b07-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="a9b07-107">Verwenden Sie das **Cmdlet** -Attribut, um die Klasse als Cmdlet zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="a9b07-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="a9b07-108">Das **Cmdlet** -Attribut gibt das Verb und das Substantiv für den Namen des Cmdlets an.</span><span class="sxs-lookup"><span data-stu-id="a9b07-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="a9b07-109">Weitere Informationen zum **Cmdlet** -Attribut finden Sie unter [CmdletAttribute-Deklaration](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a9b07-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="a9b07-110">Geben Sie den Namen der Klasse an.</span><span class="sxs-lookup"><span data-stu-id="a9b07-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="a9b07-111">Legen Sie fest, dass das Cmdlet von einer der folgenden Klassen abgeleitet ist:</span><span class="sxs-lookup"><span data-stu-id="a9b07-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="a9b07-112">System. Management. Automation. Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a9b07-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="a9b07-113">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="a9b07-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="a9b07-114">Um die Parameter für das Cmdlet zu definieren, verwenden Sie das **Parameter** Attribut.</span><span class="sxs-lookup"><span data-stu-id="a9b07-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="a9b07-115">In diesem Fall wird nur ein erforderlicher Parameter angegeben.</span><span class="sxs-lookup"><span data-stu-id="a9b07-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="a9b07-116">Weitere Informationen zum **Parameter** -Attribut finden Sie unter [Parameterattribute-Deklaration](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a9b07-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="a9b07-117">Überschreiben Sie die Eingabe Verarbeitungsmethode, die die Eingabe verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="a9b07-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="a9b07-118">In diesem Fall wird die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode überschrieben.</span><span class="sxs-lookup"><span data-stu-id="a9b07-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="a9b07-119">Um die Begrüßung zu schreiben, verwenden Sie die Methode [System. Management. Automation. Cmdlet. Write-Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="a9b07-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="a9b07-120">Die Begrüßung wird im folgenden Format angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a9b07-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="a9b07-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a9b07-121">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a9b07-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a9b07-122">See also</span></span>

[<span data-ttu-id="a9b07-123">System. Management. Automation. Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a9b07-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="a9b07-124">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="a9b07-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="a9b07-125">System. Management. Automation. Cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="a9b07-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="a9b07-126">System. Management. Automation. Cmdlet. Write Object</span><span class="sxs-lookup"><span data-stu-id="a9b07-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="a9b07-127">CmdletAttribute-Deklaration</span><span class="sxs-lookup"><span data-stu-id="a9b07-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="a9b07-128">ParameterAttribute-Deklaration</span><span class="sxs-lookup"><span data-stu-id="a9b07-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="a9b07-129">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a9b07-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)