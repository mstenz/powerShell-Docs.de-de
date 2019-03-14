---
title: Anmeldeinformationen Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 1513d340cdadc5cb7622e791cc3c163ff39dfe1d
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795401"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="f9936-102">Attributdeklaration: Credential</span><span class="sxs-lookup"><span data-stu-id="f9936-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="f9936-103">Die Anmeldeinformationen-Attribut ist ein optionales Attribut, das mit dem Credential-Parameter des Typs verwendet werden kann [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) , damit eine Zeichenfolge auch als Argument an den Parameter übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="f9936-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="f9936-104">Wenn dieses Attribut auf eine Parameterdeklaration hinzugefügt wird, konvertiert Windows PowerShell die Zeichenfolgeneingabe in einem [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) Objekt.</span><span class="sxs-lookup"><span data-stu-id="f9936-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="f9936-105">Z. B. die [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) Cmdlet verwendet dieses Attribut Generieren von Windows PowerShell werden der [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) -Objekt, das vom Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f9936-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9936-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9936-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="f9936-107">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f9936-107">Remarks</span></span>

- <span data-ttu-id="f9936-108">Dieses Attribut wird in der Regel verwendet, durch die Parameter des Typs [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) , damit eine Zeichenfolge auch als Argument an den Parameter übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="f9936-108">Typically this attribute is used by parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="f9936-109">Wenn eine [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) Objekt wird an den Parameter übergeben, die Windows PowerShell führt keine Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="f9936-109">When a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="f9936-110">Beim Erstellen der [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) Objekt ist, wird Windows PowerShell den aktuellen Host verwendet, um die entsprechenden Anweisungen für den Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f9936-110">When creating the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="f9936-111">Beispielsweise zeigt den Standardwert Host eine Eingabeaufforderung für einen Benutzernamen und ein Kennwort, wenn dieses Attribut verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f9936-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="f9936-112">Jedoch wenn Sie ein benutzerdefinierter Host verwendet wird, die eine andere Eingabeaufforderung definiert, und Sie würden diese Aufforderung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f9936-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="f9936-113">Dieses Attribut wird mit dem Parameter-Attribut verwendet.</span><span class="sxs-lookup"><span data-stu-id="f9936-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="f9936-114">Weitere Informationen zu diesem Attribut finden Sie unter [Parameter Attributdeklaration](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f9936-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="f9936-115">Das Credential-Attribut definiert ist, durch die [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="f9936-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9936-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f9936-116">See Also</span></span>

[<span data-ttu-id="f9936-117">Parameteraliase</span><span class="sxs-lookup"><span data-stu-id="f9936-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="f9936-118">Parameterdeklaration-Attribut</span><span class="sxs-lookup"><span data-stu-id="f9936-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="f9936-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f9936-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
