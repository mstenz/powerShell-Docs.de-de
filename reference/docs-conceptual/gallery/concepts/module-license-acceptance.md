---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Module, die eine Zustimmung zur Lizenz erfordern
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328521"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="2762f-103">Module, die eine Zustimmung zur Lizenz erfordern</span><span class="sxs-lookup"><span data-stu-id="2762f-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="2762f-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="2762f-104">SYNOPSIS</span></span>

<span data-ttu-id="2762f-105">Die Rechtsabteilungen einiger Modulherausgeber verlangen, dass Kunden der Lizenz explizit zustimmen, bevor sie das Modul aus dem PowerShell-Katalog installieren.</span><span class="sxs-lookup"><span data-stu-id="2762f-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="2762f-106">Wenn ein Benutzer ein Modul mit PowerShellGet installiert, aktualisiert oder speichert (entweder direkt oder in Abhängigkeit von einem anderen Paket) und dieses Modul erfordert, dass der Benutzer einer Lizenz zustimmt, muss der Benutzer die Lizenzbedingungen akzeptieren, da der Vorgang sonst fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="2762f-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="2762f-107">Veröffentlichungsanforderungen für Module</span><span class="sxs-lookup"><span data-stu-id="2762f-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="2762f-108">Module, für die die Benutzer einer Lizenz zustimmen sollen, müssen folgende Anforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="2762f-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="2762f-109">Der PSData-Abschnitt des Modulmanifests muss „RequireLicenseAcceptance = $True“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="2762f-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="2762f-110">Das Stammverzeichnis des Moduls muss die Datei „license.txt“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="2762f-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="2762f-111">Das Modulmanifest muss den Lizenz-URI enthalten.</span><span class="sxs-lookup"><span data-stu-id="2762f-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="2762f-112">Das Modul muss mit PowerShellGet Format, Version 2.0 und höher, veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="2762f-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="2762f-113">Auswirkungen auf „Install-Module“, „Save-Module“ und „Update-Module“</span><span class="sxs-lookup"><span data-stu-id="2762f-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="2762f-114">Die Cmdlets „Install“, „Save“ und „Update“ unterstützen den neuen Parameter „AcceptLicense“, der vorgibt, dass der Benutzer die Lizenz gesehen hat.</span><span class="sxs-lookup"><span data-stu-id="2762f-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="2762f-115">Wenn „RequiredLicenseAcceptance“ TRUE lautet und „–AcceptLicense“ nicht angegeben ist, werden dem Benutzer die Datei „license.txt“ und die folgende Meldung angezeigt: &quot;Akzeptieren Sie diese Lizenzbedingungen (Yes/No/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="2762f-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="2762f-116">Bei Zustimmung zur Lizenz</span><span class="sxs-lookup"><span data-stu-id="2762f-116">If the license is accepted</span></span>
    - <span data-ttu-id="2762f-117">**Save-Module:** Das Modul wird auf das System des Benutzers kopiert.</span><span class="sxs-lookup"><span data-stu-id="2762f-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="2762f-118">**Install-Module:** Das Modul wird (basierend auf dem Bereich) in den richtigen Ordner auf dem System des Benutzers kopiert.</span><span class="sxs-lookup"><span data-stu-id="2762f-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="2762f-119">**Update-Module:** Das Modul wird aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="2762f-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="2762f-120">Bei Ablehnung der Lizenz.</span><span class="sxs-lookup"><span data-stu-id="2762f-120">If the license is declined.</span></span>
    - <span data-ttu-id="2762f-121">Der Vorgang wird abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="2762f-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="2762f-122">Alle Cmdlets suchen nach den Metadaten (requireLicenseAcceptance und Formatversion), die besagen, dass eine Zustimmung zur Lizenz erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="2762f-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="2762f-123">Wenn die Formatversion des Clients älter als 2.0 ist, verursacht der Vorgang einen Fehler, und der Benutzer wird zum Aktualisieren des Clients aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="2762f-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="2762f-124">Wenn das Modul mit einer älteren Formatversion als 2.0 veröffentlicht wurde, wird das Flag „requireLicenseAcceptance“ ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2762f-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="2762f-125">Modulabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="2762f-125">Module Dependencies</span></span>

- <span data-ttu-id="2762f-126">Während des Vorgangs zum Installieren/Speichern/Aktualisieren ist das obige Lizenzzustimmungsverhalten erforderlich, falls ein abhängiges Modul (ein anderes vom Modul abhängiges Element) die Zustimmung zur Lizenz verlangt.</span><span class="sxs-lookup"><span data-stu-id="2762f-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="2762f-127">Wenn die Modulversion im lokalen Katalog bereits als auf dem System installiert aufgeführt ist, wird die Lizenzüberprüfung umgangen.</span><span class="sxs-lookup"><span data-stu-id="2762f-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="2762f-128">Wenn ein abhängiges Modul beim Installieren/Speichern/Aktualisieren eine Lizenz benötigt und die Zustimmung zur Lizenz nicht erfolgt, schlägt der Vorgang fehl und folgt den normalen Prozessen für das Paket, das nicht installiert/gespeichert/aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="2762f-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="2762f-129">Auswirkungen auf -Force</span><span class="sxs-lookup"><span data-stu-id="2762f-129">Impact on -Force</span></span>

<span data-ttu-id="2762f-130">Die Angabe von `–Force` reicht zum Akzeptieren einer Lizenz NICHT aus.</span><span class="sxs-lookup"><span data-stu-id="2762f-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="2762f-131">`–AcceptLicense` ist für die Berechtigung zum Installieren erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2762f-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="2762f-132">Wenn `–Force` angegeben wird, RequiredLicenseAcceptance „True“ lautet und `–AcceptLicense` NICHT angegeben ist, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="2762f-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="2762f-133">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="2762f-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="2762f-134">Beispiel 1: Aktualisieren des Modulmanifests zum Anfordern der Zustimmung zur Lizenz</span><span class="sxs-lookup"><span data-stu-id="2762f-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="2762f-135">Dieser Befehl aktualisiert die Manifestdatei und legt das RequireLicenseAcceptance-Flag auf TRUE fest.</span><span class="sxs-lookup"><span data-stu-id="2762f-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="2762f-136">Beispiel 2: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="2762f-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="2762f-137">Dieser Befehl zeigt die Lizenz aus der Datei „license.txt“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="2762f-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="2762f-138">Beispiel 3: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2762f-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="2762f-139">Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz installiert.</span><span class="sxs-lookup"><span data-stu-id="2762f-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="2762f-140">Beispiel 4: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -Force</span><span class="sxs-lookup"><span data-stu-id="2762f-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="2762f-141">Beispiel 5: Installieren eines Moduls mit Abhängigkeiten, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="2762f-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="2762f-142">Das Modul „ModuleWithDependency“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="2762f-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="2762f-143">Der Benutzer wird zum Akzeptieren der Lizenz aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="2762f-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="2762f-144">Beispiel 6: Installieren eines Moduls mit Abhängigkeiten, das die Zustimmung zur Lizenz und -AcceptLicense erfordert</span><span class="sxs-lookup"><span data-stu-id="2762f-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="2762f-145">Das Modul „ModuleWithDependency“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab.</span><span class="sxs-lookup"><span data-stu-id="2762f-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="2762f-146">Der Benutzer wird nicht zum Akzeptieren der Lizenz aufgefordert, weil -AcceptLicense angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="2762f-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="2762f-147">Beispiel 7: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, auf einem Client, der eine ältere Version als PSGetFormatVersion 2.0 ausführt</span><span class="sxs-lookup"><span data-stu-id="2762f-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="2762f-148">Beispiel 8: Speichern eines Moduls, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="2762f-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
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

<span data-ttu-id="2762f-149">Dieser Befehl zeigt die Lizenz aus der Datei „license.txt“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="2762f-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="2762f-150">Beispiel 9: Speichern eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2762f-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="2762f-151">Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2762f-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="2762f-152">Beispiel 10: Aktualisieren eines Moduls, das die Zustimmung zur Lizenz erfordert</span><span class="sxs-lookup"><span data-stu-id="2762f-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="2762f-153">Dieser Befehl zeigt die Lizenz aus der Datei „license.txt“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="2762f-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="2762f-154">Beispiel 11: Aktualisieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2762f-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="2762f-155">Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="2762f-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="2762f-156">Weitere Details</span><span class="sxs-lookup"><span data-stu-id="2762f-156">More details</span></span>

[<span data-ttu-id="2762f-157">Erforderliche Zustimmung zur Lizenz für Skripts</span><span class="sxs-lookup"><span data-stu-id="2762f-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="2762f-158">Unterstützung für das Anfordern der Zustimmung zur Lizenz in PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="2762f-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="2762f-159">Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2762f-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
