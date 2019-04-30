---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Erforderliche Zustimmung zur Lizenz für Skripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084673"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="77ffc-103">Erforderliche Zustimmung zur Lizenz für Skripts</span><span class="sxs-lookup"><span data-stu-id="77ffc-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="77ffc-104">Das Zustimmen zu Lizenzen wird für Skripts nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="77ffc-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="77ffc-105">Das Szenario, in dem ein Skript von einem Modul abhängt, das die Zustimmung zur Lizenz erfordert, wird jedoch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="77ffc-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="77ffc-106">Skriptbefehle (Install-Script/Save-Script/Update-Script) unterstützen einen neuen Parameter „-AcceptLicense“, der vorgibt, dass der Benutzer die Lizenz gesehen hat.</span><span class="sxs-lookup"><span data-stu-id="77ffc-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="77ffc-107">Wenn „-AcceptLicense“ nicht angegeben wird, wird dem Benutzer die Datei „license.txt“ für das abhängige Modul angezeigt, und der Benutzer wird dazu aufgefordert, die Lizenz zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="77ffc-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="77ffc-108">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="77ffc-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="77ffc-109">Beispiel 1: Installieren eines Skripts mit Abhängigkeiten, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="77ffc-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="77ffc-110">Das Skript „ScriptRequireLicenseAcceptance“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="77ffc-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="77ffc-111">Der Benutzer wird zum Akzeptieren der Lizenz aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="77ffc-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="77ffc-112">Beispiel 2: Installieren eines Skripts mit Abhängigkeiten, das die Zustimmung zur Lizenz und -AcceptLicense erfordert</span><span class="sxs-lookup"><span data-stu-id="77ffc-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="77ffc-113">Das Skript „ScriptRequireLicenseAcceptance“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="77ffc-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="77ffc-114">Der Benutzer wird nicht zum Akzeptieren der Lizenz aufgefordert, weil -AcceptLicense angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="77ffc-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="77ffc-115">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="77ffc-115">More details</span></span>

- [<span data-ttu-id="77ffc-116">Unterstützung für das Anfordern der Zustimmung zur Lizenz für Module</span><span class="sxs-lookup"><span data-stu-id="77ffc-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="77ffc-117">Unterstützung für das Anfordern der Zustimmung zur Lizenz in PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="77ffc-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="77ffc-118">Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="77ffc-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
