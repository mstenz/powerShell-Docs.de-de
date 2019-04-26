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
# <a name="how-to-declare-dynamic-parameters"></a>Deklarieren von dynamischen Parametern

Dieses Beispiel zeigt, wie Sie dynamische Parameter definieren, die an das Cmdlet zur Laufzeit hinzugefügt werden. In diesem Beispiel die `Department` Parameter wird an das Cmdlet hinzugefügt, wenn der Benutzer gibt die `Employee` switch-Parameter. Weitere Informationen zu dynamischen Parametern finden Sie unter [dynamische Cmdletparameter](./cmdlet-dynamic-parameters.md).

## <a name="to-define-dynamic-parameters"></a>Um dynamische Parameter zu definieren.

1. Fügen Sie in der Cmdlet-Klassendeklaration, die [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) -Schnittstelle wie gezeigt.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Rufen Sie die [System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) Methode, die das Objekt zurückgibt, die dynamischen Parameter definiert sind. In diesem Beispiel ist die Methode wird aufgerufen, wenn die `Employee` Parameter angegeben ist.

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

3. Deklarieren Sie eine Klasse, die definiert, die dynamischen Parameter hinzugefügt werden. Sie können die Attribute, mit denen Sie deklarieren die statische Cmdlet-Parameter, um die dynamischen Parameter zu deklarieren.

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

## <a name="example"></a>Beispiel

In diesem Beispiel die `Department` -Parameter hinzugefügt wird, wenn der Benutzer gibt die `Employee` Parameter. Die `Department` Parameter ist ein optionaler Parameter, und das ValidateSet-Attribut wird verwendet, um die zulässigen Argumente angeben.

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

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[-Cmdlet dynamische Parameter](./cmdlet-dynamic-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)