---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a>Übermitteln des Konfigurationsdokuments, ohne es anzuwenden

Das Cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) kopiert eine MOF-Konfigurationsdatei auf einen Zielknoten, ohne die Konfiguration anzuwenden.
Diese Konfiguration wird während des nächsten Konsistenzdurchlaufs oder bei Ausführen des Cmdlets [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) angewendet.