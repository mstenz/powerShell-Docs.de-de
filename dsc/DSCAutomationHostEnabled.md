---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSCAutomationHostEnabled (Registrierungsschlüssel)"
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
>Gilt für: Windows PowerShell 5.0

<a id="dscautomationhostenabled-registry-key" class="xliff"></a>
# DSCAutomationHostEnabled (Registrierungsschlüssel)

DSC verwendet den Registrierungsschlüssel **DSCAutomationHostEnabled** unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**, um die Konfiguration des Computer beim ersten Start zu ermöglichen.
DSCAutomationHostEnabled unterstützt drei Modi:

|  DSCAutomationHostEnabled-Wert  |  Beschreibung   | 
|---|---| 
0 | Konfiguration des Computers beim Hochfahren deaktivieren |
1 | Konfiguration des Computers beim Hochfahren aktivieren |
2 | Konfiguration des Computers nur dann aktivieren, wenn DSC sich im Status „ausstehend“ oder „aktuell“ befindet. Dies ist der Standardwert. |

<a id="see-also" class="xliff"></a>
## Weitere Informationen

Ein Beispiel dazu, wie Sie dieses Features zum Ausführen von Konfigurationen beim ersten Hochfahren verwenden, finden Sie unter [Konfigurieren eines virtuellen Computers beim ersten Hochfahren mithilfe von DSC](bootstrapDsc.md).


