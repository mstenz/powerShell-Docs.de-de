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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858846"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="24440-102">Überprüfen von Parametereingaben</span><span class="sxs-lookup"><span data-stu-id="24440-102">Validating Parameter Input</span></span>

<span data-ttu-id="24440-103">Windows PowerShell kann es sich um Cmdlet-Parameter auf unterschiedliche Weise übergebenen Argumente überprüfen.</span><span class="sxs-lookup"><span data-stu-id="24440-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="24440-104">Windows PowerShell können die Länge des Bereichs und dem Muster der Zeichen des Arguments überprüfen.</span><span class="sxs-lookup"><span data-stu-id="24440-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="24440-105">Sie können die Anzahl von Argumenten zur Verfügung (Anzahl) überprüfen.</span><span class="sxs-lookup"><span data-stu-id="24440-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="24440-106">Diese Validierungsregeln werden von Validierungsattributen, die deklariert werden mit dem Parameter-Attribut auf öffentlichen Eigenschaften, die von der Cmdlet-Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="24440-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="24440-107">Um ein Parameterargument zu überprüfen, verwendet die Windows PowerShell-Laufzeit die Informationen durch die Validierungsattribute, bestätigen den Wert des Parameters aus, bevor das Cmdlet ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="24440-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="24440-108">Wenn die Parametereingabe nicht gültig ist, erhält der Benutzer eine Fehlermeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="24440-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="24440-109">Jeder Parameter für die Validierung definiert eine Validierungsregel, die von Windows PowerShell erzwungen wird.</span><span class="sxs-lookup"><span data-stu-id="24440-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="24440-110">Windows PowerShell erzwingt die Validierungsregeln, die basierend auf den folgenden Attributen.</span><span class="sxs-lookup"><span data-stu-id="24440-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="24440-111">ValidateCount gibt die minimale und maximale Anzahl von Argumenten, die ein Parameter akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="24440-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="24440-112">Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="24440-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="24440-113">ValidateLength auf gibt die minimale und maximale Anzahl von Zeichen in das Parameterargument.</span><span class="sxs-lookup"><span data-stu-id="24440-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="24440-114">Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [validateLength auf Attributdeklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="24440-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="24440-115">Validatepattern-Element gibt an, einen regulären Ausdruck, der das Parameterargument überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="24440-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="24440-116">Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="24440-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="24440-117">ValidateRange gibt an, die minimalen und maximalen Werte des Parameters-Arguments.</span><span class="sxs-lookup"><span data-stu-id="24440-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="24440-118">Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="24440-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="24440-119">ValidateSet gibt die gültigen Werte für das Parameterargument.</span><span class="sxs-lookup"><span data-stu-id="24440-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="24440-120">Weitere Informationen zu der Syntax verwendet, um dieses Attribut zu deklarieren, finden Sie unter [ValidateSet Attributdeklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="24440-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24440-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="24440-121">See Also</span></span>

[<span data-ttu-id="24440-122">Gewusst wie: Überprüfen der Parametereingabe</span><span class="sxs-lookup"><span data-stu-id="24440-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="24440-123">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="24440-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
