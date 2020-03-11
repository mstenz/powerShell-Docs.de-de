---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Verwenden der PowerShell-Dokumentation
ms.openlocfilehash: 7b73bc82f32e3ce1e6015822e0cc82078183931b
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279304"
---
# <a name="how-to-use-the-powershell-documentation"></a>Verwenden der PowerShell-Dokumentation

Willkommen bei der PowerShell-Onlinedokumentation. Auf dieser Website finden Sie die Cmdlet-Referenz für die folgenden PowerShell-Versionen:

- PowerShell 7 (Vorschauversion)
- PowerShell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Suchen von Artikeln und Auswählen einer Version

Es gibt zwei Möglichkeiten, um in der Dokumentation nach Inhalten zu suchen. Der einfachste Weg ist die Verwendung des Filterfelds unter der Versionsauswahl. Geben Sie einfach ein Wort ein, das im Titel eines Artikels enthalten ist. Es wird eine Liste der passenden Artikel angezeigt. Sie können auch festlegen, dass die gesamte Website anhand dieser Liste durchsucht werden soll.

Standardmäßig ist auf dieser Website die Dokumentation für die neueste veröffentlichte Version von PowerShell zu sehen. Einige Cmdlets funktionieren in verschiedenen Versionen von PowerShell unterschiedlich. Stellen Sie sicher, dass Sie die Dokumentation für die von Ihnen verwendete Version von PowerShell anzeigen.

Verwenden Sie die Versionsauswahl oben auf der Seite, um die gewünschte Version von PowerShell auszuwählen.

![Versionsauswahl](media/how-to-use-docs/version-search.gif)

Anhand des Werts `$PSversionTable.PSVersion` können Sie erkennen, welche Version von PowerShell Sie verwenden. Das folgende Beispiel zeigt die Ausgabe für Windows PowerShell v5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
