---
title: Schreiben von Hilfe für PowerShell-Skripts und Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857476"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Schreiben von Hilfe für PowerShell-Skripts und Funktionen

PowerShell-Skripts und Funktionen sollten vollständig dokumentiert werden, wenn sie für andere Benutzer freigegeben werden.
Die `Get-Help` Cmdlet zeigt die Hilfethemen für Skripts und die Funktion im gleichen Format, z. B. es zeigt die Hilfe für Cmdlets und alle der `Get-Help` Parametern verwendet wird, auf die Hilfethemen für Skripts und -Funktion.

PowerShell-Skripts können ein Hilfethema zu diesem Skript und die Hilfethemen zu den einzelnen Funktionen in das Skript eingefügt werden.
Funktionen, die unabhängig von den Skripts gemeinsam genutzt werden, können ihre eigenen Hilfethemen enthalten.

In diesem Dokument wird erläutert, das Format und die richtige Platzierung der Hilfethemen, und es enthält Vorschläge für Richtlinien für den Inhalt.

## <a name="types-of-script-and-function-help"></a>Typen von Skript und die Funktion-Hilfe

### <a name="comment-based-help"></a>Kommentarbasierte Hilfe
Das Hilfethema, das ein Skript oder eine Funktion beschreibt, kann als ein Satz von Anmerkungen in das Skript oder die Funktion implementiert werden.
Beim kommentarbasierte Hilfe für ein Skript, und für Funktionen in einem Skript zu schreiben, achten Sie sorgfältig den Regeln für die kommentarbasierte Hilfe platzieren.
Die Platzierung bestimmt, ob die `Get-Help` Cmdlet, das Skript oder eine Funktion ordnet das Hilfethema.
Weitere Informationen zum Schreiben von Kommentar-Hilfethemen finden Sie unter [About_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>XML-basierten Befehl Hilfe
Das Hilfethema, das ein Skript oder eine Funktion beschreibt, kann in eine XML-Datei implementiert werden, die der Befehl Hilfe-Schema verwendet.
Um das Skript oder die Funktion die XML-Datei zuzuordnen, verwenden die `ExternalHelp` kommentieren Schlüsselwort, gefolgt von den Pfad und Namen der XML-Datei.

Wenn die `ExternalHelp` kommentieren Schlüsselwort ist vorhanden, er hat Vorrang vor kommentarbasierte Hilfe, auch wenn `Get-Help` eine Hilfedatei, die den Wert der entspricht wurde nicht gefunden der `ExternalHelp` Schlüsselwort.

### <a name="online-help"></a>Onlinehilfe
Sie können die Hilfethemen im Internet veröffentlichen und die anschließende Weiterleitung `Get-Help` zu die Themen zu öffnen.
Weitere Informationen zum Schreiben von Kommentar-Hilfethemen finden Sie unter [Supporting Online Help](../module/supporting-online-help.md).

Es gibt keine feststehende Methode für das Schreiben von konzeptionellen ("Info") Themen für Skripts und Funktionen.
Allerdings können Sie konzeptionellen Themen, in der Internet-Liste in den Themen und den URLs im Abschnitt "Verwandte Links" eines Hilfethemas Befehl veröffentlichen.

## <a name="content-considerations-for-script-and-function-help"></a>Inhalt Überlegungen zum Skript und die Funktion unterstützen

- Wenn Sie eine sehr kurze Hilfethema mit nur einigen der verfügbaren Befehl Hilfe enthaltenen Abschnitte schreiben, achten Sie darauf, dass Sie klare Beschreibungen der Parameter Skript oder einer Funktion enthalten soll. Auch enthalten Sie ein oder zwei Beispiele für Befehle im Abschnitt "Beispiele", selbst wenn Sie zum Beispiel Beschreibungen auslassen.

- Alle Beschreibungen finden Sie in den Befehl als ein Skript oder eine Funktion. Diese Informationen helfen den Benutzer zu verstehen und verwalten den Befehl.

  Gibt z. B. die folgende ausführliche Beschreibung an, dass der New-Topic-Befehl ein Skript handelt. Dies erinnert Benutzer, die sie benötigen, geben den Pfad und den vollständigen Namen ein, wenn sie ausgeführt wird.

  > "Das New-Topic-Skript erstellt eine leere Konzeptthema für jeden Themennamen eines in der Eingabedatei..."

  Gibt an, dass die folgende ausführliche Beschreibung `Disable-PSRemoting` ist eine Funktion. Diese Informationen sind besonders nützlich für Benutzer, wenn die Sitzung mehrere Befehle mit demselben Namen enthält, von denen einige möglicherweise von einem Befehl mit höherer rangfolgenposition verborgen werden.

  > Die `Disable-PSRemoting` Funktion deaktiviert alle Sitzungskonfigurationen auf dem lokalen Computer...

- In einem Skript-Hilfethema wird erläutert, wie das Skript als Ganzes verwenden. Wenn Sie auch die Hilfethemen für Funktionen im Skript schreiben, die Funktionen in Ihrem Skript Hilfethema durch, und enthalten Sie Verweise auf die Hilfethemen für die Funktion im Abschnitt "Verwandte Links" des Hilfethemas Skript. Im Gegensatz dazu eine Funktion in einem Skript ist, Erläutern Sie im Hilfethema Funktion die Rolle, die die Funktion wiedergegeben wird, in das Skript, und wie sie unabhängig voneinander verwendet werden kann. Listen Sie dann im Hilfethema "Skript" im Abschnitt "Verwandte Links" des Hilfethemas Funktion.

- Wenn Sie Beispiele für ein Hilfethema Skript zu schreiben, achten Sie darauf, dass Sie den Pfad zur Skriptdatei im Beispielbefehl enthält. Dies erinnert Benutzer daran, dass sie den Pfad explizit angeben müssen, auch wenn das Skript im aktuellen Verzeichnis ist.

- In einem Hilfethema Funktion erinnern Sie Benutzer, die die Funktion nur in der aktuellen Sitzung vorhanden ist, und klicken, um es in anderen Sitzungen verwenden, müssen sie hinzufügen oder ein PowerShell-Profil hinzufügen.

- `Get-Help` Zeigt das Hilfethema für ein Skript oder eine Funktion an, nur, wenn die Skriptdatei und die Hilfedateien am richtigen Speicherort gespeichert werden. Aus diesem Grund ist es nicht sinnvoll, die Anweisungen zum Installieren von PowerShell, oder speichern, oder installieren das Skript oder einer Funktion in einem Hilfethema Skript oder einer Funktion enthalten. Stattdessen können Sie alle Anweisungen zur Installation in das Dokument, das Sie verwenden, um das Skript oder die Funktion zu verteilen.

## <a name="see-also"></a>Weitere Informationen

 [Schreiben von XML-Hilfethemen für Skripts und Funktionen](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Schreiben von XML-basierte Hilfethemen zu Befehlen](./writing-xml-based-help-topics-for-commands.md)

 [Schreiben von Kommentar-Hilfethemen](./writing-comment-based-help-topics.md)
