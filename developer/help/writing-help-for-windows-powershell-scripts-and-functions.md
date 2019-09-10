---
title: Schreiben von Hilfe für PowerShell-Skripts und-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848101"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Schreiben von Hilfe für PowerShell-Skripts und-Funktionen

PowerShell-Skripts und-Funktionen sollten vollständig dokumentiert sein, wenn Sie für andere Personen freigegeben werden.
Das `Get-Help` -Cmdlet zeigt die Hilfe Themen für Skripts und Funktionen im gleichen Format an, in dem die Hilfe für Cmdlets angezeigt `Get-Help` wird, und alle Parameter funktionieren in Skript-und Funktions Hilfe Themen.

PowerShell-Skripts können ein Hilfethema zu dem Skript und Hilfe Themen zu den einzelnen Funktionen im Skript enthalten.
Funktionen, die unabhängig von Skripts freigegeben werden, können eigene Hilfe Themen enthalten.

In diesem Dokument werden das Format und die richtige Platzierung der Hilfe Themen erläutert, und es werden Richtlinien für den Inhalt vorgeschlagen.

## <a name="types-of-script-and-function-help"></a>Typen von Skript-und Funktions Hilfe

### <a name="comment-based-help"></a>Kommentar basierte Hilfe
Das Hilfethema, das ein Skript oder eine Funktion beschreibt, kann als Satz von Kommentaren innerhalb des Skripts oder der Funktion implementiert werden.
Beachten Sie beim Schreiben der Kommentar basierten Hilfe für ein Skript und für Funktionen in einem Skript sorgfältig die Regeln zum Platzieren der Kommentar basierten Hilfe.
Die Platzierung bestimmt, ob `Get-Help` das Cmdlet das Hilfethema dem Skript oder einer Funktion zuordnet.
Weitere Informationen zum Schreiben von Kommentar basierten Hilfe Themen finden Sie unter [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>XML-basierte Befehls Hilfe
Das Hilfethema, das ein Skript oder eine Funktion beschreibt, kann in einer XML-Datei implementiert werden, die das Befehls Hilfe Schema verwendet.
Um das Skript oder die Funktion der XML-Datei zuzuordnen, verwenden `ExternalHelp` Sie das Kommentar Schlüsselwort, gefolgt vom Pfad und Namen der XML-Datei.

Wenn das `ExternalHelp` Kommentar Schlüsselwort vorhanden ist, hat es Vorrang vor der Kommentar basierten Hilfe, `Get-Help` auch wenn keine Hilfedatei finden kann, die mit dem `ExternalHelp` Wert des Schlüssel Worts übereinstimmt.

### <a name="online-help"></a>Online Hilfe
Sie können Ihre Hilfe Themen im Internet veröffentlichen und die Themen dann `Get-Help` direkt öffnen.
Weitere Informationen zum Schreiben von Kommentar basierten Hilfe Themen finden Sie [unter unterstützen der Online Hilfe](../module/supporting-online-help.md).

Es gibt keine bewährte Methode zum Schreiben von konzeptionellen Themen ("about") für Skripts und Funktionen.
Sie können jedoch konzeptionelle Themen im Internet auflisten. die Themen und deren URLs finden Sie im Abschnitt Verwandte Links eines Befehls Hilfe Themas.

## <a name="content-considerations-for-script-and-function-help"></a>Inhalts Überlegungen für Skript-und Funktions Hilfe

- Wenn Sie ein sehr kurzes Hilfethema mit nur einigen der verfügbaren Befehls Hilfe Abschnitte schreiben, stellen Sie sicher, dass Sie klare Beschreibungen der Skript-oder Funktionsparameter einschließen. Fügen Sie auch einen oder zwei Beispiel Befehle in den Abschnitt "Beispiele" ein, auch wenn Sie sich entscheiden, Beispiel Beschreibungen auszulassen.

- Verweisen Sie in allen Beschreibungen auf den Befehl als Skript oder Funktion. Diese Informationen helfen dem Benutzer, den Befehl zu verstehen und zu verwalten.

  In der folgenden detaillierten Beschreibung ist beispielsweise angegeben, dass der New-Topic-Befehl ein Skript ist. Dadurch werden Benutzer daran erinnert, dass Sie den Pfad und den vollständigen Namen angeben müssen, wenn Sie Sie ausführen.

  > "Das New-Topic-Skript erstellt ein leeres konzeptionelles Thema für jeden Themen Namen in der Eingabedatei..."

  Die folgende ausführliche Beschreibung gibt an `Disable-PSRemoting` , dass eine Funktion ist. Diese Informationen sind besonders nützlich für Benutzer, wenn die Sitzung mehrere Befehle mit demselben Namen enthält, von denen einige möglicherweise durch einen Befehl mit höherer Rangfolge ausgeblendet werden.

  > Die `Disable-PSRemoting` Funktion deaktiviert alle Sitzungs Konfigurationen auf dem lokalen Computer...

- Erläutern Sie in einem Skript Hilfethema, wie Sie das Skript als Ganzes verwenden. Wenn Sie auch Hilfe Themen für Funktionen im Skript schreiben, erwähnen Sie die Funktionen in Ihrem Skript Hilfethema, und schließen Sie Verweise auf die Funktionen der Hilfe Themen im Abschnitt Verwandte Links des Skripts Hilfethema ein. Wenn eine Funktion Teil eines Skripts ist, erklären Sie im Gegensatz dazu im Hilfethema der Funktion die Rolle, die die Funktion im Skript spielt, und wie Sie unabhängig voneinander verwendet werden kann. Listen Sie dann das Skript Hilfethema im Abschnitt "Verwandte Links" des Hilfe Themas für die Funktion auf.

- Wenn Sie Beispiele für ein Skript Hilfethema schreiben, stellen Sie sicher, dass Sie den Pfad zur Skriptdatei im Beispiel Befehl einschließen. Dadurch werden Benutzer daran erinnert, dass Sie den Pfad explizit angeben müssen, auch wenn sich das Skript im aktuellen Verzeichnis befindet.

- Erinnern Sie sich in einem Funktions Hilfethema an Benutzer, dass die Funktion nur in der aktuellen Sitzung vorhanden ist, und um Sie in anderen Sitzungen zu verwenden. Sie müssen Sie hinzufügen oder ihr ein PowerShell-Profil hinzufügen.

- `Get-Help`zeigt das Hilfethema für ein Skript oder eine Funktion nur an, wenn die Skriptdatei und die Hilfe Themendateien an den richtigen Speicherorten gespeichert werden. Daher ist es nicht sinnvoll, Anweisungen zum Installieren von PowerShell oder zum Speichern oder Installieren des Skripts oder der Funktion in einem Skript oder in einem Hilfethema zu erhalten. Fügen Sie stattdessen alle Installationsanweisungen in das Dokument ein, das Sie zum Verteilen des Skripts oder der Funktion verwenden.

## <a name="see-also"></a>Weitere Informationen

[Schreiben von Kommentar basierten Hilfe Themen](./writing-comment-based-help-topics.md)
