---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058011"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="fc7d5-102">Registrieren eines PowerShell-Repositorys</span><span class="sxs-lookup"><span data-stu-id="fc7d5-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="fc7d5-103">Sie können PowerShellGet für interne Repositorys konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="fc7d5-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="fc7d5-104">Dies erfolgt mithilfe der folgenden Erweiterungen:</span><span class="sxs-lookup"><span data-stu-id="fc7d5-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="fc7d5-105">Register-PSRepository: Registriert ein Repository für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="fc7d5-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="fc7d5-106">Unregister-PSRepository: Entfernt ein registriertes Repository für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="fc7d5-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="fc7d5-107">Set-PSRepository: Legt Werte für ein registriertes Repository fest.</span><span class="sxs-lookup"><span data-stu-id="fc7d5-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="fc7d5-108">Get-PSRepository: Ruft alle registrierten Repositorys für den aktuellen Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="fc7d5-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="fc7d5-109">Nachdem ein Repository registriert wurde, können Sie „Find-Module“ und „Install-Module“ dafür verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc7d5-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
