---
title: Validatepattern-Attribut Deklaration | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369159"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="26986-102">Attributdeklaration: ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="26986-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="26986-103">Das validatepattern-Attribut gibt ein Muster für reguläre Ausdrücke an, das das Argument eines Cmdlet-Parameters überprüft.</span><span class="sxs-lookup"><span data-stu-id="26986-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="26986-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="26986-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="26986-105">Wenn validatepattern innerhalb eines Cmdlets aufgerufen wird, konvertiert Windows PowerShell Runtime das-Argument des Cmdlet-Parameters in eine Zeichenfolge und vergleicht diese Zeichenfolge dann mit dem Muster, das vom validatepattern-Attribut bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="26986-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="26986-106">Das-Cmdlet wird nur ausgeführt, wenn die konvertierte Zeichen folgen Darstellung des Arguments und des angegebenen Musters abgleichen.</span><span class="sxs-lookup"><span data-stu-id="26986-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="26986-107">Wenn Sie nicht identisch sind, wird von der Windows PowerShell-Laufzeit ein Fehler ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="26986-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="26986-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="26986-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="26986-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="26986-109">Parameters</span></span>

<span data-ttu-id="26986-110">`RegexString` ([System. String](/dotnet/api/System.String)) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="26986-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="26986-111">Gibt einen regulären Ausdruck an, der das Parameter Argument überprüft.</span><span class="sxs-lookup"><span data-stu-id="26986-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="26986-112">Optionen ([System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) optionaler benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="26986-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="26986-113">Gibt eine bitweise Kombination von [System. Text. RegularExpressions. RegexOptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -Flags an, die Optionen für reguläre Ausdrücke angeben.</span><span class="sxs-lookup"><span data-stu-id="26986-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="26986-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="26986-114">Remarks</span></span>

- <span data-ttu-id="26986-115">Dieses Attribut kann nur einmal pro Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="26986-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="26986-116">Mit dem `Option`-Parameter des-Attributs können Sie das Muster weiter definieren.</span><span class="sxs-lookup"><span data-stu-id="26986-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="26986-117">Beispielsweise können Sie für das Muster die Groß-/Kleinschreibung beachten.</span><span class="sxs-lookup"><span data-stu-id="26986-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="26986-118">Wenn dieses Attribut auf eine Auflistung angewendet wird, muss jedes Element in der Auflistung mit dem Muster identisch sein.</span><span class="sxs-lookup"><span data-stu-id="26986-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="26986-119">Das validatepattern-Attribut wird von der [System. Management. Automation. validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="26986-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="26986-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="26986-120">See Also</span></span>

[<span data-ttu-id="26986-121">System. Management. Automation. validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="26986-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="26986-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="26986-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
