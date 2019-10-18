---
ms.date: 09/25/2019
keywords: powershell,cmdlet
title: Verwenden der PowerShell-Dokumentation
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281647"
---
# <a name="how-to-use-the-powershell-documentation"></a>Verwenden der PowerShell-Dokumentation

Willkommen bei der PowerShell-Onlinedokumentation. Auf dieser Website finden Sie die Cmdlet-Referenz für die folgenden PowerShell-Versionen:

- PowerShell 7 (Vorschauversion)
- PowerShell 6
- PowerShell 5.1
- PowerShell 5.0
- PowerShell 4.0
- PowerShell 3.0

## <a name="selecting-your-version"></a>Auswahl Ihrer Version

Standardmäßig ist auf dieser Website die Dokumentation für die neueste veröffentlichte Version von PowerShell zu sehen. Einige Cmdlets funktionieren in verschiedenen Versionen von PowerShell unterschiedlich. Stellen Sie sicher, dass Sie die Dokumentation für die von Ihnen verwendete Version von PowerShell anzeigen.

Verwenden Sie die Versionsauswahl oben auf der Seite, um die gewünschte Version von PowerShell auszuwählen.

![Versionsauswahl](images/how-to-use-docs/picker-vall.gif)

Anhand des Werts `$PSversionTable.PSVersion` können Sie erkennen, welche Version von PowerShell Sie verwenden. Das folgende Beispiel zeigt die Ausgabe für Windows PowerShell v5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>Suche nach Artikeln

Es gibt zwei Möglichkeiten, um in der Dokumentation nach Inhalten zu suchen. Der einfachste Weg ist die Verwendung des Filterfelds unter der Versionsauswahl. Geben Sie einfach ein Wort ein, das im Titel eines Artikels enthalten ist. Es wird eine Liste der passenden Artikel angezeigt. Sie können auch festlegen, dass die gesamte Website anhand dieser Liste durchsucht werden soll.

![Filterfeld](images/how-to-use-docs/filter-search.gif)
