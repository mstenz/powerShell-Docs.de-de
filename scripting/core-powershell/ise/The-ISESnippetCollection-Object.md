---
title: Das ISESnippetCollection-Objekt
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 410cd4503883ea2cc02936044d7357b9cb029274

---

# Das ISESnippetCollection-Objekt
  Das **ISESnippetCollection**-Objekt ist eine Sammlung von **ISESnippet**-Objekten. Die einem **PowerShellTab**-Objekt zugeordnete Dateisammlung ist ein Member dieser Klasse. Ein Beispiel ist die **$psISE.CurrentPowerShellTab.Files**-Sammlung.

## Methoden

### Load\( FilePathName \)
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Lädt eine .snippets.ps1xml-Datei mit benutzerdefinierten Codeausschnitten. Die einfachste Möglichkeit zum Erstellen von Codeausschnitten ist das New-IseSnippet-Cmdlet, das sie automatisch im Profilordner speichert, sodass sie bei jedem Start von Windows PowerShell ISE geladen werden.

 **FilePathName** – Zeichenfolge – der Pfad und der Dateiname für eine Datei mit der Erweiterung „.snippets.ps1xml“, die Codeausschnittdefinitionen enthält.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## Weitere Informationen
- [Das ISESnippet-Objekt](The-ISESnippetObject.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Oct16_HO3-->


