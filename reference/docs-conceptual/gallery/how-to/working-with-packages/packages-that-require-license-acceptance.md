---
ms.date: 06/12/2017
contributor: Farehar
keywords: Katalog,PowerShell,psgallery
title: Erforderliche Zustimmung zur Lizenz
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278647"
---
# <a name="require-license-acceptance"></a>Erforderliche Zustimmung zur Lizenz

Der Text zum Anfordern der Zustimmung zur Lizenz wird auf der Seite mit den Elementdetails für Module angezeigt, für die die Zustimmung zur Lizenz erforderlich ist. Die Lizenz für das Modul kann durch Klicken auf „‚License.txt‘ anzeigen“ angezeigt werden.

![Erforderliche Zustimmung zur Lizenz](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

Benutzer werden beim Installieren, Speichern oder Aktualisieren des Moduls über PowerShellGet oder bei der Bereitstellung für Azure Automation aufgefordert, die Lizenz zu akzeptieren.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Erforderliche Zustimmung zur Lizenz für die Bereitstellung in Azure Automation

Wenn für das Modul, das in Azure Automation bereitgestellt wird, die Zustimmung zur Lizenz erforderlich ist, wird auf der Portaloberfläche ein Haftungsausschluss mit folgender Meldung angezeigt: „Für dieses Modul muss der Lizenz zugestimmt werden. Indem Sie auf ‚OK‘ klicken, akzeptieren Sie die Lizenzbedingungen.“

![Für die Bereitstellung in Azure Automation ist die Zustimmung zur Lizenz erforderlich.](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Weitere Informationen

[Erforderliche Zustimmung zur Lizenz in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation-Website](/azure/automation)
