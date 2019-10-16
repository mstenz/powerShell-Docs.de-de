---
title: Deklaration der Credential-Attribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369889"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="77cc8-102">Attributdeklaration: Credential</span><span class="sxs-lookup"><span data-stu-id="77cc8-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="77cc8-103">Das Anmelde Informationen-Attribut ist ein optionales Attribut, das mit Anmelde Informations Parametern vom Typ " [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) " verwendet werden kann, sodass eine Zeichenfolge auch als Argument an den-Parameter übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="77cc8-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="77cc8-104">Wenn dieses Attribut einer Parameter Deklaration hinzugefügt wird, konvertiert Windows PowerShell die Zeichen folgen Eingabe in ein [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="77cc8-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="77cc8-105">Beispielsweise verwendet das [Get-Credential-](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) Cmdlet dieses Attribut, damit Windows PowerShell das [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -Objekt generiert, das vom Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="77cc8-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="77cc8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="77cc8-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="77cc8-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="77cc8-107">Remarks</span></span>

- <span data-ttu-id="77cc8-108">In der Regel wird dieses Attribut von Parametern des Typs [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) verwendet, sodass eine Zeichenfolge auch als Argument an den-Parameter übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="77cc8-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="77cc8-109">Wenn ein [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -Objekt an den-Parameter übergeben wird, führt Windows PowerShell keine Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="77cc8-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="77cc8-110">Beim Erstellen des [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -Objekts verwendet Windows PowerShell den aktuellen Host, um dem Benutzer die entsprechenden Eingabe Aufforderungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="77cc8-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="77cc8-111">Der Standard Host zeigt z. b. eine Eingabeaufforderung für einen Benutzernamen und ein Kennwort an, wenn dieses Attribut verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="77cc8-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="77cc8-112">Wenn jedoch ein benutzerdefinierter Host verwendet wird, der eine andere Eingabeaufforderung definiert, wird diese Eingabeaufforderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="77cc8-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="77cc8-113">Dieses Attribut wird mit dem Parameter-Attribut verwendet.</span><span class="sxs-lookup"><span data-stu-id="77cc8-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="77cc8-114">Weitere Informationen zu diesem Attribut finden Sie unter [Parameter Attribut Deklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="77cc8-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="77cc8-115">Das Anmelde Informationen-Attribut wird von der [System. Management. Automation. kredentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="77cc8-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="77cc8-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="77cc8-116">See Also</span></span>

[<span data-ttu-id="77cc8-117">Parameter Aliase</span><span class="sxs-lookup"><span data-stu-id="77cc8-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="77cc8-118">Parameter Attribut Deklaration</span><span class="sxs-lookup"><span data-stu-id="77cc8-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="77cc8-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="77cc8-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
