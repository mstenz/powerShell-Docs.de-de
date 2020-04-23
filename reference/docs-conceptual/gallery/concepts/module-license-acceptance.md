---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Module, die eine Zustimmung zur Lizenz erfordern
ms.openlocfilehash: a2f7ed72aae8579a6723f65b86dd0993f1a22afd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80082809"
---
# <a name="modules-requiring-license-acceptance"></a>Module, die eine Zustimmung zur Lizenz erfordern

## <a name="synopsis"></a>ZUSAMMENFASSUNG

Die Rechtsabteilungen einiger Modulherausgeber verlangen, dass Kunden der Lizenz explizit zustimmen, bevor sie das Modul aus dem PowerShell-Katalog installieren. Wenn ein Benutzer ein Modul mit PowerShellGet installiert, aktualisiert oder speichert (entweder direkt oder in Abhängigkeit von einem anderen Paket) und dieses Modul erfordert, dass der Benutzer einer Lizenz zustimmt, muss der Benutzer die Lizenzbedingungen akzeptieren, da der Vorgang sonst fehlschlägt.

## <a name="publish-requirements-for-modules"></a>Veröffentlichungsanforderungen für Module

Module, für die die Benutzer einer Lizenz zustimmen sollen, müssen folgende Anforderungen erfüllen:

- Der PSData-Abschnitt des Modulmanifests muss „RequireLicenseAcceptance = $True“ enthalten.
- Das Stammverzeichnis des Moduls muss die Datei „license.txt“ enthalten.
- Das Modulmanifest muss den Lizenz-URI enthalten.
- Das Modul muss mit PowerShellGet Format, Version 2.0 und höher, veröffentlicht werden.

## <a name="impact-on-installsaveupdate-module"></a>Auswirkungen auf „Install-Module“, „Save-Module“ und „Update-Module“

- Die Cmdlets „Install“, „Save“ und „Update“ unterstützen den neuen Parameter **AcceptLicense**, der vorgibt, dass der Benutzer die Lizenz gesehen hat.
- Wenn **RequiredLicenseAcceptance** TRUE lautet und **AcceptLicense** nicht angegeben ist, werden dem Benutzer die Datei „`license.txt`“ und die folgende Meldung angezeigt: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.
  - Bei Zustimmung zur Lizenz
    - **Save-Module:** Das Modul wird auf das System des Benutzers kopiert.
    - **Install-Module:** Das Modul wird (basierend auf dem Bereich) in den richtigen Ordner auf dem System des Benutzers kopiert.
    - **Update-Module:** Das Modul wird aktualisiert.
  - Bei Ablehnung der Lizenz.
    - Vorgang wurde abgebrochen.
    - Alle Cmdlets suchen nach den Metadaten (**requireLicenseAcceptance** und Formatversion), die besagen, dass eine Zustimmung zur Lizenz erforderlich ist.
    - Wenn die Formatversion des Clients älter als 2.0 ist, verursacht der Vorgang einen Fehler, und der Benutzer wird zum Aktualisieren des Clients aufgefordert.
    - Wenn das Modul mit einer älteren Formatversion als 2.0 veröffentlicht wurde, wird das Flag „requireLicenseAcceptance“ ignoriert.

## <a name="module-dependencies"></a>Modulabhängigkeiten

- Während des Vorgangs zum Installieren/Speichern/Aktualisieren ist das obige Lizenzzustimmungsverhalten erforderlich, falls ein abhängiges Modul (ein anderes vom Modul abhängiges Element) die Zustimmung zur Lizenz verlangt.
- Wenn die Modulversion im lokalen Katalog bereits als auf dem System installiert aufgeführt ist, wird die Lizenzüberprüfung umgangen.
- Wenn ein abhängiges Modul beim Installieren/Speichern/Aktualisieren eine Lizenz benötigt und die Zustimmung zur Lizenz nicht erfolgt, verursacht der Vorgang einen Fehler und folgt den normalen Prozessen für das Paket, das nicht installiert/gespeichert/aktualisiert werden kann.

## <a name="impact-on--force"></a>Auswirkungen auf -Force

Die Angabe von `–Force` reicht zum Akzeptieren einer Lizenz NICHT aus. `–AcceptLicense` ist für die Berechtigung zum Installieren erforderlich. Wenn `–Force` angegeben wird, RequiredLicenseAcceptance TRUE lautet und `–AcceptLicense` NICHT angegeben ist, tritt ein Fehler auf.

## <a name="examples"></a>BEISPIELE

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Beispiel 1: Aktualisieren des Modulmanifests zum Anfordern der Zustimmung zur Lizenz

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Dieser Befehl aktualisiert die Manifestdatei und legt das RequireLicenseAcceptance-Flag auf TRUE fest.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Beispiel 2: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
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

Dieser Befehl zeigt die Lizenz aus der Datei „`license.txt`“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Beispiel 3: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz installiert.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Beispiel 4: Installieren eines Moduls, das die Zustimmung zur Lizenz mit -Force erfordert

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```Output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Beispiel 5: Installieren eines Moduls mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern

Das Modul **ModuleWithDependency** hängt vom Modul **ModuleRequireLicenseAcceptance** ab. Der Benutzer wird zum Akzeptieren der Lizenz aufgefordert.

```powershell
Install-Module -Name ModuleWithDependency
```

```Output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Beispiel 6: Installieren eines Moduls mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern, und -AcceptLicense

Das Modul **ModuleWithDependency** hängt vom Modul **ModuleRequireLicenseAcceptance** ab. Der Benutzer wird nicht zum Akzeptieren der Lizenz aufgefordert, weil **AcceptLicense** angegeben wurde.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Beispiel 7: Installieren eines Moduls, das die Zustimmung zur Lizenz erfordert, auf einem Client, der eine ältere Version als PSGetFormatVersion 2.0 ausführt

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Beispiel 8: Speichern eines Moduls, das die Zustimmung zur Lizenz erfordert

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```Output
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

Dieser Befehl zeigt die Lizenz aus der Datei „`license.txt`“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Beispiel 9: Speichern eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz gespeichert.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Beispiel 10: Aktualisieren eines Moduls, das die Zustimmung zur Lizenz erfordert

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```Output
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

Dieser Befehl zeigt die Lizenz aus der Datei „`license.txt`“ an und fordert den Benutzer auf, die Lizenzbedingungen zu akzeptieren.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Beispiel 11: Aktualisieren eines Moduls, das die Zustimmung zur Lizenz erfordert, mit -AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Das Modul wird ohne Aufforderung zum Akzeptieren der Lizenz aktualisiert.

## <a name="more-details"></a>Weitere Informationen

[Erforderliche Zustimmung zur Lizenz für Skripts](./script-license-acceptance.md)

[Unterstützung für das Anfordern der Zustimmung zur Lizenz in PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
