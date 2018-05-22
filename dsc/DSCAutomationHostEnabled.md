---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSCAutomationHostEnabled (Registrierungsschlüssel)
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
>Gilt für: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled (Registrierungsschlüssel)

DSC verwendet den Registrierungsschlüssel **DSCAutomationHostEnabled** unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**, um die Konfiguration des Computer beim ersten Start zu ermöglichen.
DSCAutomationHostEnabled unterstützt drei Modi:

|  DSCAutomationHostEnabled-Wert  |  Beschreibung   |
|---|---|
0 | Konfiguration des Computers beim Hochfahren deaktivieren |
1 | Konfiguration des Computers beim Hochfahren aktivieren |
2 | Konfiguration des Computers nur dann aktivieren, wenn DSC sich im Status „ausstehend“ oder „aktuell“ befindet. Dies ist der Standardwert. |

## <a name="see-also"></a>Weitere Informationen

Ein Beispiel dazu, wie Sie dieses Features zum Ausführen von Konfigurationen beim ersten Hochfahren verwenden, finden Sie unter [Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC](bootstrapDsc.md).