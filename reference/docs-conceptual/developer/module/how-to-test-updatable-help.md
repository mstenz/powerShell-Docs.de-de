---
title: Vorgehensweise beim Testen der aktualisierbaren Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367149"
---
# <a name="how-to-test-updatable-help"></a>Testen der aktualisierbaren Hilfe

In diesem Thema werden die Ansätze zum Testen der aktualisierbaren Hilfe für ein Modul beschrieben.

## <a name="using-verbose-to-detect-errors"></a>Verwenden von Verbose zum Erkennen von Fehlern

Nachdem Sie die helpinfo-XML-Datei und die CAB-Dateien für das Modul hochgeladen haben, testen Sie die Dateien, indem Sie einen [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Befehl mit dem Parameter **verbose** ausführen Der **verbose** -Parameter weist `Update-Help` an, die wichtigen Schritte in seinen Aktionen zu melden, von dem Lesen des **helpinfouri** -Schlüssels im Modul Manifest zum Überprüfen der Dateitypen in der entpackten CAB-Datei und Ablegen der Dateien im sprachspezifischen Modul Verzeichnis.

Wenn alle ausführlichen Meldungen aufgelöst werden, führen Sie einen `Update-Help` Befehl mit dem **Debug** -Parameter aus. Dieser Parameter sollte alle verbleibenden Probleme mit den aktualisierbaren Hilfedateien erkennen.