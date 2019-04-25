---
title: -Cmdlet dynamische Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068537"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="aacfd-102">Dynamische Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="aacfd-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="aacfd-103">Cmdlets können Parameter definieren, die für den Benutzer unter speziellen Bedingungen, z. B. wenn das Argument eines anderen Parameters für einen bestimmten Wert ist verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="aacfd-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="aacfd-104">Diese Parameter werden zur Laufzeit hinzugefügt und werden als bezeichnet *dynamische Parameter* , da sie nur bei Bedarf hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="aacfd-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="aacfd-105">Beispielsweise können Sie ein Cmdlet entwerfen, die mehrere Parameter hinzufügt, nur, wenn Sie ein bestimmten Switch-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="aacfd-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="aacfd-106">Anbieter und Windows PowerShell-Funktionen können auch mit dynamische Parametern definieren.</span><span class="sxs-lookup"><span data-stu-id="aacfd-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="aacfd-107">Dynamische Parameter in Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="aacfd-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="aacfd-108">Windows PowerShell verwendet dynamische Parameter in einige der Anbieter-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="aacfd-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="aacfd-109">Z. B. die `Get-Item` und `Get-ChildItem` hinzufügen-Cmdlets eine `CodeSigningCert` Parameter zur Laufzeit bei der `Path` -Parameter des Cmdlets gibt den Pfad des Anbieters an.</span><span class="sxs-lookup"><span data-stu-id="aacfd-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="aacfd-110">Wenn die `Path` -Parameter des Cmdlets gibt einen Pfad für einen anderen Anbieter, der `CodeSigningCert` Parameter ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="aacfd-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="aacfd-111">Die folgenden Beispiele zeigen wie die `CodeSigningCert` -Parameter zur Laufzeit hinzugefügt bei der `Get-Item` Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aacfd-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="aacfd-112">Im ersten Beispiel ist die Windows PowerShell-Laufzeit wurde den Parameter hinzugefügt, und das Cmdlet erfolgreich ist.</span><span class="sxs-lookup"><span data-stu-id="aacfd-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="aacfd-113">Klicken Sie im zweiten Beispiel einem Dateisystemlaufwerk angegeben ist, und ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="aacfd-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="aacfd-114">Die Fehlermeldung gibt an, dass die `CodeSigningCert` Parameter wurde nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="aacfd-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="aacfd-115">Unterstützung für dynamische Parameter</span><span class="sxs-lookup"><span data-stu-id="aacfd-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="aacfd-116">Um dynamische Parameter zu unterstützen, muss der Cmdlet-Code die folgenden Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="aacfd-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="aacfd-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) diese Schnittstelle stellt die Methode, die dynamischen Parameter abruft.</span><span class="sxs-lookup"><span data-stu-id="aacfd-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="aacfd-118">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aacfd-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="aacfd-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) diese Methode ruft das Objekt, das die Definitionen für die dynamischen Parameter enthält.</span><span class="sxs-lookup"><span data-stu-id="aacfd-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="aacfd-120">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aacfd-120">Example:</span></span>

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

<span data-ttu-id="aacfd-121">Dynamische Parameter-Klasse definiert diese Klasse die Parameter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="aacfd-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="aacfd-122">Diese Klasse muss einen Parameter-Attribut für jeden Parameter und alle optionalen Alias und Validierung-Attribute, die vom Cmdlet erforderlich sind, enthalten.</span><span class="sxs-lookup"><span data-stu-id="aacfd-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="aacfd-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="aacfd-123">Example:</span></span>

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

<span data-ttu-id="aacfd-124">Ein vollständiges Beispiel eines Cmdlets, die dynamischen Parameter unterstützt, finden Sie unter [wie dynamische Parameter deklarieren](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aacfd-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aacfd-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aacfd-125">See Also</span></span>

[<span data-ttu-id="aacfd-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="aacfd-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="aacfd-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="aacfd-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="aacfd-128">Gewusst wie: Deklarieren von dynamischen Parametern</span><span class="sxs-lookup"><span data-stu-id="aacfd-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="aacfd-129">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="aacfd-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
