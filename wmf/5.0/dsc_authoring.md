---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085642"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Erstellungsverbesserungen mithilfe von PowerShell ISE

Das Erstellen von DSC-Konfigurationen in Windows PowerShell ISE ist nun dank der folgenden Verbesserungen viel einfacher:

- Auflisten aller DSC-Ressourcen in einem **Configuration**-Block oder **node**-Block durch Drücken von **STRG+LEERTASTE** in einer leeren Zeile.
- Automatische Vervollständigung für Ressourceneigenschaften mit dem **enumeration**-Typ.
- Automatische Vervollständigung für die **DependsOn**-Eigenschaft von DSC-Ressourcen basierend auf anderen Ressourceninstanzen in der Konfiguration.
- Bessere automatische Ergänzung von Eigenschaftswerten von Ressourcen.

**Hinweis:** Sie benötigen eine leere Zeichenfolge für Werte von Ressourceneigenschaften, bevor Sie STRG+LEERTASTE zum Auflisten von Optionen verwenden können. Bei Drücken der **TAB**-Taste werden Optionen durchlaufen.
