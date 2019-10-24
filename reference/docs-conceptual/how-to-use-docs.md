---
ms.date: 10/20/2019
keywords: powershell,cmdlet
title: Verwenden der PowerShell-Dokumentation
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: ac1ccdd826f112a11db09af9c628cae013f947ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2019
ms.locfileid: "72676156"
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

![Versionsauswahl](images/how-to-use-docs/version-search.gif)

Anhand des Werts `$PSversionTable.PSVersion` können Sie erkennen, welche Version von PowerShell Sie verwenden. Das folgende Beispiel zeigt die Ausgabe für Windows PowerShell v5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
