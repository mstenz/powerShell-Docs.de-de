---
title: 'Gewusst wie: Deklarieren von Parametersätzen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067891"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="66866-102">Deklarieren von Parametersätzen</span><span class="sxs-lookup"><span data-stu-id="66866-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="66866-103">Dieses Beispiel zeigt, wie zwei Parametersätze definiert werden, wenn Sie die Parameter für ein Cmdlet zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="66866-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="66866-104">Jeder Parametersatz sind eine unique-Parameter und freigegebene Parameter, der von beiden Parametersätze verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="66866-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="66866-105">Weitere Informationen zu Parametern Mengen, einschließlich der Parameter den Standardsatz an finden Sie unter [Cmdlet Parametersätze](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="66866-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66866-106">Wann immer möglich, definieren Sie den unique-Parameter eines Parameters, der als ein erforderlicher Parameter festlegen.</span><span class="sxs-lookup"><span data-stu-id="66866-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="66866-107">Wenn Sie Ihr Cmdlet ohne Angabe von Parametern ausführen möchten, kann allerdings der unique-Parameter einen optionalen Parameter sein.</span><span class="sxs-lookup"><span data-stu-id="66866-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="66866-108">Z. B. die unique-Parameter von der `Get-Command` Cmdlet ist optional.</span><span class="sxs-lookup"><span data-stu-id="66866-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="66866-109">Gewusst wie: Definieren von zwei Parametersätze</span><span class="sxs-lookup"><span data-stu-id="66866-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="66866-110">Hinzufügen der `ParameterSet` Schlüsselwort, das Parameter-Attribut eindeutig als Parameter für den ersten Parametersatz.</span><span class="sxs-lookup"><span data-stu-id="66866-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="66866-111">Hinzufügen der `ParameterSet` Schlüsselwort, das Parameter-Attribut eindeutig als Parameter für den zweiten Parametersatz.</span><span class="sxs-lookup"><span data-stu-id="66866-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="66866-112">Für den Parameter, die zu beiden Parametersätzen gehört, für jeden Parameter einen Parameter-Attribut hinzufügen und dann die `ParameterSet` Schlüsselwort, um jeden Satz.</span><span class="sxs-lookup"><span data-stu-id="66866-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="66866-113">In jedem Parameter-Attribut können Sie angeben, wie dieser Parameter definiert ist.</span><span class="sxs-lookup"><span data-stu-id="66866-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="66866-114">Ein Parameter kann optional in einem Satz und in einer anderen obligatorisch sein.</span><span class="sxs-lookup"><span data-stu-id="66866-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="66866-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="66866-115">See Also</span></span>

[<span data-ttu-id="66866-116">Cmdlet-Parameter legt fest</span><span class="sxs-lookup"><span data-stu-id="66866-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="66866-117">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="66866-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
