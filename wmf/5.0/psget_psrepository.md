---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="61ace-102">Registrieren eines PowerShell-Repositorys</span><span class="sxs-lookup"><span data-stu-id="61ace-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="61ace-103">Sie können PowerShellGet für interne Repositorys konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="61ace-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="61ace-104">Dies erfolgt mithilfe der folgenden Erweiterungen:</span><span class="sxs-lookup"><span data-stu-id="61ace-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="61ace-105">Register-PSRepository: Registriert ein Repository für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="61ace-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="61ace-106">Unregister-PSRepository: Entfernt ein registriertes Repository für den aktuellen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="61ace-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="61ace-107">Set-PSRepository: Legt Werte für ein registriertes Repository fest.</span><span class="sxs-lookup"><span data-stu-id="61ace-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="61ace-108">Get-PSRepository: Ruft alle registrierten Repositorys für den aktuellen Benutzer ab.</span><span class="sxs-lookup"><span data-stu-id="61ace-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="61ace-109">Nachdem ein Repository registriert wurde, können Sie „Find-Module“ und „Install-Module“ dafür verwenden.</span><span class="sxs-lookup"><span data-stu-id="61ace-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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