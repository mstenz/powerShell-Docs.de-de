---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e921a5ead21f52b7e0d9efd9335c44b99d7d6802
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="deliver-a-configuration-document-without-applying"></a>Übermitteln des Konfigurationsdokuments, ohne es anzuwenden

Das Cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) kopiert eine MOF-Konfigurationsdatei auf einen Zielknoten, ohne die Konfiguration anzuwenden. Diese Konfiguration wird während des nächsten Konsistenzdurchlaufs oder bei Ausführen des Cmdlets [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) angewendet.

