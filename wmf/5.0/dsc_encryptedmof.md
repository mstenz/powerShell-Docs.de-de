---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4c2a3fb15b108f1a8e9fd271a620bcb1cb8c77ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222335"
---
# <a name="mof-documents-are-encrypted-by-default"></a>MOF-Dokumente standardmäßig verschlüsselt

Konfigurationsdokumente enthalten vertrauliche Informationen. In früheren Versionen von DSC mussten Sie zum Schützten von Anmeldeinformationen innerhalb einer Konfiguration Zertifikate verteilen und verwalten. Dies brachte häufig einen erheblichen Verwaltungsaufwand mit sich, wobei es aber immer noch Konfigurationsinformationen gab, die nicht geschützt waren bzw. werden konnten.

Dies ist nicht mehr der Fall, da **alle MOF-Konfigurationsdateien standardmäßig geschützt sind**. Keine Zertifikate oder Metakonfigurationseinstellungen erforderlich Jedes Mal, wenn eine MOF-Konfigurationsdatei auf einem Zielknoten vom lokalen Konfigurations-Manager (LCM) auf einen Datenträger gespeichert wird, wird sie verschlüsselt. Die MOF-Dateien werden mit [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx) verschlüsselt. **Hinweis:** Von einem Konfigurationsskript generierte MOF-Dateien werden nicht verschlüsselt.

**Beispiel:** Verschlüsselung im Pushmodus ![MOF-Verschlüsselung](../images/MOF_Encryption.jpg)

Wenn Sie bereits die Zertifikatmethode zum Verschlüsseln von Kennwörtern verwenden oder zusätzliche Sicherheit für Ihre Kennwörter benötigen, funktioniert das [bestehende Verfahren zur zertifikatbasierten Verschlüsselung](https://msdn.microsoft.com/powershell/dsc/securemof) weiterhin. Das Ergebnis ist ein MOF-Dokument, das mit den DPAPIs vollständig verschlüsselt ist und zusätzlich über darin enthaltene verschlüsselte Kennwörter verfügt.

Diese Verschlüsselung gilt nur für MOF-Konfigurationsdokumente (pending.mof, current.mof, previous.mof, MOF-Teilkonfigurationen). MOF-Dateien mit Metakonfigurationen werden weiterhin unverschlüsselt gespeichert, da sie meist keine geheimen Schlüssel enthalten.
