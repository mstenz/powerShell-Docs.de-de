---
ms.date: 07/09/2019
keywords: DSC, GPO, PowerShell, Konfiguration, Setup
title: Schnellstart – Konvertieren von Gruppenrichtlinien in DSC
ms.openlocfilehash: 5e6b86be5127332fe4fd400980c8e147b735247b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500656"
---
> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Schnellstart: Konvertieren von Gruppenrichtlinien in DSC

Sie können eine DSC-Konfiguration aus einer Gruppenrichtlinie oder Azure Security Center-Baseline generieren. Das Modul [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) umfasst die folgenden Befehle für diese Aufgabe.

- `ConvertFrom-GPO`: Konvertiert Gruppenrichtlinien, als Dateien gespeichert. Sie können auch ein Verzeichnis mit mehreren Richtlinien angeben, die in einer Konfiguration zusammengefasst werden.
  - Verwenden Sie zum Exportieren von Gruppenrichtlinien in Ihrer Umgebung das Cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps), oder folgen Sie den Anweisungen unter [Export a GPO to a File (Exportieren von Gruppenrichtlinienobjekten in eine Datei)](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM`: Konvertiert Security Compliance Manager-Baselines, als `.xml`-Dateien gespeichert.
- `ConvertFrom-ASC`: Konvertiert Azure Security Center-Baselines, als `.json`-Dateien gespeichert.
- `Merge-GPOs`: Konvertiert auf einen Zielcomputer angewendete Gruppenrichtlinien.

Mit den oben aufgeführten Cmdlets wird eine Baseline in eine DSC-`.mof`-Datei konvertiert. Sie können auch ein Konfigurationsskript ausgeben (`.ps1`), das bearbeitet und neu kompiliert werden kann. Die Cmdlets erkennen Kompilierungsfehler für fehlende Ressourcen oder doppelte Ressourcenblöcke. Ressourcenblöcke, die Kompilierungsfehler verursachen, werden auskommentiert.

Im folgenden Beispiel wird eine [Microsoft Security-Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) in ein DSC-Konfigurationsskript (`.ps1`) und eine `.mof`-Datei konvertiert.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Nach dem Ausführen der Befehle sehen Sie zwei Dateien im Standardausgabeverzeichnis, das unter dem aktuellen Pfad erstellt wird.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Für jeden verwalteten Knoten sind außerdem die folgenden zwei Module erforderlich:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** ist eine von der Community entwickelte Lösung, durch die DSC für den Support leichter analysierbar ist, da Communitylösungen von den Projektverantwortlichen und nicht von Microsoft stammen. Sie können ein neues Problem für **BaselineManagement** auf [GitHub](https://github.com/microsoft/BaselineManagement) öffnen.

## <a name="next-steps"></a>Nächste Schritte

- Informationen zum Hochladen Ihres Konfigurationsskripts in Azure Automation State Configuration finden Sie unter [Erste Schritte](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Fügen Sie Ihrem [Automation-Konto](/azure/automation/shared-resources/modules) das **SecurityPolicyDSC**-Modul und das **AuditPolicyDSC**-Modul hinzu.
- DSC-Konfigurationen und -Ressourcen finden Sie unter [PowerShell-Katalog](https://www.powershellgallery.com/).
