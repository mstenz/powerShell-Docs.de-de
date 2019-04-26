---
title: Typen von Cmdlet-Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067194"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="3cb90-102">Cmdlet-Parametertypen</span><span class="sxs-lookup"><span data-stu-id="3cb90-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="3cb90-103">Dieses Thema beschreibt die verschiedenen Typen von Parametern, die Sie in Cmdlets deklarieren können.</span><span class="sxs-lookup"><span data-stu-id="3cb90-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="3cb90-104">Cmdlet-Parameter können mit Feldern fester Breite, benannte, erforderlich, optional oder switch-Parameter.</span><span class="sxs-lookup"><span data-stu-id="3cb90-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="3cb90-105">Positionelle und benannte Parameter</span><span class="sxs-lookup"><span data-stu-id="3cb90-105">Positional and Named Parameters</span></span>

<span data-ttu-id="3cb90-106">Alle Cmdlet-Parameter sind entweder die benannten oder positionellen Parameter.</span><span class="sxs-lookup"><span data-stu-id="3cb90-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="3cb90-107">Ein benannter Parameter erfordert, dass Sie den Parameternamen und -Argument beim Aufrufen von des-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3cb90-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="3cb90-108">Ein Positionsparameter erfordert nur, dass Sie in der entsprechenden Reihenfolge die Argumente eingeben.</span><span class="sxs-lookup"><span data-stu-id="3cb90-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="3cb90-109">Das System wird dann das erste unbenannte Argument der erste positionelle Parameter zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="3cb90-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="3cb90-110">Das System ordnet das zweite unbenannte Argument an den zweiten unbenannten Parameter und So weiter.</span><span class="sxs-lookup"><span data-stu-id="3cb90-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="3cb90-111">Standardmäßig werden alle Cmdlet-Parameter Parameter benannt.</span><span class="sxs-lookup"><span data-stu-id="3cb90-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="3cb90-112">Um einen benannten Parameter definieren, lassen die `Position` -Schlüsselwort in der **Parameter** -Attributdeklaration, wie in der folgenden Parameterdeklaration dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3cb90-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="3cb90-113">Um einen Positionsparameter zu definieren, fügen die `Position` Schlüsselwort im Parameter-Attributdeklaration, und geben Sie eine Position.</span><span class="sxs-lookup"><span data-stu-id="3cb90-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="3cb90-114">Im folgenden Beispiel wird die `UserName` Parameter als Positionsparameter an Position 0 deklariert ist.</span><span class="sxs-lookup"><span data-stu-id="3cb90-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="3cb90-115">Dies bedeutet, dass das erste Argument für den Aufruf automatisch an diesen Parameter gebunden wird.</span><span class="sxs-lookup"><span data-stu-id="3cb90-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="3cb90-116">Gute Cmdlet-Entwurf empfiehlt, dass die am häufigsten verwendeten Parameter als Positionsparameter deklariert werden, sodass der Benutzer nicht den Parameternamen eingeben, wenn das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3cb90-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="3cb90-117">Positionelle und benannte Parameter akzeptieren, einzelne Argumente oder mehrere Argumente, die durch Kommas getrennt.</span><span class="sxs-lookup"><span data-stu-id="3cb90-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="3cb90-118">Mehrere Argumente sind nur zulässig, wenn der Parameter eine Auflistung wie z. B. ein Array von Zeichenfolgen akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="3cb90-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="3cb90-119">Sie können positionelle und benannte Parameter in einem Cmdlet kombinieren.</span><span class="sxs-lookup"><span data-stu-id="3cb90-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="3cb90-120">In diesem Fall ruft das System zuerst die benannten Argumente ab, und klicken Sie dann versuchen, die verbleibenden zuordnen unbenannte Argumente für die Positionsparameter.</span><span class="sxs-lookup"><span data-stu-id="3cb90-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="3cb90-121">Die folgenden Befehle demonstrieren die verschiedenen Möglichkeiten, in dem Sie, für einzelne und mehrere Argumente für die Parameter von angeben können, der `Get-Command` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3cb90-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="3cb90-122">Beachten Sie, dass in den letzten zwei Beispielen **-Namen** muss nicht angegeben werden, da die `Name` Parameter als Positionsparameter definiert ist.</span><span class="sxs-lookup"><span data-stu-id="3cb90-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="3cb90-123">Obligatorischen und optionalen Parametern</span><span class="sxs-lookup"><span data-stu-id="3cb90-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="3cb90-124">Sie können auch die Cmdlet-Parameter als obligatorisch oder optional Parameter definieren.</span><span class="sxs-lookup"><span data-stu-id="3cb90-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="3cb90-125">(Ein obligatorischen Parameter muss angegeben werden, bevor die Windows PowerShell-Laufzeit das Cmdlet aufruft.)  Standardmäßig werden Parameter als optional definiert.</span><span class="sxs-lookup"><span data-stu-id="3cb90-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="3cb90-126">Um einen obligatorischen Parameter zu definieren, fügen die `Mandatory` Schlüsselwort im Parameter-Attributdeklaration, und legen Sie ihn auf `true`, wie in der folgenden Parameterdeklaration dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3cb90-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="3cb90-127">Um einen optionalen Parameter zu definieren, lassen die `Mandatory` -Schlüsselwort in der **Parameter** -Attributdeklaration, wie in der folgenden Parameterdeklaration dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3cb90-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="3cb90-128">Switch-Parameter</span><span class="sxs-lookup"><span data-stu-id="3cb90-128">Switch Parameters</span></span>

<span data-ttu-id="3cb90-129">Windows PowerShell bietet eine [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) Typ, der können Sie einen Parameter definieren, deren Wert wird automatisch festgelegt, um `false` , wenn der Parameter nicht angegeben wird, wenn das Cmdlet wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="3cb90-129">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="3cb90-130">Verwenden Sie nach Möglichkeit anstelle von booleschen Parametern Switch-Parameter.</span><span class="sxs-lookup"><span data-stu-id="3cb90-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="3cb90-131">Betrachten Sie das folgende Beispiel aus.</span><span class="sxs-lookup"><span data-stu-id="3cb90-131">Consider the following sample.</span></span> <span data-ttu-id="3cb90-132">Mehrere Windows PowerShell-Cmdlets übergeben werden standardmäßig kein Ausgabeobjekt entlang der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="3cb90-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="3cb90-133">Diese Cmdlets haben jedoch eine `PassThru` switch-Parameter, die das Standardverhalten überschrieben.</span><span class="sxs-lookup"><span data-stu-id="3cb90-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="3cb90-134">Wenn die `PassThru` Parameter angegeben ist, wenn diese Cmdlets aufgerufen werden, das Cmdlet gibt ein Ausgabeobjekt an die Pipeline zurück.</span><span class="sxs-lookup"><span data-stu-id="3cb90-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="3cb90-135">Bei Bedarf den Parameter, um einen Standardwert besitzen `true` der Parameter im Aufruf nicht angegeben ist, berücksichtigen Sie die Bedeutung von der Parameter umkehren.</span><span class="sxs-lookup"><span data-stu-id="3cb90-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="3cb90-136">Beispiel, statt das Parameter-Attribut in einen booleschen Wert der `true`, deklarieren Sie die Eigenschaft als die [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) geben, und legen Sie dann auf den Standardwert des Parameters, der `false`.</span><span class="sxs-lookup"><span data-stu-id="3cb90-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="3cb90-137">Um einen Switch-Parameter zu definieren, deklarieren Sie die Eigenschaft als die [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) eingeben, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="3cb90-137">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="3cb90-138">Damit wird das Cmdlet für den Parameter zu reagieren, wenn es angegeben ist, verwenden Sie die folgende Struktur in einem der eingabeverarbeitungsmethoden.</span><span class="sxs-lookup"><span data-stu-id="3cb90-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="3cb90-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3cb90-139">See Also</span></span>

[<span data-ttu-id="3cb90-140">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3cb90-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
