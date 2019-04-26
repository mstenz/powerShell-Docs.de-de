---
title: Alias-Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068713"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="4ca27-102">Attributdeklaration: Alias</span><span class="sxs-lookup"><span data-stu-id="4ca27-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="4ca27-103">Der Alias-Attribut ermöglicht den Benutzer, unterschiedliche Namen für die Cmdlet-Parameter anzugeben.</span><span class="sxs-lookup"><span data-stu-id="4ca27-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="4ca27-104">Aliase können verwendet werden, um die Tastenkombinationen für einen Parameternamen angeben, oder bieten andere Namen, die für verschiedene Szenarien geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="4ca27-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ca27-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ca27-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="4ca27-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="4ca27-106">Parameters</span></span>

<span data-ttu-id="4ca27-107">`aliasName` (Testeigenschaftentyp Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4ca27-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="4ca27-108">Gibt einen Satz von durch Trennzeichen getrennte Aliasnamen für die Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="4ca27-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ca27-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4ca27-109">Remarks</span></span>

- <span data-ttu-id="4ca27-110">Der Alias-Attribut wird mit dem Parameter-Attribut verwendet, wenn Sie einen Cmdlet-Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="4ca27-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="4ca27-111">Weitere Informationen dazu, wie Sie diese Attribute deklarieren können, finden Sie unter [wie Cmdlet-Parametern deklarieren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4ca27-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="4ca27-112">Jeder Aliasname muss innerhalb eines Cmdlets eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="4ca27-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="4ca27-113">Windows PowerShell führt keine Überprüfung auf doppelte Aliasnamen durch.</span><span class="sxs-lookup"><span data-stu-id="4ca27-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="4ca27-114">Der Alias-Attribut wird einmal für jeden Parameter in einem Cmdlet verwendet.</span><span class="sxs-lookup"><span data-stu-id="4ca27-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="4ca27-115">Der Alias-Attribut wird definiert, durch die [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="4ca27-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ca27-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4ca27-116">See Also</span></span>

[<span data-ttu-id="4ca27-117">Parameteraliase</span><span class="sxs-lookup"><span data-stu-id="4ca27-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="4ca27-118">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4ca27-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
