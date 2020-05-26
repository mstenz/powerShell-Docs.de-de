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
ms.openlocfilehash: 8dd3770a60ca56634ad1eb1ac8cf89d96c975c90
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811509"
---
# <a name="how-to-test-updatable-help"></a>Testen der aktualisierbaren Hilfe

In diesem Thema werden die Ansätze zum Testen der aktualisierbaren Hilfe für ein Modul beschrieben.

## <a name="using-verbose-to-detect-errors"></a>Verwenden von Verbose zum Erkennen von Fehlern

Nachdem Sie die helpinfo-XML-Datei und die CAB-Dateien für das Modul hochgeladen haben, testen Sie die Dateien, indem Sie einen [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Befehl mit dem Parameter **verbose** ausführen Der **verbose** -Parameter weist `Update-Help` an, die wichtigen Schritte in seinen Aktionen zu melden, von dem Lesen des **helpinfouri** -Schlüssels im Modul Manifest, um die Dateitypen in der entpackten CAB-Datei zu überprüfen und die Dateien in das sprachspezifische Modul Verzeichnis zu platzieren.

Wenn alle ausführlichen Meldungen aufgelöst werden, führen Sie einen `Update-Help` Befehl mit dem **Debug** -Parameter aus. Dieser Parameter sollte alle verbleibenden Probleme mit den aktualisierbaren Hilfedateien erkennen.
