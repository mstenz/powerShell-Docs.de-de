---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 555e01e88647b40717417360fb74bb6554a9c122
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="authoring-improvements-using-powershell-ise"></a>Erstellungsverbesserungen mithilfe von PowerShell ISE

Das Erstellen von DSC-Konfigurationen in Windows PowerShell ISE ist nun dank der folgenden Verbesserungen viel einfacher:

- Auflisten aller DSC-Ressourcen in einem **Configuration**-Block oder **node**-Block durch Drücken von **STRG+LEERTASTE** in einer leeren Zeile.
- Automatische Vervollständigung für Ressourceneigenschaften mit dem **enumeration**-Typ.
- Automatische Vervollständigung für die **DependsOn**-Eigenschaft von DSC-Ressourcen basierend auf anderen Ressourceninstanzen in der Konfiguration.
- Bessere automatische Ergänzung von Eigenschaftswerten von Ressourcen.

**Hinweis:** Sie benötigen eine leere Zeichenfolge für Werte von Ressourceneigenschaften, bevor Sie STRG+LEERTASTE zum Auflisten von Optionen verwenden können. Bei Drücken der **TAB**-Taste werden Optionen durchlaufen.

