---
title: So testen Sie die aktualisierbare Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082327"
---
# <a name="how-to-test-updatable-help"></a>Testen der aktualisierbaren Hilfe

Dieses Thema beschreibt Verfahren zum Testen der aktualisierbaren Hilfe für ein Modul.

## <a name="using-verbose-to-detect-errors"></a>Verwenden ausführliche Fehler zu erkennen

Testen Sie die Dateien nach dem Hochladen der HelpInfo XML-Datei und die CAB-Dateien für das Modul mit einer [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) -Befehl mit der **ausführlich** Parameter. Die **ausführlich** -Parameter weist `Update-Help` melden die wichtigen Schritte in der Liste der Vorgänge beim Lesen der **HelpInfoUri** -Schlüssels im modulmanifest zur Überprüfung der Dateitypen in die entpackten CAB-Datei ein, und platzieren die Dateien in sprachspezifischen Modulverzeichnis gespeichert.

Wenn Sie alle ausführliche Meldungen aufgelöst werden, führen Sie eine `Update-Help` -Befehl mit der **Debuggen** Parameter. Dieser Parameter sollte alle verbleibenden Probleme mit aktualisierbaren Hilfedateien erkennen.