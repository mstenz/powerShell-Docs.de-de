---
title: Parameteraliase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067585"
---
# <a name="parameter-aliases"></a><span data-ttu-id="f8eb4-102">Parameteraliase</span><span class="sxs-lookup"><span data-stu-id="f8eb4-102">Parameter Aliases</span></span>

<span data-ttu-id="f8eb4-103">Cmdlet-Parameter können auch Aliase aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="f8eb4-104">Sie können die Aliase anstatt den Parameternamen verwenden, eingeben oder geben Sie den Parameter in einem Befehl.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="f8eb4-105">Vorteile der Verwendung von Aliasen</span><span class="sxs-lookup"><span data-stu-id="f8eb4-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="f8eb4-106">Hinzufügen von Aliasen zu Parameter bietet die folgenden Vorteile.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="f8eb4-107">Sie können eine Verknüpfung bereitstellen, sodass der Benutzer nicht der vollständige Parametername verwendet wird, wenn das-Cmdlet aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="f8eb4-108">Beispielsweise können Sie den Alias "CN" statt des Parameternamens "ComputerName".</span><span class="sxs-lookup"><span data-stu-id="f8eb4-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="f8eb4-109">Sie können mehrere Aliasnamen definieren, sollten Sie andere Namen für den gleichen Parameter bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="f8eb4-110">Sie möchten mehrere Aliase zu definieren, wenn man arbeiten mit mehreren Benutzergruppen, die auf dieselben Daten auf unterschiedliche Weise zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="f8eb4-111">Sie können die Kompatibilität Abwärtskompatibilität für vorhandene Skripts angeben, wenn ändert sich der Name eines Parameters.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="f8eb4-112">Verwenden Sie die Alias-Attribut zusammen mit dem Attribut ValueFromPipelineByName, können Sie einen Parameter definieren, der Ihr Cmdlet zum Binden an verschiedene Objekttypen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="f8eb4-113">Angenommen Sie, Sie haben zwei Objekte unterschiedlicher Typen und das erste Objekt eine Eigenschaft Writer und das zweite Objekt hatten eine editoreigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="f8eb4-114">Hätte Ihr Cmdlet Parameter, die Autor und Editor-Aliase und mit dem Cmdlet akzeptiert Pipelineeingabe basierend auf den Eigenschaftennamen, Ihr Cmdlet konnte auf beide Objekte, die mit den zwei Parameter Aliasen binden.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="f8eb4-115">Weitere Informationen zu Aliasen, die mit bestimmten Parametern verwendet werden können, finden Sie unter [allgemeine Parameternamen](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="f8eb4-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="f8eb4-116">Definieren Parameteraliase</span><span class="sxs-lookup"><span data-stu-id="f8eb4-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="f8eb4-117">Deklarieren Sie die Alias-Attribut, um einen Alias für einen Parameter zu definieren, wie in der folgenden Parameterdeklaration dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="f8eb4-118">In diesem Beispiel werden mehrere Aliase für den gleichen Parameter definiert.</span><span class="sxs-lookup"><span data-stu-id="f8eb4-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="f8eb4-119">(Weitere Informationen finden Sie unter[wie Cmdlet-Parametern deklarieren](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="f8eb4-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f8eb4-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f8eb4-120">See Also</span></span>

[<span data-ttu-id="f8eb4-121">Allgemeine Parameternamen</span><span class="sxs-lookup"><span data-stu-id="f8eb4-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="f8eb4-122">Gewusst wie: Deklarieren von Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="f8eb4-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="f8eb4-123">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f8eb4-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
