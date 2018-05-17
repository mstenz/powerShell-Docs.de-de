---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Erforderliche Zustimmung zur Lizenz für Skripts
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a>Erforderliche Zustimmung zur Lizenz für Skripts

Das Zustimmen zu Lizenzen wird für Skripts nicht unterstützt. Das Szenario, in dem ein Skript von einem Modul abhängt, das die Zustimmung zur Lizenz erfordert, wird jedoch unterstützt.

Skriptbefehle (Install-Script/Save-Script/Update-Script) unterstützen einen neuen Parameter „-AcceptLicense“, der vorgibt, dass der Benutzer die Lizenz gesehen hat. Wenn „-AcceptLicense“ nicht angegeben wird, wird dem Benutzer die Datei „license.txt“ für das abhängige Modul angezeigt, und der Benutzer wird dazu aufgefordert, die Lizenz zu akzeptieren.

## <a name="examples"></a>BEISPIELE

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Beispiel 1: Installieren eines Skripts mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern

Das Skript „ScriptRequireLicenseAcceptance“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab. Der Benutzer wird zum Akzeptieren der Lizenz aufgefordert.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Beispiel 2: Installieren eines Skripts mit Abhängigkeiten, die die Zustimmung zur Lizenz erfordern, und -AcceptLicense

Das Skript „ScriptRequireLicenseAcceptance“ hängt vom Modul „ModuleRequireLicenseAcceptance“ ab. Der Benutzer wird nicht zum Akzeptieren der Lizenz aufgefordert, weil -AcceptLicense angegeben wurde.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Weitere Details

- [Unterstützung für das Anfordern der Zustimmung zur Lizenz für Module](module-license-acceptance.md)
- [Unterstützung für das Anfordern der Zustimmung zur Lizenz in PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)