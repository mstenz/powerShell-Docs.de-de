---
title: "DSCAutomationHostEnabled (Registrierungsschlüssel)"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: eb5889668136def1b47a4999374711460a08179c
ms.sourcegitcommit: 6057e6d22ef8a2095af610e0d681e751366a9773
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2017
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


