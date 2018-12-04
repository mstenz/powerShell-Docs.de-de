---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Syntax für die Katalogsuche
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742855"
---
# <a name="gallery-search-syntax"></a>Syntax für die Katalogsuche

Sie können suchen, die PowerShell-Katalog mit der [PowerShell-Katalog-Website](https://www.powershellgallery.com/).
PowerShell-Katalog-Website bietet ein Textsuchfeld, wo Sie Wörter, Ausdrücke und verwenden können, um die Suchergebnisse einzugrenzen.

## <a name="search-by-keywords"></a>Suche nach Schlüsselwörtern

    dsc azure sql

Suchen Sie versucht, suchen Sie die relevanten Dokumente, die alle 3-Schlüsselwörter enthält, und zugehörige Dokumente zurückzugeben.

## <a name="search-using-phrases-and-keywords"></a>Suchen mithilfe von Ausdrücken und Schlüsselwörtern

    "azure sql" deployment

Die Eingabe eines Ausdrucks zwischen Anführungszeichen ("") ändert den Suchvorgang. Es wird nun nach dem bestimmten Ausdruck statt nach einzelnen Schlüsselwörter gesucht.
Übereinstimmende Dokumente sollten in der Regel den exakten Ausdruck "azure sql", einschließlich der Varianten bezüglich Groß-/Kleinschreibung enthalten, z.B. "Azure SQL" und sollten auch in der Regel das Wort „deployment“ (Bereitstellung) enthalten.

## <a name="filtering-on-fields"></a>Filtern nach Feldern

Sie können nach einer bestimmten Paket-ID (bzw. „Id“ oder „id“) oder nach bestimmten anderen Feldern suchen, indem Sie den Suchbegriffen den Feldnamen voranstellen.

Aktuell lauten die durchsuchbaren Felder „Id“, „Version“, „Tags“, „Author“ (Autor), „Owner“,(Besitzer) „Functions“ (Funktionen), „Cmdlets“, „DscResources“ und „PowerShellVersion“.

[Was ist der Unterschied zwischen ID und Titel? Die ID ist der Name, den Sie in der Konsole verwenden. Der Titel ist das, was oben auf der Paketseite in den Suchergebnissen angezeigt wird.]

## <a name="examples"></a>Beispiele

    ID:PSReadline
    
Sucht Pakete mit einer ID, die mit "PSReadline".

    Id:"AzureRM.Profile"

Dies ist eine andere Möglichkeit, Pakete mit „AzureRM.Profile“ im ID-Feld zu suchen.

Der Filter „Id“ ist eine Übereinstimmung bei Teilzeichenfolge, Sie suchen also nach Folgendem:

    Id:"azure"

Dieser enthält Ergebnisse, die von "azurerm.Profile" enthalten "und"Azure.Storage".

Sie können auch nach mehreren Schlüsselwörtern in einem einzelnen Feld suchen. 

    id:azure tags:intellisense

Und Sie die Suche nach Ausdrücken mit doppelten Anführungszeichen ausführen können:

    id:"azure.storage"

So suchen Sie alle Pakete mit DSC-Tag:

    Tags:DSC

So suchen Sie alle Pakete mit der angegebenen Funktion:

    Functions:Get-TreeSize

So suchen Sie alle Pakete mit dem angegebenen Cmdlet:

    Cmdlets:Get-AzureRmEnvironment

So suchen Sie alle Pakete mit dem angegebenen DSC-Ressourcennamen:

    DscResources:xArchive

So suchen Sie alle Pakete mit der angegebenen PowerShellVersion:

    PowerShellVersion:2.0

Wenn Sie anschließend ein Feld verwenden, das nicht unterstützt wird, wie z.B. „commands“ (Befehle), wird es einfach ignoriert, und alle Felder werden durchsucht. Das folgende Query

    commands:blobs storage

wird genau wie diese Abfrage interpretiert:

    blobs storage
