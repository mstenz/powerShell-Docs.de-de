---
title: 'Gewusst wie: Deklarieren von dynamischen Parametern | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067919"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="05cbd-102">Deklarieren von dynamischen Parametern</span><span class="sxs-lookup"><span data-stu-id="05cbd-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="05cbd-103">Dieses Beispiel zeigt, wie Sie dynamische Parameter definieren, die an das Cmdlet zur Laufzeit hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="05cbd-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="05cbd-104">In diesem Beispiel die `Department` Parameter wird an das Cmdlet hinzugefügt, wenn der Benutzer gibt die `Employee` switch-Parameter.</span><span class="sxs-lookup"><span data-stu-id="05cbd-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="05cbd-105">Weitere Informationen zu dynamischen Parametern finden Sie unter [dynamische Cmdletparameter](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="05cbd-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="05cbd-106">Um dynamische Parameter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="05cbd-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="05cbd-107">Fügen Sie in der Cmdlet-Klassendeklaration, die [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) -Schnittstelle wie gezeigt.</span><span class="sxs-lookup"><span data-stu-id="05cbd-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="05cbd-108">Rufen Sie die [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) Methode, die das Objekt zurückgibt, die dynamischen Parameter definiert sind.</span><span class="sxs-lookup"><span data-stu-id="05cbd-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="05cbd-109">In diesem Beispiel ist die Methode wird aufgerufen, wenn die `Employee` Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="05cbd-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="05cbd-110">Deklarieren Sie eine Klasse, die definiert, die dynamischen Parameter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="05cbd-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="05cbd-111">Sie können die Attribute, mit denen Sie deklarieren die statische Cmdlet-Parameter, um die dynamischen Parameter zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="05cbd-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="05cbd-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="05cbd-112">Example</span></span>

<span data-ttu-id="05cbd-113">In diesem Beispiel die `Department` -Parameter hinzugefügt wird, wenn der Benutzer gibt die `Employee` Parameter.</span><span class="sxs-lookup"><span data-stu-id="05cbd-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="05cbd-114">Die `Department` Parameter ist ein optionaler Parameter, und das ValidateSet-Attribut wird verwendet, um die zulässigen Argumente angeben.</span><span class="sxs-lookup"><span data-stu-id="05cbd-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="05cbd-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="05cbd-115">See Also</span></span>

[<span data-ttu-id="05cbd-116">System.Management.Automation.Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="05cbd-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="05cbd-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="05cbd-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="05cbd-118">-Cmdlet dynamische Parameter</span><span class="sxs-lookup"><span data-stu-id="05cbd-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="05cbd-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="05cbd-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)