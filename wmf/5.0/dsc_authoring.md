---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679441"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Erstellungsverbesserungen mithilfe von PowerShell ISE

Das Erstellen von DSC-Konfigurationen in Windows PowerShell ISE ist nun dank der folgenden Verbesserungen viel einfacher:

- Auflisten aller DSC-Ressourcen in einem **Configuration**-Block oder **node**-Block durch Drücken von **STRG+LEERTASTE** in einer leeren Zeile.
- Automatische Vervollständigung für Ressourceneigenschaften mit dem **enumeration**-Typ.
- Automatische Vervollständigung für die **DependsOn**-Eigenschaft von DSC-Ressourcen basierend auf anderen Ressourceninstanzen in der Konfiguration.
- Bessere automatische Ergänzung von Eigenschaftswerten von Ressourcen.

**Hinweis:** Sie benötigen eine leere Zeichenfolge für Werte von Ressourceneigenschaften, bevor Sie STRG+LEERTASTE zum Auflisten von Optionen verwenden können. Bei Drücken der **TAB**-Taste werden Optionen durchlaufen.
