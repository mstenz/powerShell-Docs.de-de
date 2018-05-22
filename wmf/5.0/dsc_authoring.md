---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1595a3e817fd711c35128f06927fd57df7a63fb8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a>Erstellungsverbesserungen mithilfe von PowerShell ISE

Das Erstellen von DSC-Konfigurationen in Windows PowerShell ISE ist nun dank der folgenden Verbesserungen viel einfacher:

- Auflisten aller DSC-Ressourcen in einem **Configuration**-Block oder **node**-Block durch Drücken von **STRG+LEERTASTE** in einer leeren Zeile.
- Automatische Vervollständigung für Ressourceneigenschaften mit dem **enumeration**-Typ.
- Automatische Vervollständigung für die **DependsOn**-Eigenschaft von DSC-Ressourcen basierend auf anderen Ressourceninstanzen in der Konfiguration.
- Bessere automatische Ergänzung von Eigenschaftswerten von Ressourcen.

**Hinweis:** Sie benötigen eine leere Zeichenfolge für Werte von Ressourceneigenschaften, bevor Sie STRG+LEERTASTE zum Auflisten von Optionen verwenden können. Bei Drücken der **TAB**-Taste werden Optionen durchlaufen.
