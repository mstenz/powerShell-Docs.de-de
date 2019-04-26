---
title: Überprüfen der Parametereingabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067143"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="0cf94-102">Überprüfen von Parametereingaben</span><span class="sxs-lookup"><span data-stu-id="0cf94-102">Validating Parameter Input</span></span>

<span data-ttu-id="0cf94-103">PowerShell kann es sich um Cmdlet-Parameter auf unterschiedliche Weise übergebenen Argumente überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0cf94-103">PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span>
<span data-ttu-id="0cf94-104">PowerShell kann es sich um die Länge des Bereichs und dem Muster der Zeichen des Arguments überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0cf94-104">PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span>
<span data-ttu-id="0cf94-105">Sie können die Anzahl von Argumenten zur Verfügung (Anzahl) überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0cf94-105">It can validate the number of arguments available (the count).</span></span>
<span data-ttu-id="0cf94-106">Diese Validierungsregeln werden von Validierungsattributen, die deklariert werden mit dem Parameter-Attribut auf öffentlichen Eigenschaften, die von der Cmdlet-Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="0cf94-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="0cf94-107">Um ein Parameterargument zu überprüfen, verwendet die PowerShell-Laufzeit die Informationen durch die Validierungsattribute, bestätigen den Wert des Parameters aus, bevor das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0cf94-107">To validate a parameter argument, the PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span>
<span data-ttu-id="0cf94-108">Wenn die Parametereingabe nicht gültig ist, erhält der Benutzer eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0cf94-108">If the parameter input is not valid, the user receives an error message.</span></span>
<span data-ttu-id="0cf94-109">Jeder Parameter für die Validierung definiert eine Validierungsregel, die von PowerShell erzwungen wird.</span><span class="sxs-lookup"><span data-stu-id="0cf94-109">Each validation parameter defines a validation rule that is enforced by PowerShell.</span></span>

<span data-ttu-id="0cf94-110">PowerShell erzwingt die Validierungsregeln, die basierend auf den folgenden Attributen.</span><span class="sxs-lookup"><span data-stu-id="0cf94-110">PowerShell enforces the validation rules based on the following attributes.</span></span>

### <a name="validatecount"></a><span data-ttu-id="0cf94-111">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="0cf94-111">ValidateCount</span></span>

<span data-ttu-id="0cf94-112">Gibt die minimale und maximale Anzahl von Argumenten, die ein Parameter akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="0cf94-112">Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span>
<span data-ttu-id="0cf94-113">Weitere Informationen finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0cf94-113">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="0cf94-114">ValidateLength auf</span><span class="sxs-lookup"><span data-stu-id="0cf94-114">ValidateLength</span></span>

<span data-ttu-id="0cf94-115">Gibt die minimale und maximale Anzahl der Zeichen im Parameterargument.</span><span class="sxs-lookup"><span data-stu-id="0cf94-115">Specifies the minimum and maximum number of characters in the parameter argument.</span></span>
<span data-ttu-id="0cf94-116">Weitere Informationen finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0cf94-116">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="0cf94-117">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="0cf94-117">ValidatePattern</span></span>

<span data-ttu-id="0cf94-118">Gibt einen regulären Ausdruck, der das Parameterargument überprüft.</span><span class="sxs-lookup"><span data-stu-id="0cf94-118">Specifies a regular expression that validates the parameter argument.</span></span>
<span data-ttu-id="0cf94-119">Weitere Informationen finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0cf94-119">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="0cf94-120">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="0cf94-120">ValidateRange</span></span>

<span data-ttu-id="0cf94-121">Gibt die minimalen und maximalen Werte des Parameters-Arguments.</span><span class="sxs-lookup"><span data-stu-id="0cf94-121">Specifies the minimum and maximum values of the parameter argument.</span></span>
<span data-ttu-id="0cf94-122">Weitere Informationen finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0cf94-122">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="0cf94-123">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="0cf94-123">ValidateSet</span></span>

<span data-ttu-id="0cf94-124">Gibt die gültigen Werte für das Parameterargument.</span><span class="sxs-lookup"><span data-stu-id="0cf94-124">Specifies the valid values for the parameter argument.</span></span>
<span data-ttu-id="0cf94-125">Weitere Informationen finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0cf94-125">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cf94-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0cf94-126">See Also</span></span>

[<span data-ttu-id="0cf94-127">Gewusst wie: Überprüfen der Parametereingabe</span><span class="sxs-lookup"><span data-stu-id="0cf94-127">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="0cf94-128">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0cf94-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
