---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Syntax für die Katalogsuche
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188410"
---
# <a name="gallery-search-syntax"></a>Syntax für die Katalogsuche

Der PowerShell-Katalog bietet ein Textsuchfeld in das Sie Wörter, Ausdrücke und Schlüsselwortausdrücke schreiben können, um die Suchergebnisse einzugrenzen.

## <a name="search-by-keywords"></a>Suche nach Schlüsselwörtern

    dsc azure sql

Die Suche tut ihr Möglichstes, um relevante Dokumente zu finden, die alle drei Schlüsselwörter enthalten, und zugehörige Dokumente zurückzugeben.

## <a name="search-using-phrases-and-keywords"></a>Suchen mithilfe von Ausdrücken und Schlüsselwörtern

    "azure sql" deployment

Die Eingabe eines Ausdrucks zwischen Anführungszeichen ("") ändert den Suchvorgang. Es wird nun nach dem bestimmten Ausdruck statt nach einzelnen Schlüsselwörter gesucht.
Übereinstimmende Dokumente sollten in der Regel den exakten Ausdruck "azure sql", einschließlich der Varianten bezüglich Groß-/Kleinschreibung enthalten, z.B. "Azure SQL" und sollten auch in der Regel das Wort „deployment“ (Bereitstellung) enthalten.

## <a name="filtering-on-fields"></a>Filtern nach Feldern

Sie können nach einer bestimmten Element-ID (oder „Id“ oder „id“) suchen oder nach bestimmten anderen Feldern, indem Sie den Suchbegriffen den Feldnamen voranstellen.

Aktuell lauten die durchsuchbaren Felder „Id“, „Version“, „Tags“, „Author“ (Autor), „Owner“,(Besitzer) „Functions“ (Funktionen), „Cmdlets“, „DscResources“ und „PowerShellVersion“.

[Was ist der Unterschied zwischen ID und Titel? Die ID ist der Name, den Sie in der Konsole verwenden. Der Titel ist das, was am oberen Rand der Elementseite in den Suchergebnissen angezeigt wird.]

## <a name="examples"></a>Beispiele

    ID:"PSReadline"
    id:"AzureRM.Profile"

findet Elemente mit „PSReadline“ oder „AzureRM.Profile“ jeweils in deren ID-Feld.

    Id:"AzureRM.Profile"

ist eine andere Möglichkeit, Elemente mit „AzureRM.Profile“ in ihrem ID-Feld zu suchen.

Der Filter „Id“ ist eine Übereinstimmung bei Teilzeichenfolge, Sie suchen also nach Folgendem:

    Id:"azure"

Daraufhin erhalten Sie die Ergebnisse, wie z.B. „AzureRM.Profile“ und „Azure.Storage“.

Sie können auch nach mehreren Schlüsselwörtern in einem einzelnen Feld suchen. Oder kombinieren Sie Felder.

    id:azure tags:intellisense
    id:azure id:storage

Sie können auch nach Ausdrücken suchen:

    id:"azure.storage"


So suchen Sie alle Elemente mit DSC-Tag.

    Tags:"DSC"

So suchen Sie alle Elemente mit der angegebenen Funktion.

    Functions:"Update-AzureRM"

So suchen Sie alle Elemente mit dem angegebenen Cmdlet.

    Cmdlets:"Get-AzureRmEnvironment"

So suchen Sie alle Elemente mit dem angegebenen DSC-Ressourcennamen.

    DscResources:"xArchive"

So suchen Sie alle Elemente mit der angegebenen PowerShellVersion.

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Wenn Sie anschließend ein Feld verwenden, das nicht unterstützt wird, wie z.B. „commands“ (Befehle), wird es einfach ignoriert, und alle Felder werden durchsucht. Das folgende Query

    commands:blobs storage

wird genau wie diese Abfrage interpretiert:

    blobs storage