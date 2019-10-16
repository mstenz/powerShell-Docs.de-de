---
title: Deklarieren von Eigenschaften als Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365749"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="ebfac-102">Deklarieren von Eigenschaften als Parameter</span><span class="sxs-lookup"><span data-stu-id="ebfac-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="ebfac-103">Dieses Thema enthält grundlegende Informationen, die Sie kennen müssen, bevor Sie die Parameter eines Cmdlets deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ebfac-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="ebfac-104">Um die Parameter eines Cmdlets in der Cmdlet-Klasse zu deklarieren, definieren Sie die öffentlichen Eigenschaften, die die einzelnen Parameter darstellen, und fügen Sie jeder Eigenschaft ein oder mehrere Parameter Attribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="ebfac-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="ebfac-105">Die Windows PowerShell-Laufzeit verwendet die Parameter Attribute, um die Eigenschaft als Cmdlet-Parameter zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="ebfac-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="ebfac-106">Die grundlegende Syntax zum Deklarieren des Parameter Attributs ist `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="ebfac-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="ebfac-107">Im folgenden finden Sie ein Beispiel für eine Eigenschaft, die als erforderlicher Parameter definiert ist.</span><span class="sxs-lookup"><span data-stu-id="ebfac-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="ebfac-108">Im folgenden finden Sie einige Dinge, die Sie über Parameter berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="ebfac-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="ebfac-109">Ein Parameter muss explizit als public gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="ebfac-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="ebfac-110">Parameter, die nicht als öffentlich gekennzeichnet sind, sind standardmäßig intern und werden von der Windows PowerShell-Laufzeit nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="ebfac-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="ebfac-111">Parameter sollten als Microsoft .NET Frameworktypen definiert werden, um eine bessere Parameter Validierung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ebfac-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="ebfac-112">Beispielsweise sollten Parameter, die auf einen Wert aus einer Menge von Werten beschränkt sind, als Enumerationstyp definiert werden.</span><span class="sxs-lookup"><span data-stu-id="ebfac-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="ebfac-113">Parameter, die einen Uniform Resource Identifier-Wert (URI) annehmen, müssen den Typ " [System. Uri](/dotnet/api/System.Uri)" aufweisen.</span><span class="sxs-lookup"><span data-stu-id="ebfac-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="ebfac-114">Vermeiden Sie grundlegende Zeichen folgen Parameter für alle außer frei Form Texteigenschaften.</span><span class="sxs-lookup"><span data-stu-id="ebfac-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="ebfac-115">Sie können einem Parameter eine beliebige Anzahl von Parametersätzen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ebfac-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="ebfac-116">Weitere Informationen zu Parametersätzen finden Sie unter [Cmdlet-Parametersätze](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ebfac-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="ebfac-117">Windows PowerShell bietet auch eine Reihe allgemeiner Parameter, die für jedes Cmdlet automatisch verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ebfac-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="ebfac-118">Weitere Informationen zu diesen Parametern und ihren Aliasen finden [Sie unter Allgemeine Cmdlet-Parameter](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="ebfac-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebfac-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ebfac-119">See Also</span></span>

[<span data-ttu-id="ebfac-120">Allgemeine Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="ebfac-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="ebfac-121">Typen von Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="ebfac-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="ebfac-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ebfac-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
