---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptance
ms.openlocfilehash: 260ccc1ee52d09a640e88203c5644f20f9723d6f
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2017
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="3be57-103">Module, die eine Zustimmung zur Lizenz erfordern</span><span class="sxs-lookup"><span data-stu-id="3be57-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="3be57-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="3be57-104">SYNOPSIS</span></span>
<span data-ttu-id="3be57-105">Die Rechtsabteilungen einiger Modulherausgeber verlangen, dass Kunden der Lizenz explizit zustimmen, bevor sie das Modul aus dem PowerShell-Katalog installieren.</span><span class="sxs-lookup"><span data-stu-id="3be57-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="3be57-106">Wenn ein Benutzer ein Modul mit PowerShellGet installiert, aktualisiert oder speichert (entweder direkt oder in Abhängigkeit von einem anderen Element) und dieses Modul die Zustimmung zu einer Lizenz erforderlich macht, muss der Benutzer die Lizenzbedingungen annehmen, da der Vorgang andernfalls nicht durchgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3be57-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="3be57-107">Veröffentlichungsanforderungen für Module</span><span class="sxs-lookup"><span data-stu-id="3be57-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="3be57-108">Module, für die die Benutzer einer Lizenz zustimmen sollen, müssen folgende Anforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="3be57-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>
    
- <span data-ttu-id="3be57-109">Der PSData-Abschnitt des Modulmanifests muss „RequireLicenseAcceptance = $True“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="3be57-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="3be57-110">Das Stammverzeichnis des Moduls muss die Datei „license.txt“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="3be57-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="3be57-111">Das Modulmanifest muss den Lizenz-URI enthalten.</span><span class="sxs-lookup"><span data-stu-id="3be57-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="3be57-112">Das Modul muss mit PowerShellGet Format, Version 2.0 und höher, veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="3be57-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="3be57-113">Auswirkungen auf „Install-Module“, „Save-Module“ und „Update-Module“</span><span class="sxs-lookup"><span data-stu-id="3be57-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="3be57-114">Die Cmdlets „Install“, „Save“ und „Update“ unterstützen den neuen Parameter „AcceptLicense“, der vorgibt, dass der Benutzer die Lizenz gesehen hat.</span><span class="sxs-lookup"><span data-stu-id="3be57-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="3be57-115">Wenn „RequiredLicenseAcceptance“ TRUE lautet und „–AcceptLicense“ nicht angegeben ist, werden dem Benutzer die Datei „license.txt“ und die folgende Meldung angezeigt: &quot;Akzeptieren Sie diese Lizenzbedingungen (Yes/No/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="3be57-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="3be57-116">Bei Zustimmung zur Lizenz</span><span class="sxs-lookup"><span data-stu-id="3be57-116">If the license is accepted</span></span>
    - <span data-ttu-id="3be57-117">**Save-Module:** Das Modul wird auf das System des Benutzers kopiert.</span><span class="sxs-lookup"><span data-stu-id="3be57-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="3be57-118">**Install-Module:** Das Modul wird (basierend auf dem Bereich) in den richtigen Ordner auf dem System des Benutzers kopiert.</span><span class="sxs-lookup"><span data-stu-id="3be57-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="3be57-119">**Update-Module:** Das Modul wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3be57-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="3be57-120">Bei Ablehnung der Lizenz.</span><span class="sxs-lookup"><span data-stu-id="3be57-120">If the license is declined.</span></span> 
    - <span data-ttu-id="3be57-121">Der Vorgang wird abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="3be57-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="3be57-122">Alle Cmdlets suchen nach den Metadaten (requireLicenseAcceptance und Formatversion), die besagen, dass eine Zustimmung zur Lizenz erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="3be57-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="3be57-123">Wenn die Formatversion des Clients älter als 2.0 ist, verursacht der Vorgang einen Fehler, und der Benutzer wird zum Aktualisieren des Clients aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="3be57-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="3be57-124">Wenn das Modul mit einer älteren Formatversion als 2.0 veröffentlicht wurde, wird das Flag „requireLicenseAcceptance“ ignoriert.</span><span class="sxs-lookup"><span data-stu-id="3be57-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

    
 ## <a name="module-dependencies"></a><span data-ttu-id="3be57-125">Modulabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="3be57-125">Module Dependencies</span></span>
- <span data-ttu-id="3be57-126">Während des Vorgangs zum Installieren/Speichern/Aktualisieren ist das obige Lizenzzustimmungsverhalten erforderlich, falls ein abhängiges Modul (ein anderes vom Modul abhängiges Element) die Zustimmung zur Lizenz verlangt.</span><span class="sxs-lookup"><span data-stu-id="3be57-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="3be57-127">Wenn die Modulversion im lokalen Katalog bereits als auf dem System installiert aufgeführt ist, wird die Lizenzüberprüfung umgangen.</span><span class="sxs-lookup"><span data-stu-id="3be57-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="3be57-128">Wenn ein abhängiges Modul beim Vorgang zum Installieren/Speichern/Aktualisieren eine Lizenz benötigt und keine Zustimmung zur Lizenz erfolgt, verursacht der Vorgang einen Fehler und befolgt die normalen Prozesse für das Element, das nicht installiert, gespeichert oder aktualisiert werden konnte.</span><span class="sxs-lookup"><span data-stu-id="3be57-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="3be57-129">Auswirkungen auf -Force</span><span class="sxs-lookup"><span data-stu-id="3be57-129">Impact on -Force</span></span>

<span data-ttu-id="3be57-130">Die Angabe von „–Force“ reicht zum Akzeptieren einer Lizenz NICHT aus.</span><span class="sxs-lookup"><span data-stu-id="3be57-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="3be57-131">–AcceptLicense ist für die Berechtigung zum Installieren erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3be57-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="3be57-132">Wenn „–Force“ angegeben wird, RequiredLicenseAcceptance TRUE lautet und „–AcceptLicense“ NICHT angegeben ist, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="3be57-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="3be57-133">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="3be57-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="3be57-134">Beispiel 1: Aktualisieren des Modulmanifests zum Anfordern der Zustimmung zur Lizenz</span><span class="sxs-lookup"><span data-stu-id="3be57-134">Example 1: Update Module Manifest to require license acceptance</span></span>
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable
    
 } # End of PrivateData hashtable
```
<span data-ttu-id="3be57-135">Dieser Befehl aktualisiert die Manifestdatei und legt das RequireLicenseAcceptance-Flag auf TRUE fest.</span><span class="sxs-lookup"><span data-stu-id="3be57-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>
### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="3be57-136">Beispiel 2: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="3be57-136">Example 2: Install Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 

```
<span data-ttu-id="3be57-137">Dieser Befehl zeigt die Lizenz aus der Datei „license.txt“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="3be57-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="3be57-138">Beispiel 3: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3be57-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="3be57-139">Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz installiert.</span><span class="sxs-lookup"><span data-stu-id="3be57-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="3be57-140">Beispiel 4: Installieren eines Moduls, das die Zustimmung zur Lizenz mit -Force erfordert</span><span class="sxs-lookup"><span data-stu-id="3be57-140">Example 4: Install Module requiring license acceptance with -Force</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="3be57-141">Beispiel 5: Installieren eines Moduls mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern</span><span class="sxs-lookup"><span data-stu-id="3be57-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>
<span data-ttu-id="3be57-142">Das Modul „ModuleWithDependency“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="3be57-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="3be57-143">Der Benutzer wird zum Akzeptieren der Lizenz aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="3be57-143">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="3be57-144">Beispiel 6: Installieren eines Moduls mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern, und -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3be57-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="3be57-145">Das Modul „ModuleWithDependency“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="3be57-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="3be57-146">Der Benutzer wird nicht zum Akzeptieren der Lizenz aufgefordert, weil -AcceptLicense angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="3be57-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="3be57-147">Beispiel 7: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, auf einem Client, der eine ältere Version als PSGetFormatVersion 2.0 ausführt</span><span class="sxs-lookup"><span data-stu-id="3be57-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="3be57-148">Beispiel 8: Speichern eines Moduls, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="3be57-148">Example 8: Save Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```
<span data-ttu-id="3be57-149">Dieser Befehl zeigt die Lizenz aus der Datei „license.txt“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="3be57-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="3be57-150">Beispiel 9: Speichern eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3be57-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
<span data-ttu-id="3be57-151">Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz gespeichert.</span><span class="sxs-lookup"><span data-stu-id="3be57-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="3be57-152">Beispiel 10: Aktualisieren eines Moduls, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="3be57-152">Example 10: Update Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```
<span data-ttu-id="3be57-153">Dieser Befehl zeigt die Lizenz aus der Datei „license.txt“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="3be57-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="3be57-154">Beispiel 11: Aktualisieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3be57-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="3be57-155">Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3be57-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="3be57-156">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="3be57-156">More details</span></span>
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[<span data-ttu-id="3be57-157">Erforderliche Zustimmung zur Lizenz für Skripts</span><span class="sxs-lookup"><span data-stu-id="3be57-157">Require License Acceptance for Scripts</span></span>](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="3be57-158">Unterstützung für das Anfordern der Zustimmung zur Lizenz in PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="3be57-158">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="3be57-159">Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="3be57-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
