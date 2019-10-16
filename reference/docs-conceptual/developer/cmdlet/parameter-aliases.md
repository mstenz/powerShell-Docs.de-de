---
title: Parameter Aliase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369589"
---
# <a name="parameter-aliases"></a><span data-ttu-id="034d7-102">Parameteraliase</span><span class="sxs-lookup"><span data-stu-id="034d7-102">Parameter Aliases</span></span>

<span data-ttu-id="034d7-103">Cmdlet-Parameter können auch Aliase enthalten.</span><span class="sxs-lookup"><span data-stu-id="034d7-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="034d7-104">Sie können die Aliase anstelle der Parameternamen verwenden, wenn Sie den-Parameter in einem-Befehl eingeben oder angeben.</span><span class="sxs-lookup"><span data-stu-id="034d7-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="034d7-105">Vorteile der Verwendung von Aliasen</span><span class="sxs-lookup"><span data-stu-id="034d7-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="034d7-106">Das Hinzufügen von Aliasen zu Parametern bietet die folgenden Vorteile.</span><span class="sxs-lookup"><span data-stu-id="034d7-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="034d7-107">Sie können eine Verknüpfung bereitstellen, sodass der Benutzer nicht den kompletten Parameternamen verwenden muss, wenn das Cmdlet aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="034d7-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="034d7-108">Beispielsweise können Sie den Alias "CN" anstelle des Parameter namens "Computername" verwenden.</span><span class="sxs-lookup"><span data-stu-id="034d7-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="034d7-109">Sie können mehrere Aliase definieren, wenn Sie unterschiedliche Namen für denselben Parameter angeben möchten.</span><span class="sxs-lookup"><span data-stu-id="034d7-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="034d7-110">Möglicherweise möchten Sie mehrere Aliase definieren, wenn Sie mit mehreren Benutzergruppen arbeiten müssen, die auf unterschiedliche Weise auf dieselben Daten verweisen.</span><span class="sxs-lookup"><span data-stu-id="034d7-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="034d7-111">Sie können die Abwärtskompatibilität für vorhandene Skripts bereitstellen, wenn sich der Name eines Parameters ändert.</span><span class="sxs-lookup"><span data-stu-id="034d7-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="034d7-112">Mithilfe des Alias-Attributs und des valuefrompipelinebyname-Attributs können Sie einen Parameter definieren, mit dem das Cmdlet an verschiedene Objekttypen gebunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="034d7-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="034d7-113">Angenommen, Sie haben zwei Objekte verschiedener Typen, und das erste Objekt verfügte über eine Writer-Eigenschaft, und das zweite Objekt verfügte über eine Editor-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="034d7-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="034d7-114">Wenn das Cmdlet über einen Parameter verfügt, der über Writer-und Editor-Aliase verfügt und das Cmdlet Pipeline Eingaben auf der Grundlage von Eigenschaftsnamen akzeptiert hat, könnte das Cmdlet mithilfe der beiden Parameter Aliase eine Bindung an beide Objekte herstellen.</span><span class="sxs-lookup"><span data-stu-id="034d7-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="034d7-115">Weitere Informationen zu Aliasen, die mit bestimmten Parametern verwendet werden können, finden Sie unter [Allgemeine Parameternamen](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="034d7-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="034d7-116">Definieren von Parameter Aliasen</span><span class="sxs-lookup"><span data-stu-id="034d7-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="034d7-117">Um einen Alias für einen Parameter zu definieren, deklarieren Sie das Alias Attribut, wie in der folgenden Parameter Deklaration gezeigt.</span><span class="sxs-lookup"><span data-stu-id="034d7-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="034d7-118">In diesem Beispiel werden mehrere Aliase für denselben Parameter definiert.</span><span class="sxs-lookup"><span data-stu-id="034d7-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="034d7-119">(Weitere Informationen finden Sie unter[Deklarieren von Cmdlet-Parametern](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="034d7-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="034d7-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="034d7-120">See Also</span></span>

[<span data-ttu-id="034d7-121">Allgemeine Parameter Namen</span><span class="sxs-lookup"><span data-stu-id="034d7-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="034d7-122">Deklarieren von Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="034d7-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="034d7-123">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="034d7-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
