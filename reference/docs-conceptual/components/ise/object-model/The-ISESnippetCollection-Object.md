---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Das ISESnippetCollection-Objekt
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736044"
---
# <a name="the-isesnippetcollection-object"></a>Das ISESnippetCollection-Objekt

Das **ISESnippetCollection**-Objekt ist eine Sammlung von **ISESnippet**-Objekten. Die einem **PowerShellTab**-Objekt zugeordnete Dateisammlung ist ein Member dieser Klasse. Ein Beispiel ist die `$psISE.CurrentPowerShellTab.Files`-Auflistung.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load\( FilePathName \)

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Lädt eine `.snippets.ps1xml`-Datei mit benutzerdefinierten Codeausschnitten. Die einfachste Möglichkeit zum Erstellen von Codeausschnitten ist das `New-IseSnippet`-Cmdlet, das die Ausschnitte automatisch im Profilordner speichert, sodass sie bei jedem Start der Windows PowerShell ISE geladen werden.

**FilePathName** – Zeichenfolge – der Pfad und der Dateiname für eine Datei mit der Erweiterung „.snippets.ps1xml“, die Codeausschnittdefinitionen enthält.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISESnippet-Objekt](The-ISESnippetObject.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
