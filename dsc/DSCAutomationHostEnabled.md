
---
title: DSCAutomationHostEnabled (Registrierungsschlüssel) ms.date: 16.05.2016 keywords: PowerShell, DSC description:  
ms.topic: Artikel author: eslesar manager: dongill ms.prod: PowerShell
---

>Gilt für: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled (Registrierungsschlüssel)

DSC verwendet den Registrierungsschlüssel **DSCAutomationHostEnabled** aus **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**, um den Computer beim ersten Start automatisch zu konfigurieren.
DSCAutomationHostEnabled unterstützt drei Modi:

|  DSCAutomationHostEnabled-Wert  |  Beschreibung   | 
|---|---| 
0 | Konfiguration des Computers beim Hochfahren deaktivieren |
1 | Konfiguration des Computers beim Hochfahren aktivieren |
2 | Konfiguration des Computers nur dann aktivieren, wenn DSC sich im Status „ausstehend“ oder „aktuell“ befindet. Dies ist der Standardwert. |

## <a name="see-also"></a>Weitere Informationen

Ein Beispiel dazu, wie Sie dieses Features zum Ausführen von Konfigurationen beim ersten Hochfahren verwenden, finden Sie unter [Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC](bootstrapDsc.md).


