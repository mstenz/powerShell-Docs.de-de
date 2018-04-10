---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a><span data-ttu-id="97f6a-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="97f6a-103">Unregister-PSRepository</span></span>

<span data-ttu-id="97f6a-104">Hebt die Registrierung eines Repositorys auf</span><span class="sxs-lookup"><span data-stu-id="97f6a-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="97f6a-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="97f6a-105">Description</span></span>

<span data-ttu-id="97f6a-106">Das Cmdlet „Unregister-PSRepository“ hebt die Registrierung für ein Repository für den aktuellen Benutzer auf.</span><span class="sxs-lookup"><span data-stu-id="97f6a-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="97f6a-107">Das Aufheben der Registrierung und das erneute Registrieren des Repositorys „PSGallery“ ist für ein Großunternehmen und getrennte Szenarios zulässig.</span><span class="sxs-lookup"><span data-stu-id="97f6a-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="97f6a-108">Benutzer können die PSGallery erneut registrieren, indem sie einfach `Register-PSRepository -Default` ausführen.</span><span class="sxs-lookup"><span data-stu-id="97f6a-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="97f6a-109">Da PSGallery das Standard-Veröffentlichungsrepository in den Cmdlets „Publish-Module“ und „Publish-Script“ ist, wird ein Fehler ausgegeben, wenn PSGallery in der Liste der registrierten Repositorys nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="97f6a-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="97f6a-110">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="97f6a-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="97f6a-111">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="97f6a-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="97f6a-112">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="97f6a-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="97f6a-113">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="97f6a-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="97f6a-114">Das Aufheben der Registrierung und das erneute Registrieren des Repositorys „PSGallery“ ist für ein Großunternehmen und getrennte Szenarios zulässig.</span><span class="sxs-lookup"><span data-stu-id="97f6a-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```