---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="efa8d-102">Registrieren eines PowerShell-Repositorys</span><span class="sxs-lookup"><span data-stu-id="efa8d-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="efa8d-103">Sie können PowerShellGet für interne Repositorys konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="efa8d-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="efa8d-104">Dies erfolgt mithilfe der folgenden Erweiterungen:</span><span class="sxs-lookup"><span data-stu-id="efa8d-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="efa8d-105">Register-PSRepository: Registriert ein Repository für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="efa8d-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="efa8d-106">Unregister-PSRepository: Entfernt ein registriertes Repository für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="efa8d-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="efa8d-107">Set-PSRepository: Legt Werte für ein registriertes Repository fest.</span><span class="sxs-lookup"><span data-stu-id="efa8d-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="efa8d-108">Get-PSRepository: Ruft alle registrierten Repositorys für den aktuellen Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="efa8d-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="efa8d-109">Nachdem ein Repository registriert wurde, können Sie „Find-Module“ und „Install-Module“ dafür verwenden.</span><span class="sxs-lookup"><span data-stu-id="efa8d-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
