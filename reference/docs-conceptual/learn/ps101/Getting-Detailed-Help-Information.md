---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Abrufen von ausführlichen Hilfeinformationen
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808496"
---
# <a name="getting-detailed-help-information"></a>Abrufen ausführlicher Hilfeinformationen

PowerShell umfasst ausführliche Hilfeartikel, in denen die Konzepte von PowerShell und die PowerShell-Sprache erläutert werden. Außerdem gibt es Hilfeartikel für jedes Cmdlet und jeden Anbieter sowie für viele Funktionen und Skripts.

Sie können diese Hilfeartikel über die Eingabeaufforderung anzeigen. Sie können aber auch die zuletzt aktualisierten Versionen dieser Artikel in der [PowerShell](/powershell/scripting/overview)-Dokumentation online anzeigen.

## <a name="getting-help-for-cmdlets"></a>Abrufen von Hilfe für Cmdlets

Wenn Sie Hilfe zu PowerShell-Cmdlets abrufen möchten, verwenden Sie das Cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help). Geben Sie beispielsweise Folgendes ein, um Hilfe für das Cmdlet `Get-ChildItem` abzurufen:

```powershell
Get-Help Get-ChildItem
```

oder

```powershell
Get-ChildItem -?
```

Sie können sogar Hilfe zu dem Cmdlet „Get-Help“ abrufen. Beispiel:

```powershell
Get-Help Get-Help
```

Um eine Liste aller Cmdlet-Hilfeartikel in der Sitzung abzurufen, geben Sie Folgendes ein:

```powershell
Get-Help -Category Cmdlet
```

Wenn Sie nur jeweils eine Seite jedes Hilfeartikels anzeigen möchten, verwenden Sie die Funktion `help` oder deren Alias `man`.
Geben Sie beispielsweise Folgendes ein, um Hilfe für das Cmdlet `Get-ChildItem` anzuzeigen:

```powershell
man Get-ChildItem
```

oder

```powershell
help Get-ChildItem
```

Um ausführliche Informationen anzuzeigen, verwenden Sie den Parameter **Detailed** des Cmdlets `Get-Help`. Geben Sie beispielsweise Folgendes ein, um ausführliche Informationen zum Cmdlet `Get-ChildItem` abzurufen:

```powershell
Get-Help Get-ChildItem -Detailed
```

Wenn Sie den gesamten Inhalt eines Hilfeartikels anzeigen möchten, verwenden Sie den Parameter **Full** des Cmdlets `Get-Help`. Soll beispielsweise der gesamte Inhalt des Hilfeartikels für das Cmdlet `Get-ChildItem` angezeigt werden, geben Sie Folgendes ein:

```powershell
Get-Help Get-ChildItem -Full
```

Um ausführliche Hilfe zu den Parametern eines Cmdlets abzurufen, verwenden Sie den Parameter **Parameter** des Cmdlets `Get-Help`. Soll beispielsweise die ausführliche Hilfe zu allen Parametern des Cmdlets `Get-ChildItem` abgerufen werden, geben Sie Folgendes ein:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Um nur die Beispiele in einem Hilfeartikel anzuzeigen, verwenden Sie den Parameter **Examples** von `Get-Help`.
Sollen beispielsweise nur die Beispiele im Hilfeartikel für das Cmdlet `Get-ChildItem` angezeigt werden, geben Sie Folgendes ein:

```powershell
Get-Help Get-ChildItem -Examples
```

Informationen dazu, wie Sie Hilfeartikel für die Cmdlets schreiben, die Sie erstellen, finden Sie unter [How to Write Cmdlet Help (Schreiben von Hilfe zu Cmdlets)](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Abrufen von konzeptioneller Hilfe

Das Cmdlet `Get-Help` zeigt auch Informationen zu konzeptionellen Artikeln in PowerShell an, darunter Artikel zur PowerShell-Sprache. Konzeptionelle Hilfeartikel beginnen mit dem Präfix „about_“, z.B. „about_line_editing“. (Der Name eines konzeptionellen Artikels muss in Englisch eingegeben werden, auch in nicht englischsprachigen Versionen von PowerShell.)

Um eine Liste der konzeptionellen Artikel anzuzeigen, geben Sie Folgendes ein:

```powershell
Get-Help about_*
```

Um einen bestimmten Hilfeartikel anzuzeigen, geben Sie den Namen des Artikels ein, Beispiel:

```powershell
Get-Help about_command_syntax
```

Die Parameter von `Get-Help`, etwa **Detailed**, **Parameter** und **Examples**, wirken sich nicht auf die Anzeige von konzeptionellen Hilfeartikeln aus.

## <a name="getting-help-about-providers"></a>Abrufen von Hilfe zu Anbietern

Das Cmdlet `Get-Help` zeigt Informationen zu PowerShell-Anbietern an. Um Hilfe zu einem Anbieter abzurufen, geben Sie `Get-Help` gefolgt vom Anbieternamen ein. Wenn Sie z. B. Hilfe zum Registrierungsanbieter abrufen möchten, geben Sie Folgendes ein:

```powershell
Get-Help registry
```

Um eine Liste aller Hilfeartikel zu Anbietern in der Sitzung abzurufen, geben Sie Folgendes ein:

```powershell
Get-Help -Category provider
```

Die Parameter von `Get-Help`, etwa **Detailed**, **Parameter** und **Examples**, wirken sich nicht auf die Anzeige von Hilfeartikeln zu Anbietern aus.

## <a name="getting-help-about-scripts-and-functions"></a>Abrufen von Hilfe zu Skripts und Funktionen

Viele Skripts und Funktionen in PowerShell haben Hilfeartikel. Verwenden Sie das Cmdlet `Get-Help`, um die Hilfeartikel für Skripts und Funktionen anzuzeigen.

Wenn Sie die Hilfe für eine Funktion anzeigen möchten, geben Sie `Get-Help` und dahinter den Namen der Funktion ein. Geben Sie beispielsweise Folgendes ein, um Hilfe für die Funktion `Disable-PSRemoting` abzurufen:

```powershell
Get-Help Disable-PSRemoting
```

Um die Hilfe für ein Skript anzuzeigen, geben Sie den Pfad zur Skriptdatei ein. Wenn sich das Skript nicht in einem Pfad befindet, der in der Umgebungsvariablen „Path“ aufgelistet ist, müssen Sie den vollqualifizierten Pfad verwenden.

Wenn Sie beispielsweise ein Skript namens „TestScript.ps1“ in Ihrem Verzeichnis „C:\\PS-Test“ haben, geben Sie Folgendes ein, um den Hilfeartikel für das Skript anzuzeigen:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Die Parameter, die für die Anzeige der Cmdlet-Hilfe vorgesehen sind, funktionieren auch für die Hilfe zu Skripts und Funktionen. Die Hilfe zu Funktionen und Skripts wird allerdings nicht beim Ausführen von `Get-Help *` angezeigt.

Informationen zum Schreiben von Hilfeartikeln für Ihre Funktionen und Skripts finden Sie in den folgenden Artikeln:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Abrufen von Hilfe aus dem Internet

Die Onlineanzeige der Hilfeartikel ist eine der besten Möglichkeiten, um Hilfe zu erhalten. Onlineartikel können leichter aktualisiert werden und bieten aktuelle Inhalte.

Um Hilfe aus dem Internet abzurufen, verwenden Sie den Parameter **Online** des Cmdlets `Get-Help`. Alle Hilfeartikel für PowerShell, einschließlich der Hilfeartikel zu Anbietern und konzeptioneller Hilfeartikel („about“), stehen online in der [PowerShell](/powershell/scripting/powershell-scripting)-Dokumentation zur Verfügung.

> [!NOTE]
> Der Parameter **Online** kann nicht mit konzeptionellen (about_\*) Hilfeartikeln oder Hilfeartikeln zu Anbietern verwendet werden.
> Die Onlinehilfe ist optional, daher ist sie nicht für alle Cmdlets, Funktionen oder Skripts verfügbar.

Möchten Sie beispielsweise die Onlineversion des Hilfeartikels zum Cmdlet `Get-ChildItem` abrufen, geben Sie Folgendes ein:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell öffnet den Artikel in Ihrem Standardbrowser. Wird Onlinehilfe für einen Hilfeartikel unterstützt, können Sie auch die URL des Hilfeartikels anzeigen. Die URL wird im Abschnitt „Verwandte Links“ eines Hilfeartikels angezeigt.

Wenn Sie beispielsweise die URL für die Onlineversion des Cmdlets „Add-Computer“ anzeigen möchten, geben Sie Folgendes ein:

```powershell
Get-Help Add-Computer
```

Die erste Zeile des Abschnitts „Verwandte Links“ des Artikels ist nachstehend dargestellt.

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

Informationen dazu, wie Sie Onlineunterstützung für Ihre Hilfeartikel bereitstellen, finden Sie unter [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Weitere Informationen

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
