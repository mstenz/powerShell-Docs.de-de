---
title: Cmdlet-Parameter legt fest | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068507"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="84af5-102">Cmdlet-Parametersätze</span><span class="sxs-lookup"><span data-stu-id="84af5-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="84af5-103">Windows PowerShell verwendet die Parameter legt fest, sodass Sie ein einzelnes Cmdlet schreiben, das für verschiedene Szenarien verschiedene Aktionen ausführen können.</span><span class="sxs-lookup"><span data-stu-id="84af5-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="84af5-104">Parametersätze können Sie verschiedene Parameter für den Benutzer verfügbar zu machen und anderen Informationen, die auf Grundlage der vom Benutzer angegebene Parameter zurückgegeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="84af5-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="84af5-105">Beispiele für die Parametersätze</span><span class="sxs-lookup"><span data-stu-id="84af5-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="84af5-106">Z. B. die `Get-EventLog` Cmdlet (bereitgestellt vom Windows PowerShell) gibt unterschiedliche Informationen, je nachdem, ob der Benutzer gibt die `List` oder `LogName` Parameter.</span><span class="sxs-lookup"><span data-stu-id="84af5-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="84af5-107">Wenn die `List` -Parameter angegeben wird, mit dem-Cmdlet gibt Informationen zu den Protokolldateien selbst jedoch nicht die darin enthaltenen Informationen.</span><span class="sxs-lookup"><span data-stu-id="84af5-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="84af5-108">Wenn die `LogName` -Parameter angegeben wird, das Cmdlet gibt Informationen zu den Ereignissen in einem bestimmten Ereignisprotokoll zurück.</span><span class="sxs-lookup"><span data-stu-id="84af5-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="84af5-109">Die `List` und `LogName` Parameter zu identifizieren, zwei separate Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="84af5-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="84af5-110">Unique-Parameter</span><span class="sxs-lookup"><span data-stu-id="84af5-110">Unique Parameter</span></span>

<span data-ttu-id="84af5-111">Jeder Parametersatz muss es sich um einen eindeutigen Parameter aufweisen, den die Windows PowerShell-Laufzeit verwenden können, um den entsprechenden Parametersatz verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="84af5-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="84af5-112">Wenn möglich, muss die unique-Parameter ein erforderlicher Parameter.</span><span class="sxs-lookup"><span data-stu-id="84af5-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="84af5-113">Wenn ein Parameter obligatorisch ist, zum Angeben des Parameters wird der Benutzer gezwungen, und die Windows PowerShell-Laufzeit kann diesen Parameter verwenden, um den Parametersatz verwenden identifizieren.</span><span class="sxs-lookup"><span data-stu-id="84af5-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="84af5-114">Die unique-Parameter ist nicht erforderlich, wenn Sie Ihr Cmdlet ohne Angabe von Parametern ausgeführt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="84af5-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="84af5-115">Mehrere Parametersätze</span><span class="sxs-lookup"><span data-stu-id="84af5-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="84af5-116">In der folgenden Abbildung zeigt die linke Spalte drei gültigen Parametersätze an.</span><span class="sxs-lookup"><span data-stu-id="84af5-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="84af5-117">Ein-Parameter gilt nur für den ersten Parametersatz, B-Parameter gilt nur für den zweiten Parametersatz und C-Parameter gilt nur für den dritten Parametersatz.</span><span class="sxs-lookup"><span data-stu-id="84af5-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="84af5-118">Allerdings müssen in der rechten Spalte, die Parametersätze einen unique-Parameter keine.</span><span class="sxs-lookup"><span data-stu-id="84af5-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="84af5-120">Parametersatz Anforderungen</span><span class="sxs-lookup"><span data-stu-id="84af5-120">Parameter Set Requirements</span></span>

<span data-ttu-id="84af5-121">Die folgenden Anforderungen gelten für alle Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="84af5-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="84af5-122">Jeder Parametersatz müssen mindestens eine unique-Parameter.</span><span class="sxs-lookup"><span data-stu-id="84af5-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="84af5-123">Wenn möglich, stellen Sie diesen Parameter einen obligatorischen Parameter.</span><span class="sxs-lookup"><span data-stu-id="84af5-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="84af5-124">Ein Parametersatz, der mehrere positionelle Parameter enthält, muss eindeutige Positionen für jeden Parameter definieren.</span><span class="sxs-lookup"><span data-stu-id="84af5-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="84af5-125">Keine zwei positionelle Parameter können die gleiche Position angeben.</span><span class="sxs-lookup"><span data-stu-id="84af5-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="84af5-126">Kann nur einen Parameter in einem Satz deklarieren die `ValueFromPipeline` Schlüsselwort mit einem Wert von `true`.</span><span class="sxs-lookup"><span data-stu-id="84af5-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="84af5-127">Es können mehrere Parameter definieren die `ValueFromPipelineByPropertyName` Schlüsselwort mit einem Wert von `true`.</span><span class="sxs-lookup"><span data-stu-id="84af5-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="84af5-128">Wenn kein Parameter festgelegt, die für einen Parameter angegeben wird, gehört der Parameter alle Parametersätze.</span><span class="sxs-lookup"><span data-stu-id="84af5-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="84af5-129">Standard-Parametersätze</span><span class="sxs-lookup"><span data-stu-id="84af5-129">Default Parameter Sets</span></span>

<span data-ttu-id="84af5-130">Wenn mehrere Parametersätze definiert sind, können Sie die `DefaultParameterSetName` -Schlüsselwort von der Cmdlet-Attribut, um den Standardsatz der Parameter anzugeben.</span><span class="sxs-lookup"><span data-stu-id="84af5-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="84af5-131">Windows PowerShell verwendet die Standardparameter festgelegt, wenn sie nicht bestimmen kann, abhängig von den Angaben, die mit dem Befehl der Parametersatz verwenden.</span><span class="sxs-lookup"><span data-stu-id="84af5-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="84af5-132">Weitere Informationen zu den Cmdlet-Attribut, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="84af5-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="84af5-133">Deklarieren von Parametersätzen</span><span class="sxs-lookup"><span data-stu-id="84af5-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="84af5-134">Um einen Parametersatz erstellen zu können, müssen Sie geben die `ParameterSetName` -Schlüsselwort, wenn Sie das Parameter-Attribut für jeden Parameter im Parametersatz deklarieren.</span><span class="sxs-lookup"><span data-stu-id="84af5-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="84af5-135">Für Parameter, die mehrere Parametersätze angehören, fügen Sie ein Parameterattribut für jeden Parameter festgelegt.</span><span class="sxs-lookup"><span data-stu-id="84af5-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="84af5-136">Dadurch können Sie den Parameter für jeden Parametersatz unterschiedlich definieren.</span><span class="sxs-lookup"><span data-stu-id="84af5-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="84af5-137">Beispielsweise können Sie einen Parameter als in einem Satz obligatorischen und optionalen, in einer anderen definieren.</span><span class="sxs-lookup"><span data-stu-id="84af5-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="84af5-138">Allerdings muss jeder Parametersatz eine unique-Parameter enthalten.</span><span class="sxs-lookup"><span data-stu-id="84af5-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="84af5-139">Im folgenden Beispiel die `UserName` Parameter ist der eindeutige Parameter die Menge an Test01-Parameter, und die `ComputerName` Parameter ist der unique-Parameter von der Test02 Parameter festgelegt.</span><span class="sxs-lookup"><span data-stu-id="84af5-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="84af5-140">Die `SharedParam` Parameter gehört zu beiden Sätzen und ist erforderlich, damit der Test01-Parameter, die aber für den Parametersatz Test02 optional festgelegt.</span><span class="sxs-lookup"><span data-stu-id="84af5-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```