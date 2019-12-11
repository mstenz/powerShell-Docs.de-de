---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISESnippetCollection-Objekt
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030500"
---
# <a name="the-isesnippetcollection-object"></a>Das ISESnippetCollection-Objekt

Das **ISESnippetCollection**-Objekt ist eine Sammlung von **ISESnippet**-Objekten. Die einem **PowerShellTab**-Objekt zugeordnete Dateisammlung ist ein Member dieser Klasse. Ein Beispiel ist die **$psISE.CurrentPowerShellTab.Files**-Sammlung.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load\( FilePathName \)

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Lädt eine .snippets.ps1xml-Datei mit benutzerdefinierten Codeausschnitten. Die einfachste Möglichkeit zum Erstellen von Codeausschnitten ist das New-IseSnippet-Cmdlet, das sie automatisch im Profilordner speichert, sodass sie bei jedem Start von Windows PowerShell ISE geladen werden.

**FilePathName** – Zeichenfolge – der Pfad und der Dateiname für eine Datei mit der Erweiterung „.snippets.ps1xml“, die Codeausschnittdefinitionen enthält.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISESnippet-Objekt](The-ISESnippetObject.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
