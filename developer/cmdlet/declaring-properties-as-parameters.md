---
title: Deklarieren von Eigenschaften, die als Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068265"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="3cf44-102">Deklarieren von Eigenschaften als Parameter</span><span class="sxs-lookup"><span data-stu-id="3cf44-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="3cf44-103">Dieses Thema enthält grundlegende Informationen, die Sie verstehen müssen, bevor Sie mit die Parametern eines Cmdlets deklarieren.</span><span class="sxs-lookup"><span data-stu-id="3cf44-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="3cf44-104">Um den Parametern eines Cmdlets in der Cmdlet-Klasse zu deklarieren, definieren Sie die öffentlichen Eigenschaften, die jeden Parameter darstellen, und fügen Sie dann auf jede Eigenschaft eine oder mehrere Parameter-Attribute hinzu.</span><span class="sxs-lookup"><span data-stu-id="3cf44-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="3cf44-105">Die Windows PowerShell-Laufzeit verwendet die Parameterattribute bezeichnen die Eigenschaft als Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="3cf44-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="3cf44-106">Die grundlegende Syntax zum Deklarieren der Parameter-Attribut ist `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="3cf44-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="3cf44-107">Hier ist ein Beispiel für eine Eigenschaft, die als ein erforderlicher Parameter definiert.</span><span class="sxs-lookup"><span data-stu-id="3cf44-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="3cf44-108">Hier sind einige wichtige Aspekte für Informationen zu Parametern.</span><span class="sxs-lookup"><span data-stu-id="3cf44-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="3cf44-109">Parameter muss explizit als öffentlich markiert werden.</span><span class="sxs-lookup"><span data-stu-id="3cf44-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="3cf44-110">Parameter, die nicht als öffentlicher Standard auf interne gekennzeichnet sind, und werden von der Windows PowerShell-Laufzeit nicht gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="3cf44-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="3cf44-111">Parameter müssen als Microsoft .NET Framework-Typen zu besseren parametervalidierung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="3cf44-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="3cf44-112">Beispielsweise sollten Parameter, die auf einen Wert aus dem Satz von Werten beschränkt sind, als ein Enumerationstyp definiert werden.</span><span class="sxs-lookup"><span data-stu-id="3cf44-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="3cf44-113">Parameter, die einen Uniform Resource Identifier (URI)-Wert akzeptieren muss vom Typ [System.Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="3cf44-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="3cf44-114">Vermeiden Sie die allgemeine Zeichenfolgen-Parameter für alle außer Freitext-Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="3cf44-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="3cf44-115">Sie können einen Parameter an eine beliebige Anzahl von Parametersätzen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3cf44-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="3cf44-116">Weitere Informationen zu Parametersätze, finden Sie unter [Cmdlet Parametersätze](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3cf44-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="3cf44-117">Windows PowerShell bietet auch einen Satz von allgemeinen Parametern, die automatisch für jedes Cmdlet verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="3cf44-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="3cf44-118">Weitere Informationen zu diesen Parametern und ihre Aliase finden Sie unter [allgemeinen Cmdlet-Parameter](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="3cf44-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3cf44-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3cf44-119">See Also</span></span>

[<span data-ttu-id="3cf44-120">-Cmdlet allgemeine Parameter</span><span class="sxs-lookup"><span data-stu-id="3cf44-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="3cf44-121">Typen von Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="3cf44-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="3cf44-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3cf44-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
