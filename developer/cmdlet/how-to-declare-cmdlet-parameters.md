---
title: 'Gewusst wie: Deklarieren von Cmdlet-Parameter | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067914"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="57f1e-102">Deklarieren von Cmdlet-Parametern</span><span class="sxs-lookup"><span data-stu-id="57f1e-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="57f1e-103">Diese Beispiele zeigen, wie Sie benannte, mit Feldern fester Breite, erforderlich, optional zu deklarieren und switch-Parameter.</span><span class="sxs-lookup"><span data-stu-id="57f1e-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="57f1e-104">Diese Beispiele zeigen auch einen parameteralias definieren.</span><span class="sxs-lookup"><span data-stu-id="57f1e-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="57f1e-105">Beschreibt, wie einen benannten Parameter deklariert</span><span class="sxs-lookup"><span data-stu-id="57f1e-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="57f1e-106">Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="57f1e-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="57f1e-107">Wenn Sie das Parameter-Attribut hinzufügen, weglassen der `Position` Schlüsselwort aus dem Attribut.</span><span class="sxs-lookup"><span data-stu-id="57f1e-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="57f1e-108">Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57f1e-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="57f1e-109">Gewusst wie: Deklarieren eines Parameters mit Feldern fester Breite</span><span class="sxs-lookup"><span data-stu-id="57f1e-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="57f1e-110">Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="57f1e-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="57f1e-111">Wenn Sie das Parameter-Attribut hinzufügen, setzen die `Position` Schlüsselwort, um die Position des formatlistenarguments.</span><span class="sxs-lookup"><span data-stu-id="57f1e-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="57f1e-112">Der Wert 0 gibt an, die erste Position.</span><span class="sxs-lookup"><span data-stu-id="57f1e-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="57f1e-113">Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57f1e-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="57f1e-114">Wie Sie einen obligatorischen Parameter deklarieren</span><span class="sxs-lookup"><span data-stu-id="57f1e-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="57f1e-115">Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="57f1e-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="57f1e-116">Wenn Sie das Parameter-Attribut hinzufügen, setzen die `Mandatory` Schlüsselwort `true`.</span><span class="sxs-lookup"><span data-stu-id="57f1e-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="57f1e-117">Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57f1e-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="57f1e-118">Wie Sie einen optionalen Parameter deklarieren</span><span class="sxs-lookup"><span data-stu-id="57f1e-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="57f1e-119">Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="57f1e-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="57f1e-120">Wenn Sie das Parameter-Attribut hinzufügen, weglassen der `Mandatory` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="57f1e-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="57f1e-121">Gewusst wie: deklarieren einen Switch-Parameter</span><span class="sxs-lookup"><span data-stu-id="57f1e-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="57f1e-122">Definieren Sie eine öffentliche Eigenschaft als Typ [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), und klicken Sie dann das Parameter-Attribut zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="57f1e-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="57f1e-123">Weitere Informationen über das Parameter-Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57f1e-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="57f1e-124">Gewusst wie: Deklarieren eines Parameters mit Aliasen</span><span class="sxs-lookup"><span data-stu-id="57f1e-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="57f1e-125">Definieren Sie eine öffentliche Eigenschaft, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="57f1e-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="57f1e-126">Fügen Sie ein Alias-Attribut, das die Aliase für den Parameter enthält.</span><span class="sxs-lookup"><span data-stu-id="57f1e-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="57f1e-127">In diesem Beispiel werden drei Aliase für den gleichen Parameter definiert.</span><span class="sxs-lookup"><span data-stu-id="57f1e-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="57f1e-128">Der erste Alias stellt eine Verknüpfung.</span><span class="sxs-lookup"><span data-stu-id="57f1e-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="57f1e-129">Die zweite und dritte Aliase Geben Sie den Namen, die Sie für verschiedene Szenarien verwenden können.</span><span class="sxs-lookup"><span data-stu-id="57f1e-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="57f1e-130">Weitere Informationen zu den Alias-Attribut, finden Sie unter [Alias Attributdeklaration](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="57f1e-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57f1e-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="57f1e-131">See Also</span></span>

[<span data-ttu-id="57f1e-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="57f1e-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="57f1e-133">Parameterdeklaration-Attribut</span><span class="sxs-lookup"><span data-stu-id="57f1e-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="57f1e-134">Alias-Attributdeklaration</span><span class="sxs-lookup"><span data-stu-id="57f1e-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="57f1e-135">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="57f1e-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
