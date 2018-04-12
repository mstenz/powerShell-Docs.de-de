---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andere nützliche Skriptobjekte
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="other-useful-scripting-objects"></a>Andere nützliche Skriptobjekte

Die folgenden Objekte bieten zusätzliche Skriptfunktionalität in Windows PowerShell ISE. Sie sind nicht Teil der **$psISE**-Hierarchie.

## <a name="useful-scripting-objects"></a>Nützliche Skriptobjekte

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Es gibt einige Einschränkungen für die Interaktion von Windows PowerShell ISE mit Konsolenanwendungen. Ein Befehl oder ein Automatisierungsskript, das einen Benutzereingriff erfordert, funktioniert möglicherweise anders, als wenn es von der Windows PowerShell-Konsole aus ausgeführt wird. Möglicherweise wollen Sie die Ausführung dieser Skripts oder Befehle im Befehlsbereich von Windows PowerShell ISE sperren. Das Objekt **$psUnsupportedConsoleApplications** hält eine Liste solcher Befehle vor. Falls Sie versuchen, die Befehle in dieser Liste auszuführen, erhalten Sie die Meldung, dass sie nicht unterstützt werden. Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen Hilfethemen und den entsprechenden Links in der lokalen kompilierten HTML-Hilfedatei verwaltet. Es wird bei der Suche der lokalen Hilfe für ein bestimmtes Thema verwendet. Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen. Das folgende Codebeispiel zeigt einige Beispiele für Schlüssel-Wert-Paare, die in **$psLocalHelp**enthalten sind.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a>Beispielausgabe

|||
|-|-|
|Key : Add-Computer|Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Key : Add-Content|Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen den Titeln der Hilfethemen und den entsprechenden externen URLs verwaltet. Es wird verwendet, um die Hilfe für ein bestimmtes Thema im Web zu finden. Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen.

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a>Beispielausgabe

|||
|-|-|
|Key : Add-Computer|Value : http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Key : Add-Content|Value : http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Weitere Informationen

- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)