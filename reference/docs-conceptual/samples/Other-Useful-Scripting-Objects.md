---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andere nützliche Skriptobjekte
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325159"
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

Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen Hilfethemen und den entsprechenden Links in der lokalen kompilierten HTML-Hilfedatei verwaltet. Es wird bei der Suche der lokalen Hilfe für ein bestimmtes Thema verwendet. Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen. Das folgende Codebeispiel zeigt einige Beispiele für Schlüssel-Wert-Paare, die in `$psLocalHelp` enthalten sind.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Dabei handelt es sich um ein Wörterbuchobjekt, das eine kontextbezogene Zuordnung zwischen den Titeln der Hilfethemen und den entsprechenden externen URLs verwaltet. Es wird verwendet, um die Hilfe für ein bestimmtes Thema im Web zu finden. Sie können Themen zu dieser Liste hinzufügen oder aus dieser Liste löschen.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

Das nachfolgende Skript fügt der Liste einen Eintrag hinzu.

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Weitere Informationen

[Zweck des Windows PowerShell ISE-Skriptobjektmodells](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
