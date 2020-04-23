---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Bereitstellen in Azure Automation
ms.openlocfilehash: 5d09a0777c59b642400d683c8cb6f881319fb881
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278718"
---
# <a name="deploy-to-azure-automation"></a>Bereitstellen in Azure Automation

Mit der Schaltfläche „In Azure Automation bereitstellen“ auf der Seite mit den Paketdetails können Sie ein Paket aus dem PowerShell-Katalog in Azure Automation bereitstellen.

![Schaltfläche zum Bereitstellen in Azure Automation](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

Wenn Sie auf diese Schaltfläche klicken, werden Sie zum Azure-Verwaltungsportal umgeleitet, wo Sie sich mit den Anmeldeinformationen Ihres Azure-Kontos anmelden.
Wenn das Paket Abhängigkeiten enthält, werden diese ebenfalls in Azure Automation bereitgestellt.

> [!WARNING]
> Wenn das gleiche Paket und die gleiche Version bereits in Ihrem Automation-Konto vorhanden sind, überschreibt das erneute Bereitstellen aus dem PowerShell-Katalog das Paket in Ihrem Automation-Konto.

Wenn Sie ein Modul bereitstellen, wird es im Abschnitt „Module“ von Azure Automation angezeigt.  Wenn Sie ein Skript bereitstellen, wird es im Abschnitt „Runbooks“ von Azure Automation angezeigt.

Sie können die Schaltfläche „In Azure Automation bereitstellen“ deaktivieren, indem Sie den Paketmetadaten das Tag „AzureAutomationNotSupported“ hinzufügen.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation

Wenn für das Modul, das in Azure Automation bereitgestellt wird, die Zustimmung zur Lizenz erforderlich ist, wird auf der Portaloberfläche ein Haftungsausschluss mit folgender Meldung angezeigt: „Für dieses Modul muss der Lizenz zugestimmt werden. Indem Sie auf ‚OK‘ klicken, akzeptieren Sie die Lizenzbedingungen.“

![Für die Bereitstellung in Azure Automation ist die Zustimmung zur Lizenz erforderlich.](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Weitere Informationen

- [Erforderliche Zustimmung zur Lizenz in PowerShellGet](../../concepts/module-license-acceptance.md)
- [Erforderliche Zustimmung zur Lizenz im PowerShell-Katalog](packages-that-require-license-acceptance.md)
- [Azure Automation-Website](https://azure.microsoft.com/services/automation/)
