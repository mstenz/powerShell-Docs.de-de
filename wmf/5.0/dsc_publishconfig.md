---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Übermitteln des Konfigurationsdokuments, ohne es anzuwenden

Das Cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) kopiert eine MOF-Konfigurationsdatei auf einen Zielknoten, ohne die Konfiguration anzuwenden.
Diese Konfiguration wird während des nächsten Konsistenzdurchlaufs oder bei Ausführen des Cmdlets [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) angewendet.
