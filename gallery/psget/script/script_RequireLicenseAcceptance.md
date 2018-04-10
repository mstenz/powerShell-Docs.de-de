---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="39db6-103">Erforderliche Zustimmung zur Lizenz für Skripts</span><span class="sxs-lookup"><span data-stu-id="39db6-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="39db6-104">Das Zustimmen zu Lizenzen wird für Skripts nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39db6-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="39db6-105">Das Szenario, in dem ein Skript von einem Modul abhängt, das die Zustimmung zur Lizenz erfordert, wird jedoch unterstützt.</span><span class="sxs-lookup"><span data-stu-id="39db6-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="39db6-106">Skriptbefehle (Install-Script/Save-Script/Update-Script) unterstützen einen neuen Parameter „-AcceptLicense“, der vorgibt, dass der Benutzer die Lizenz gesehen hat.</span><span class="sxs-lookup"><span data-stu-id="39db6-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="39db6-107">Wenn „-AcceptLicense“ nicht angegeben wird, wird dem Benutzer die Datei „license.txt“ für das abhängige Modul angezeigt, und der Benutzer wird dazu aufgefordert, die Lizenz zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="39db6-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="39db6-108">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="39db6-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="39db6-109">Beispiel 1: Installieren eines Skripts mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern</span><span class="sxs-lookup"><span data-stu-id="39db6-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="39db6-110">Das Skript „ScriptRequireLicenseAcceptance“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="39db6-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="39db6-111">Der Benutzer wird zum Akzeptieren der Lizenz aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="39db6-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="39db6-112">Beispiel 2: Installieren eines Skripts mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern, und -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="39db6-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="39db6-113">Das Skript „ScriptRequireLicenseAcceptance“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="39db6-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="39db6-114">Der Benutzer wird nicht zum Akzeptieren der Lizenz aufgefordert, weil -AcceptLicense angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="39db6-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="39db6-115">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="39db6-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="39db6-116">Unterstützung für das Anfordern der Zustimmung zur Lizenz für Module</span><span class="sxs-lookup"><span data-stu-id="39db6-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="39db6-117">Unterstützung für das Anfordern der Zustimmung zur Lizenz in PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="39db6-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="39db6-118">Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="39db6-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)