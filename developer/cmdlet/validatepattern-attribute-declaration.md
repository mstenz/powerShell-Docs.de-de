---
title: Deklaration von ValidatePattern-Attribut | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067126"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="5c6ae-102">Attributdeklaration: ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="5c6ae-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="5c6ae-103">Das ValidatePattern-Attribut gibt an, das Muster eines regulären Ausdrucks, das das Argument der Cmdlet-Parameter überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="5c6ae-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="5c6ae-105">Wenn ein Cmdlet validatepattern-Element aufgerufen wird, wird die Windows PowerShell-Laufzeit konvertiert das Argument von der Cmdlet-Parameter in eine Zeichenfolge und vergleicht dann diese Zeichenfolge in das Muster, die durch das ValidatePattern-Attribut angegeben.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="5c6ae-106">Das Cmdlet ausgeführt wird, nur dann, wenn die konvertierte Zeichenfolge-Darstellung des Arguments und dem angegebenen Muster übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="5c6ae-107">Wenn sie nicht übereinstimmen, wird ein Fehler von der Windows PowerShell-Laufzeit ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c6ae-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c6ae-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="5c6ae-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="5c6ae-109">Parameters</span></span>

<span data-ttu-id="5c6ae-110">`RegexString` ([System.String](/dotnet/api/System.String)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="5c6ae-111">Gibt einen regulären Ausdruck, der das Parameterargument überprüft.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="5c6ae-112">Optionen ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="5c6ae-113">Gibt eine bitweise Kombination von [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) Flags, die Optionen für reguläre Ausdrücke angeben.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c6ae-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5c6ae-114">Remarks</span></span>

- <span data-ttu-id="5c6ae-115">Dieses Attribut kann nur einmal pro Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="5c6ae-116">Sie können die `Option` Parameter des Attributs, das Muster genauer zu definieren.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="5c6ae-117">Beispielsweise können Sie die Groß-/ Kleinschreibung des Musters vornehmen.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="5c6ae-118">Wenn dieses Attribut auf eine Auflistung angewendet wird, muss jedes Element in der Auflistung mit dem Muster entsprechen.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="5c6ae-119">Das ValidatePattern-Attribut definiert ist, durch die [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="5c6ae-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c6ae-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5c6ae-120">See Also</span></span>

[<span data-ttu-id="5c6ae-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="5c6ae-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="5c6ae-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="5c6ae-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
